---
title: "[SOLVED] how can i check which version of Ubuntu I am using?"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by shiningkenmonster on 2008-11-12
i ordered a dell mini 9 with ubuntu 8.04.

in my e-mail invoice, it says I am getting the ubuntu 8.04.1
[B]
is there a way for me to check which version I have?[/B]

---

### Post by Crafty Kisses on 2008-11-12
You can look in this file, paste this command in the terminal:
```
/etc/lsb-release
```
The other option is go to, **System ---> Administration ---> System Monitor**, then click on the System Specs tab I think.

---

### Post by Kevbert on 2008-11-12
Welcome to Ubuntu
Via the boot menu (it should say there).
Via Application-Accessories-terminal with
```
lsb_release -a
```
You'll find the command line interface (terminal) is quite useful.

---

### Post by shiningkenmonster on 2008-11-12
Codename,

bash: /etc/lsb-release: Permission denied

am i suppose to log in as sudo first? how do i do that?

---

### Post by Crafty Kisses on 2008-11-12
Try the following then:
```
sudo /etc/lsb-release
```

---

### Post by shiningkenmonster on 2008-11-12
Kevbert, thanks it says I have ubuntu 8.04.1

---

### Post by Liviu-Theodor on 2008-11-12
You can find out and using a GUI, if you like: look at [FONT="Courier New"]System->Administration->System Monitor[/FONT], at the [FONT="Verdana"]System[/FONT] tab.

---

### Post by shiningkenmonster on 2008-11-12
Codename

that was weird. I type in

sudo /etc/lsb-release

and than it asked for my password, I pressed enter.
than I proceeded to enter my password. It gave me 2 seconds to enter my password. Which I couldn't type as fast.
than it says failed.
after three tries.

it says:
sudo: /etc/lsb-release: command not found

---

### Post by Elfy on 2008-11-12
```
lsb_release -a
```

---

### Post by Crafty Kisses on 2008-11-12
Then it must be the following:
```
lsb_release -a
```
In the older distributions of Ubuntu that was the command to do it.

---

### Post by Mr_JMM on 2008-11-12
> **shiningkenmonster said:**
> ... 
and than it asked for my password, I pressed enter.
than I proceeded to enter my password. It gave me 2 seconds to enter my password. Which I couldn't type as fast.
than it says failed.
...

Don't press enter when it asks for your password. Just enter it (you won't see the cursor) THEN press enter.

---

