---
title: "Syntax error in Python"
date: 2013-01-29
forum: Programming Talk
---

### Post by horizons187 on 2013-01-29
I have this code I'm working on to just do some basic area of shapes calculations with a simple text menu in terminal. I keep getting a syntax error in Line 13 but it is the same as all other definitions I have used and I'm not sure what's going on. Here's the code.

P.S. Still very new to Python and programming in general

[PHP]#! /usr/bin/python
#-*-coding: utf-8 -*-
# calculates a area of shapes
print
def print_options():
    print("Options:")
    print(" Enter c for circle function.")
    print(" Enter r for rectangle function.")
    print(" Enter sq for square function.")
    print(" Enter o to see your options.")
    print(" Enter q to quit."

def hello():
    print('Hello!')

def recarea(width, height):
    return width * height

def sqarea(width, height):
    return width * height

def print_welcome(name):
    print('Welcome,', name)

def crcarea(radius):
    return 3.14 * radius**2

def    positive_input(prompt):
    number = float(input(prompt))
    while number <= 0:
        print('Must be a positive number')
        number = float(input(prompt))
    return number

choice = "o"
name = input('Your Name: ')
hello()
print_welcome(name)
while choice != "q"
    if choice == "r"
        w = positive_input('Width: ')
        h = positive_input('Height: ')

        print('Width =', w, 'Height =', h, 'so Area =', recarea(w, h))
    elif choice == "sq"
        w = positive_input('Width: ')
        h = positive_input('Height: ')

        print('Width =', w, 'Height =', h, 'so Area =', sqarea(w, h))
    elif choice == "c"
        radius =  positive_input('Radius: ')
    
        print('Radius =', radius, 'so Area =', crcarea)
    elif choice == "o" or choice != "q"
        print_options()
        choice = input("Option: ")
print()
[/PHP]

---

### Post by r-senior on 2013-01-29
Isn't there a closing bracket missing? After the word "quit"?

---

### Post by horizons187 on 2013-01-29
I'm so dumb. Thank you.

---

### Post by danniel on 2013-01-31
You should also install and use **pylint** (or **pyflakes**), which will check your code for styling and for possible errors.

---

