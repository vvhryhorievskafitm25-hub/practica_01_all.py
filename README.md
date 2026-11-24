import math


# ============================================================
# ПРАКТИЧНА РОБОТА №1
# Розробка програмних модулів з використанням базових
# операторів, умовних конструкцій та циклів
# ============================================================


# -------------------- ЗАВДАННЯ 1.1 --------------------------

def task_1_1():
    print("\nЗАВДАННЯ 1.1. Базові оператори та математичні обчислення")

    try:
        a = float(input("Введіть число a: "))
        b = float(input("Введіть число b: "))
        c = float(input("Введіть число c: "))

        print("\nРезультати обчислень:")
        print(f"Сума квадратів: {a**2 + b**2 + c**2:.2f}")
        print(f"Середнє арифметичне: {(a + b + c) / 3:.2f}")

        # Обчислення дискримінанта
        D = b**2 - 4 * a * c
        print(f"Дискримінант: {D:.2f}")

        # Обчислення гіпотенузи
        if a > 0 and b > 0:
            hypotenuse = math.sqrt(a**2 + b**2)
            print(f"Гіпотенуза: {hypotenuse:.2f}")
        else:
            print("Гіпотенузу не можна обчислити: катети мають бути додатними.")

        # Перевірка нерівності трикутника
        is_triangle = (
            a > 0 and b > 0 and c > 0
            and not (a + b <= c or a + c <= b or b + c <= a)
        )

        if is_triangle:
            print("З цих сторін можна утворити трикутник.")
        else:
            print("З цих сторін не можна утворити трикутник.")

        # Демонстрація арифметичних операторів
        print("\nДемонстрація операторів:")
        print(f"a + b = {a + b}")
        print(f"a - b = {a - b}")
        print(f"a * b = {a * b}")

        if b != 0:
            print(f"a / b = {a / b:.2f}")
            print(f"a // b = {a // b}")
            print(f"a % b = {a % b}")
        else:
            print("Ділення на нуль неможливе.")

        print(f"a ** 2 = {a ** 2}")

    except ValueError:
        print("Помилка! Потрібно вводити числові значення.")


# -------------------- ЗАВДАННЯ 1.2 --------------------------

def task_1_2():
    print("\nЗАВДАННЯ 1.2. Перетворення типів даних")

    raw = input("Введіть будь-яке значення: ")

    print("\nПочаткове значення:", raw)
    print("Тип даних:", type(raw))
    print("Кількість символів:", len(raw))
    print("Чи є значення рядком:", isinstance(raw, str))
    print("Перетворення на bool:", bool(raw))
    print("Перетворення на str:", str(raw))
    print("ID об'єкта:", id(raw))

    # Перетворення на ціле число
    try:
        integer_value = int(raw)
        print("Ціле число:", integer_value)
    except ValueError:
        print("Неможливо перетворити введення на int.")

    # Перетворення на дійсне число
    try:
        float_value = float(raw)
        print("Дійсне число:", float_value)
    except ValueError:
        print("Неможливо перетворити введення на float.")

    # Демонстрація додаткових вбудованих функцій
    print("\nДодаткова інформація:")
    print("Тип після перетворення:", type(str(raw)))
    print("Довжина рядка:", len(str(raw)))
    print("Діапазон range(5):", list(range(5)))

    name = input("\nВведіть ім'я: ")
    age = input("Введіть вік: ")

    try:
        age = int(age)
        print(f"\nІм'я: {name:<15}")
        print(f"Вік: {age:03d}")
        print(f"Вік через форматування: {age:5d}")
    except ValueError:
        print("Вік потрібно вводити цілим числом.")


# -------------------- ЗАВДАННЯ 2.1 --------------------------

def task_2_1():
    print("\nЗАВДАННЯ 2.1. Визначення оцінки")

    try:
        score = int(input("Введіть кількість балів (0–100): "))

        if score < 0 or score > 100:
            print("Помилка! Кількість балів має бути від 0 до 100.")
        elif score >= 90:
            print("Оцінка: A — відмінно.")
        elif score >= 82:
            print("Оцінка: B — дуже добре.")
        elif score >= 74:
            print("Оцінка: C — добре.")
        elif score >= 64:
            print("Оцінка: D — задовільно.")
        elif score >= 60:
            print("Оцінка: E — достатньо.")
        elif score >= 35:
            print("Оцінка: FX — потрібно повторно скласти.")
        else:
            print("Оцінка: F — незадовільно.")

    except ValueError:
        print("Помилка! Введіть ціле число.")


# -------------------- ЗАВДАННЯ 2.2 --------------------------

