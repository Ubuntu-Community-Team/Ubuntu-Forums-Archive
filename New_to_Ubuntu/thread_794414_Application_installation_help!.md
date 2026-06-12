---
title: "Application installation help!"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by iwannalearn on 2008-05-14
Hi, i just downloaded konverter which is .deb installed using package manager, but where did it go? how do i open and use the application?

In terminal i did 

xxxxx@xxxxx-laptop:~$ whereis konverter
konverter: /usr/bin/konverter

i went the path location found konverter double clicked on it but noting?

Any help please

---

### Post by mkoehler on 2008-05-14
First of all, you should make sure that you can run it as an application.  In order to do this, find it in nautilus, right click on it, click properties, go to "Permissions", then make sure that "Allow executing as program" is checked (as it should be already).  After that, you should be able to double-click on it, or you can just run the command in the terminal (konverter)

---

### Post by shifty_powers on 2008-05-14
just open a terminal and type konverter ;)

---

### Post by iwannalearn on 2008-05-14
> **shifty_powers said:**
> just open a terminal and type konverter ;)

Ok i must be missing something:(

xxxxx@xxxxx-laptop:~$ konverter
konverter: error while loading shared libraries: libxine.so.1: cannot open shared object file: No such file or directory

You need any further info guys?

---

### Post by mkoehler on 2008-05-14
Odd, the debian file should have checked all dependencies before installing.  However, to be on the safe side, go to System > Administration > Synaptic and check that you have and/or install libxine1, libxine1-bin, and libxine1-console

---

### Post by iwannalearn on 2008-05-14
> **mkoehler said:**
> Odd, the debian file should have checked all dependencies before installing.  However, to be on the safe side, go to System > Administration > Synaptic and check that you have and/or install libxine1, libxine1-bin, and libxine1-console

Many thanks mate that did the trick:)

Without you guys i would have given up on ubuntu!

Keep up the good work

---

### Post by mlentink on 2008-05-14
> **iwannalearn said:**
> 
Keep up the good work

No. ***You*** keep up the good work. If you've been helped, so help another, help us all...

---

