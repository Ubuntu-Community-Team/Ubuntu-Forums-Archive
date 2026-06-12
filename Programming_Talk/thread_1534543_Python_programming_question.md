---
title: "Python programming question"
date: 2010-07-19
forum: Programming Talk
---

### Post by xaegis on 2010-07-19
I am currently programming an RPG in python. I was attempting to use the MVC(Model View Controller) pattern but I'm a bit confused.
Should I use nested lists to represent the user characters and their stats 
(Str_,Dex_,Int_) and flags or should I use a class? What are the pros and cons of using each method and how do they fit into the MVC? Is this good for a client/server game using Django.

Thank you for your help

---

### Post by Can+~ on 2010-07-19
> **xaegis said:**
> Is this good for a client/server game using Django

I would first lower my expectations, if you don't know the basics of python, working with a client/server application, even with django, will be a daunting task.

> **xaegis said:**
> Should I use nested lists to represent the user characters and their stats 
(Str_,Dex_,Int_) and flags or should I use a class? What are the pros and cons of using each method and how do they fit into the MVC?

There's a better question to ask. Are you holding data, or logic? Due to context, I would think that a character is not just a sequential set of attributes, but an object with can perform actions (methods).

A class suits better, it's more logic to instantiate a character, than to replicate a list of attributes. In fact, stats, as I see it, should be a dictionary inside the class, such as

[PHP]self.stats = {"str":0, "agi":0, "int":0, "dex":0, ...}[/PHP]

Then, in an MVC environment, the Model will retain the data of the character (self.stats, plus any other thing, level, etc), the View will be your interface, pygame, whatever. And the controller, will be the game logic, including the character logic (actions), plus, how the actions performed in the interface (view) translate to events on the game (controller).

There are many other ways to "do the cut", as to what object represents which part of MVC, but that's the rough idea.

---

### Post by xaegis on 2010-07-19
You are a GOD! Thank you! Thank YOU!
I will start writing the class now. Thank you for explaining it in a way I could understand!:D

---

