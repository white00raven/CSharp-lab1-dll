# Смешанное программирование на С++ и С#

**Цель работы:** научиться создавать библиотеки динамической компоновки на С++ и подключать их к проектам на C#.\

## Создание библиотеки динамической компоновки

В пакете Visual Studio создадим новое решение `Lab1` и включим в него проект `TestDll`. Тип: консольное приложение (VS <2017) или пустой проект (VS 2017), потом выставляется опция `Dll`.

В проект помещаются файлы:

**TestDll.h**

```cpp
#pragma once

extern "C" {
   _declspec(dllexport) double Add(double x, double y);
}
```

**TestDll.cpp**

```cpp
#include "TestDll.h"

extern "C" {
   _declspec(dllexport) double Add(double x, double y)
   {
      return x+y;
   }
}
```

Проект необходимо построить и в результате сборке должен появиться файл динамической компоновки `TestDll.dll`

## Создание консольного приложения на C#

В то же решение `Lab1` нужно добавить новый проект **Консольное приложение на C#** под именем `CheckDll`

**Program.cs**

```csharp
using System;
using System.Collections;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Runtime.InteropServices;

namespace CheckDll
{
   class Program
   {
      [DllImport(@"путь\TestDll.dll",CallingConvention = CallingConvention.Cdecl)]
      static extern double Add(double x,double y);
      static void Main(string[] args)
      {
         Console.WriteLine(Add(3,2));
      }
    }
}
```

Теперь необходимо построить приложение и запустить его. В случае успеха, на экране должна появиться 5, иначе появятся сообщения об ошибках.

## Работа с массивами

В том же проекте добавить функцию, заполняющую массив целых чисел случайными значениями в диапазоне от 0 до 100. Функцию поместить в Dll, а результат вывести в консольном приложении C#

## Простые числа

Написать динамическую библиотеку для работы с простыми числами. Реализовать в библиотеке следующие функции:

- **int isPrime(unsigned long number)** - проверка числа на простоту
- **unsigned long nextPrime(unsigned long number)** - нахождение ближайшего простого, большего number
- **unsigned long nPrime(int n)** - вычисление n-ого простого числа (в ряду простых чисел)

Написать демонстрационное приложение на C#, использующую функции из динамической библиотеки

## Графический интерфейс

Создать оконное приложение C# для демонстрации работы с простыми числами из Dll. Для создания приложения необходимо добавить к имеющемуся решению проект типа **Windows Forms Application**, затем перейти к описанию класса формы **Form1.cs** и добавить в класс строки, необходимые для загрузки Dll (см. консольный проект).

Добавить на форму несколько элементов управления (поля ввода, надписи, кнопки) и проверить работу функций, находящихся в Dll (тест на простоту, вычисление ряда простых чисел, нахождение ближайшего простого для введенного пользователем числа).

Добавить на форму элемент **Chart** (диаграмма) и с помощью него построить график ПИ-функции от целого числа x. ПИ(x) - возвращает количество простых чисел в диапазоне от 2 до x включительно. График построить для интервала от 2 до 100.

## Результаты работы

Результаты работы в виде исходных файлов .h, .cpp, .cs прислать в пул-запросе, для своей ветки. 

## Алгоритм выполнения работы

Для выполнения работы необходимо:

1. Выполнить *fork* репозитария в свой аккаунт.
1. Выполнить клонирование репозитария из своего аккаунта к себе на локальную машину (`git clone`).
1. Создать ветку **git** с индивидуальным номером (`git branch имя_ветки`).
1. Сделать ветку активной (`git checkout имя`).
1. Необходимо разместить исходные файлы с решениями задач, поместив **.h, .cpp, .cs**. 
1. Добавить файлы в хранилище (`git add`).
1. Выполнить фиксацию изменений (`git commit -m "комментарий"`).
1. Отправить содержимое ветки в свой удаленный репозитарий (`git push origin имя_ветки`).
1. Создать пул-запрос в репозитарий группы и ждать результата 


|  ФИО              | Имя ветки |
|-------------------|-----------|
| Афанасьев А.     | b1 |
| Воронов Д.    | b2 |
| Баландин А.    | b3 |
| Бритова Ю.|  b4 |
| Голованов Д.         | b5  |
| Головин Д.        | b6 |
| Гордеев В.       | b7 |
| Дукова Е.     | b8 |
| Комаров Д.       | b9 |
| Кузьминский И.     | b10 |
| Кузьмин А.          | b11 |
| Кулаков Р.  | b12  |
| Майоров Н.     | b13 |
| Матвеев С.        | b14 |
| Мизгирев А.            | b15 |
| Мишанина П. | b16 |
| Новикова В.     | b17 |
| Орлов А.      | b18 |
| Слащева Я. | b19 |
| Сорокин А. | b20 |




