---
title: "My first python program"
date: 2008-05-21
forum: Programming Talk
---

### Post by Swatfoot on 2008-05-21
This is my first attempt at python program please don't laugh I've never programmed before note it wont work but I am trying.


#!/usr/bin/python
#Filename:whatsyourname.py

#start with message
print 'Welcome to my short python program'
name = int(raw_input('Whats your name?'))
print 'Welcome ' + name

---

### Post by dmm1285 on 2008-05-21
Python is a dynamic language, you don't need to cast into an int. Also. int is short for "integer". and you want a string in this case.

---

### Post by Can+~ on 2008-05-21
Great you're interested in programming, a tip though:

[PHP]#!/usr/bin/python
#Filename:whatsyourname.py

#start with message
print 'Welcome to my short python program'
name = raw_input('Whats your name?')
print 'Welcome ' + name [/PHP]

The int() converts what you put inside, into a number (integer), in your case, you are asking the name, therefore, you store it as a string (plain text).

---

