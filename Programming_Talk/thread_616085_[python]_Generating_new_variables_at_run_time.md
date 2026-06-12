---
title: "[python] Generating new variables at run time"
date: 2007-11-17
forum: Programming Talk
---

### Post by ihavenoname on 2007-11-17
I was just wondering if there was a way to have new variables generated at run time. For example, If I am making a program that tallies the cost of someones pizza order, I could have it say
```

price_of_pizza_1 = input("Please type the price of the first pizza: ")
price_of_pizza_2 = input("Please type the price of the second pizza: ")

total = price_of_pizza_1 + price_of_pizza_2
print "Your total is:", total

```

Now that would work fine if I knew how many pizzas were being ordered, but what if some one wants three pizzas? 

Is there a way to have the program generate new variables (eg. price_of_pizza_3,price_of_pizza_4) as they are needed. 

I would like to able to have the program receive inputs from a textbox and generate new pizza variables as the prices are entered and to add the new pizzas to a list. (Using pygtk)

At the same time I would like their to be a command line version of this as well. (By that I mean, if there is a pygtk method and a separate cli method I would like to know both.)

Any ideas?

p.s. The program above is just an example I'm not sure if the code I type would even work in it's current state, I just wrote it to explain what I was trying to do.

---

### Post by LaRoza on 2007-11-17
You can make a list, and append new values as needed.

---

### Post by LaRoza on 2007-11-17
[php]
#! /usr/bin/python

pizza_order = []

pizza_tally = 0
count = True
while count == True:
    pizza = raw_input("What type of pizza do you want?")
    if pizza != "":
        pizza_order.append(pizza)
    else:
        count = False

print "You ordered ", len(pizza_order)
for p in pizza_order:
     print p
[/php]

This doesn't tally the price, but gives shows how to add pizzas to a order, and calculate the total amount, and access each one.

If you want to tally prices, it depends on how the pricing works. If every pizza is the same price, all you need is the length and the ability to multiply. 

I have a feeling what you have in mind doesn't involve pizza's and this was an example.

---

### Post by ihavenoname on 2007-11-17
> **LaRoza said:**
> [php]
#! /usr/bin/python

pizza_order = []

pizza_tally = 0
count = True
while count == True:
    pizza = raw_input("What type of pizza do you want?")
    if pizza != "":
        pizza_order.append(pizza)
    else:
        count = False

print "You ordered ", len(pizza_order)
for p in pizza_order:
     print p
[/php]This doesn't tally the price, but gives shows how to add pizzas to a order, and calculate the total amount, and access each one.

If you want to tally prices, it depends on how the pricing works. If every pizza is the same price, all you need is the length and the ability to multiply. 

I have a feeling what you have in mind doesn't involve pizza's and this was an example.

Ah, thank you. That method looks like it will work, but how would you display the list of pizzas?

How you have the list output in pygtk. I am not very familar with pygtk so I am planing on learning this. 

No, you are correct I am not making a pizza program, I am trying to work on a gui for lvm. I needed a method to display the various physical volumes that a user has created.

---

### Post by LaRoza on 2007-11-17
> **ihavenoname said:**
> Ah, thank you. That method looks like it will work, but how would you display the list of pizzas?

How you have the list output in pygtk. I am not very familar with pygtk so I am planing on learning this. 


This script lists the pizzas at the end.

```

for p in pizza_order:
     print p 

```

With a list (or tuple), you can iterate through it with a for loop. I don't know much about PyGTK, but making a list should be easy.

---

### Post by ihavenoname on 2007-11-17
> **LaRoza said:**
> This script lists the pizzas at the end.

```

for p in pizza_order:
     print p 

```With a list (or tuple), you can iterate through it with a for loop. I don't know much about PyGTK, but making a list should be easy.

Thanks you've been a great help!

---

### Post by LaRoza on 2007-11-17
> **ihavenoname said:**
> Thanks you've been a great help!

No problem.

---

### Post by Quikee on 2007-11-18
You are making a GUI for LVM? Something like [system-config-lvm]("http://ubuntuforums.org/showthread.php?t=216117&highlight=gui+lvm")( which is also made in python)?

---

### Post by Kadrus on 2007-11-18
Euuh..I guess I am too late for this since Laroza already answered the question but anyway you can **create a loop.**. or ask the user at the beginning how many pizzas he wants..use the **if conditions**...
and the ask the questions..

---

### Post by LaRoza on 2007-11-18
> **Kadrus said:**
> Euuh..I guess I am too late for this since Laroza already answered the question but anyway you can **create a loop.**. or ask the user at the beginning how many pizzas he wants..use the **if conditions**...
and the ask the questions..

Trying to increase post count, eh?

---

### Post by ihavenoname on 2007-11-18
> **Quikee said:**
> You are making a GUI for LVM? Something like [system-config-lvm]("http://ubuntuforums.org/showthread.php?t=216117&highlight=gui+lvm")( which is also made in python)?

No, that's for managing LVM, I'm trying to make a gui for partitioning your hard drive using lvm. The idea is to have it be used in the Desktop(Live) cd installer. Since that currently has no LVM support.

---

