---
title: "c++ help"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by Roeyfreak10 on 2008-09-10
so i just started learning c++

and i was on another computer before it was running xp
so i was using dev-c++ to write up all the code and then compile it
and then create an execeutable out of it but now im on my computer at home
running ubuntu 8.04 so i need a program that can do the same. any suggestions?

---

### Post by jemate18 on 2008-09-10
> **Roeyfreak10 said:**
> so i just started learning c++

and i was on another computer before it was running xp
so i was using dev-c++ to write up all the code and then compile it
and then create an execeutable out of it but now im on my computer at home
running ubuntu 8.04 so i need a program that can do the same. any suggestions?

for ubuntu you need this first
```
sudo apt-get install build-essential
```

there you will have gcc and other stuff for compiling programs

---

### Post by jemate18 on 2008-09-10
For your IDE

HUGE
1. Netbeans
2. Eclipse

MID
1. Jedit
2. Scite
3. geany

SMALL
1. gedit (GNOME)
2. kate (KDE)
3. mousepad (XFCE)

CONSOLE
1. pico
2. vi
3. nano

---

### Post by sam_delta on 2008-09-10
there are several IDE (integrated development enviroment), the only one ive used is Anjuta (you can find it in synaptics or add/remove) or install it with the following command
```
 sudo apt-get install anjuta
```

or, you can always just use any text editor to make the code and compile (make executable) with g++ using the following command 
```
g++ -o output file.cpp
``` where file.cpp is your source file and output is where your executable file
as mentioned before, you need build-essential package```
sudo apt-get install build-essential
``` Note: its essential, NOT essentials

sam

---

### Post by jemate18 on 2008-09-10
Have you made your choice on which editor (IDE) you want to use?

---

### Post by motang on 2008-09-10
I would go with Geany, it has a good interface and very good.

---

### Post by jemate18 on 2008-09-10
> **jemate18 said:**
> Have you made your choice on which editor (IDE) you want to use?

if you have chosen geany then open
1. Applications -> Accessories -> Terminal

type
2. ```
sudo apt-get install geany

```

---

