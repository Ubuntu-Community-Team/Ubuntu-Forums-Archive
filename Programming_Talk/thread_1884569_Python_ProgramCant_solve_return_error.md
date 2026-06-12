---
title: "Python Program:Cant solve return error"
date: 2011-11-21
forum: Programming Talk
---

### Post by TheMattyC on 2011-11-21
Im writing a modular Python program that will calculate the cost of purchasing a meal.  This program will include decisions and loops.  Details of the program are as follows:
•	Your menu items only include the following food with accompanied price: 
o	Yum Yum Burger = $0.99
o	Grease Yum Fries = $0.79
o	Soda Yum = $1.09

•	Allow the user of the program to purchase any quantity 0 through 20, of these items on one order. So maximum of 20 for each of the burger, fries and soda can be ordered in one order. The user may choose not to order an item at all.
•	Allow the user of the program to purchase one or more types of these items on one order. That is, the user can order any item more than once in the same order
•	After the order is placed, calculate the sub-totals and the total. Add a 13% sales tax to total to produce the final purchasing price. 
•	Print to the screen a receipt showing the total number of each item purchased, the sub-total amount of each item purchased (number purchased by price), the total amount, the tax on the total amount and then and the final purchase price. 

I have a pretty solid grasp on what i should be doing but for some reason i cannot get my code to work at all. I have attached my python code if someone could please look at it, when ever i try to run the program i instantly get a syntax error on my first function on the return command. I can not figure out what is causing this to happen.

---

### Post by MadCow108 on 2011-11-21
indentation is important in python

the returns must be in the same indentation level as the functions and you can't return from global scope (lowest indentation level)

also the last function is missing a colon at the end and an empty body is noted as pass in python
```
def calculate_burger_cost(num_of_burgers):
  pass
```

---

### Post by TheMattyC on 2011-11-21
i have the functions working properly now, im just trying to figure out how to pull it all together in the main. I believe that my get_item functions may not be correct as well either though 

here is my updated program so far

---

### Post by MadCow108 on 2011-11-21
each function name must be unique within its scope in python, you have three get_item functions, it can only be one. more technically, you can't overload/override functions in python.
you have a bunch of common functionality duplicated throught your code.
you should reduce the duplication, e.g. the string and the prices could be looked up from a dictionary in a single function.

e.g.
```
get_item("burger", waiter_responses)
get_cost(45, "soda", price_table)
```

see the python documentation on what a dictionary is.

---