def task_2_2():
    print("\nЗАВДАННЯ 2.2. Аналіз трикутника")

    try:
        a = float(input("Введіть сторону a: "))
        b = float(input("Введіть сторону b: "))
        c = float(input("Введіть сторону c: "))

        if a <= 0 or b <= 0 or c <= 0:
            print("Сторони трикутника повинні бути додатними.")
        elif a + b <= c or a + c <= b or b + c <= a:
            print("Трикутник із такими сторонами не існує.")
        else:
            print("Трикутник існує.")

            if a == b and b == c:
                print("Тип трикутника: рівносторонній.")
            elif a == b or a == c or b == c:
                print("Тип трикутника: рівнобедрений.")
            else:
                print("Тип трикутника: різносторонній.")

            # Перевірка на прямокутний трикутник
            sides = sorted([a, b, c])

            if abs(sides[0]**2 + sides[1]**2 - sides[2]**2) < 1e-9:
                print("Трикутник є прямокутним.")
            else:
                print("Трикутник не є прямокутним.")

            # Формула Герона
            p = (a + b + c) / 2
            area = math.sqrt(p * (p - a) * (p - b) * (p - c))

            print(f"Півпериметр: {p:.2f}")
            print(f"Площа трикутника: {area:.2f}")

    except ValueError:
        print("Помилка! Введіть числові значення.")


# -------------------- ЗАВДАННЯ 3.1 --------------------------

def task_3_1():
    print("\nЗАВДАННЯ 3.1. Використання циклів")

    try:
        n = int(input("Введіть натуральне число n: "))

        if n < 0:
            print("Число не може бути від'ємним.")
            return

        # Обчислення факторіала
        factorial = 1
        for i in range(1, n + 1):
            factorial *= i

        print(f"\nФакторіал {n}! = {factorial}")

        # Обчислення гармонійної суми
        harmonic_sum = 0

        for i in range(1, n + 1):
            harmonic_sum += 1 / i

        print(f"Гармонійна сума: {harmonic_sum:.4f}")

        # Таблиця множення
        print("\nТаблиця множення:")

        for i in range(1, 11):
            for j in range(1, 11):
                print(f"{i * j:4}", end="")
            print()

        # Демонстрація range(start, stop, step)
        print("\nПослідовність парних чисел:")
        for i in range(0, 21, 2):
            print(i, end=" ")

        print()

    except ValueError:
        print("Помилка! Введіть ціле число.")


# -------------------- ЗАВДАННЯ 3.2 --------------------------

def task_3_2():
    print("\nЗАВДАННЯ 3.2. Інтерактивний калькулятор")

    history = []

    while True:
        print("\nДоступні операції: +, -, *, /, //, %, **")
        print("Для виходу введіть exit.")

        operation = input("Введіть операцію: ")

        if operation.lower() == "exit":
            break

        if operation not in ["+", "-", "*", "/", "//", "%", "**"]:
            print("Невідома операція. Спробуйте ще раз.")
            continue

        try:
            a = float(input("Введіть перше число: "))
            b = float(input("Введіть друге число: "))

            if operation in ["/", "//", "%"] and b == 0:
                print("Помилка! Ділення на нуль неможливе.")
                continue

            if operation == "+":
                result = a + b
            elif operation == "-":
                result = a - b
            elif operation == "*":
                result = a * b
            elif operation == "/":
                result = a / b
            elif operation == "//":
                result = a // b
            elif operation == "%":
                result = a % b
            elif operation == "**":
                result = a ** b

            print(f"Результат: {result}")

            history.append(f"{a} {operation} {b} = {result}")

        except ValueError:
            print("Помилка! Потрібно вводити числа.")
            continue
        except (ZeroDivisionError, OverflowError, ArithmeticError) as error:
            print("Помилка обчислення:", error)
            continue

    print("\nІсторія обчислень:")

    if history:
        for item in history:
            print(item)
    else:
        print("Обчислень не було.")

    print("Роботу калькулятора завершено.")


# -------------------- ГОЛОВНЕ МЕНЮ --------------------------

def main():
    while True:
        print("\n" + "=" * 55)
        print("ПРАКТИЧНА РОБОТА №1")
        print("Оберіть завдання для виконання:")
        print("=" * 55)

        print("1 — Завдання 1.1. Базові оператори")
        print("2 — Завдання 1.2. Перетворення типів")
        print("3 — Завдання 2.1. Визначення оцінки")
        print("4 — Завдання 2.2. Аналіз трикутника")
        print("5 — Завдання 3.1. Цикли")
        print("6 — Завдання 3.2. Калькулятор")
        print("0 — Вихід")

        choice = input("\nВаш вибір: ")

        if choice == "1":
            task_1_1()
        elif choice == "2":
            task_1_2()
        elif choice == "3":
            task_2_1()
        elif choice == "4":
            task_2_2()
        elif choice == "5":
            task_3_1()
        elif choice == "6":
            task_3_2()
        elif choice == "0":
            print("Програму завершено.")
            break
        else:
            print("Неправильний вибір. Спробуйте ще раз.")


# Запуск програми
if __name__ == "__main__":
    main()
