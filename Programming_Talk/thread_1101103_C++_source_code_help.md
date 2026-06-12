---
title: "C++ source code help"
date: 2009-03-19
forum: Programming Talk
---

### Post by huwaw69 on 2009-03-19
i have a simple project of mine that is like inventory program...
for example i have 3 products, i have an apple, an orange, and a manggo...
the 3 products quantity is 10 per product, so:
apple x10
orange x10
manggo x10

The program must be able to show the user how much each product costs, how many product is left, and how much sales did the user gained...
so for the output:
---------------------------------------------------------------
                      "Inventory Program"
::Options::
1. Check Product Quantity
2. Item Being Purchased
3. Product Left
4. Product individual price
3. Exit
-------------------------------------------------------------------------------

If the user choice is option 1, the program must ask the product name and display how many product is left. For output Example:

--------------------------------------------------------------------------------
1. Check Product Quantity
product name:?
apple <<---- The user typed apple
there are still 10 apples left. <<The Program Replies With this
--------------------------------------------------------------------------------

if the user's choice is option 2. The Program will ask for the product name, then how much will be deducted to the quantity and then shows the item name and how much is the cost...
for output example:
---------------------------------------------------------------------------------
2. Item Being purchased
product name:?
apple <<-- user buys an apple
how many?
5 <<-- User Buys 5 apples
apple $1 ea. <<___ The Program replies with the product name and
5piece = $5 <<       how much the product costs
-------------------------------------------------------------------------------

and for the 3rd option the program will ask the product name and then replies how many is left/ how much product is still left...
for output example..

---------------------------------------------------------------------------------
3. Product left
enter product name:
apple <<-- user asks how many apples left
apple has 5 more left the program replies for this
--------------------------------------------------------------------------------
and for the 4th option  the program must reply with the procuct name and how much it costs per piece. For output example..
---------------------------------------------------------------------------------
4.Product individual price
Enter Products Name:?
apple <<-- The user wants to know how much apple is per piece
apple = $1 per piece <<-- the program replies the name and costs
---------------------------------------------------------------------------------
This is for my mom she is running a pharmacy and having a hard time monitoring her products... so i wanna know if c++ is able to do this?
then will you help im still a noob in c++ or should i say a beginner..

Please dont post the exact code... im not that lazy please just post a guide on how will i do it or what should i use and how will i design the functions or classess...
please use header <iostream> its my prefered header... its the first one i learned, i forgot how to use <stdio.h>...
Please Help me..

---

### Post by antony_css on 2009-03-19
[Stack overflow]("http://stackoverflow.com/") is a good site for problems about programming.

Also google "C++ reference" to learn the syntax of C++.

---

### Post by kavon89 on 2009-03-20
If this is for a real application and not just homework something, you'll need to save everything to a file and you'll want a good design to keep things in order.

I would go with an object oriented approach with multiple inheritances, such as an Item class which contains the basic requirements of anything sold in your mother's pharmacy, like a price, upc number, department number perhaps.

---

### Post by huwaw69 on 2009-03-20
I just need the names of the medicines right? this was just a sample program... i just want to know the method or easiest method to do it? but i like the idea of that object oriented thing

---

