Отчёт представляет информацию о программе, моделирующую ПИД-регулятор. В качестве объекта управления использована математическая модель, а также классы линейной и нелинейной модели.
Классы:
Класс Math
Абстрактный базовый класс для математических моделей. Он содержит виртуальную функцию Calc, которая должна быть реализована в производных классах. Эта функция принимает текущий выход, предыдущий выход и входной сигнал и возвращает вычисленный выход модели.
Класс LinModel - класс, наследующийся от Math, представляет линейную модель. Он имеет два коэффициента A и B, которые используются для вычисления выходного значения по формуле A * curout + B * input.
Класс NonlinModel представляет нелинейную математическую модель. Данный класс наследуется от абстрактного класса MathModel и реализует его виртуальную функцию calcOutput. Имеет четыре приватных переменных - A, B, C и D, которые используются в формуле для вычисления выходного значения модели. Конструктор класса принимает значения коэффициентов A, B, C и D и инициализирует соответствующие приватные переменные.
Функция calcout переопределена в классе NonlinModel и использует формулу A * curout - B * pow(prevout, 2) + C * input + D * sin(input) для вычисления выходного значения модели на основе текущего выхода, предыдущего выхода и входного значения.
Класс PID - класс, реализующий регулятор PID. Он имеет три коэффициента P, I и D, которые соответствуют пропорциональной, интегральной и дифференциальной составляющим регулятора соответственно. Функция calcOutput принимает текущую ошибку и вычисляет управляющий сигнал на основе коэффициентов и аккумулированных ошибок.