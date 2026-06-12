---
title: "[SOLVED] thread follow-up"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by pablolie on 2008-08-23
as the originator of the "how do it get real rrot [intentionally misspelled] privilege thread" i want to apologize to the forum for opening up a can of worms that could lead to compromise Ubuntu's wonderful security approach. 

i accomplished everything i needed to get done with the simple
gksudo nautilus
command, which allowed me to edit the system file i had to edit.

the fact i have not needed to do this in 6 months of using ubuntu attests to the flexibility of the system for almost every task that is required in everyday operation. and i want it to stay that way, and support it. especially after having a direct benchmark against windows vista 64 bit, which is running on a parallel system, which i installed at the same time, and which despite the fact it is supposed to be hyper-stable can not hold a candle to my ubuntu home server as far as stability goes.

again, i appreciate the help, and it was not my intent to start a discussion that may lead anyone to second guess the ubuntu strategy of protecting the root system - i find it a good thing, and i want it to stay that way.

---

### Post by elmoosecapitan on 2008-08-23
If ROOT privileges are needed, simply open a terminal and type ```
sudo command
```.

A ROOT login is possible, but Ubuntu has never publicly disclosed such information; it is what allows Ubuntu to be such a safe OS.

---

### Post by halitech on 2008-08-23
if you need to edit a file, an easy way is to 

```
gksu gedit /path/to/file
```
it will ask for your password and then open in gedit. You can substitute gedit for the editor of your choice. I find it much easier plus I'm not second guessing which file I'm opening.

---

### Post by halitech on 2008-08-23
> **elmoosecapitan said:**
> If ROOT privileges are needed, simply open a terminal and type ```
sudo command
```.

A ROOT login is possible, but Ubuntu has never publicly disclosed such information; it is what allows Ubuntu to be such a safe OS.

if it is a graphic app its better to use gksu then sudo

---

