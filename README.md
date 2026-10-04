def get_max_dragon_force(n):
    # Валидация входных данных согласно ограничениям задачи (0 < N < 100)
    if n <= 0 or n >= 100:
        raise ValueError("Количество голов должно быть в диапазоне от 1 до 99")
        
    # Базовые случаи
    if n == 1: return 1
    if n == 2: return 2
    if n == 3: return 3
    
    # Логика деления на оптимальные группы (по 3 головы)
    remainder = n % 3
    if remainder == 0:
        return 3 ** (n // 3)
    elif remainder == 1:
        # Если осталась 1 голова, выгоднее взять две двойки: 3 + 1 = 4 = 2 * 2
        return (3 ** (n // 3 - 1)) * 4
    else:
        # Если осталось 2 головы, просто умножаем на 2
        return (3 ** (n // 3)) * 2

# Пример тестирования алгоритма
if __name__ == "__main__":
    try:
        heads = int(input("Введите количество голов драконьей стаи (N): "))
        max_force = get_max_dragon_force(heads)
        print(f"Максимально возможная сила стаи из {heads} голов: {max_force}")
    except ValueError as e:
        print(f"Ошибка ввода: {e}")
