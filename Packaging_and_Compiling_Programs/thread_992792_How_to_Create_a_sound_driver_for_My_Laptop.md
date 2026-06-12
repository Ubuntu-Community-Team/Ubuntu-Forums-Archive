---
title: "How to Create a sound driver for My Laptop"
date: 2008-11-25
forum: Packaging and Compiling Programs
---

### Post by Uchiha_madara on 2008-11-25
I tried hard to Configure the Sound Card Driver of My Laptop !!

i need to Open The Driver of My SOund card that works on Windows 
and read it ..

then , i'll try to Create My own for Linux ...

is that Possible or not ??

if the answer is yes ... i need the Software or a method to Create this Package or this Driver!!

if not .... tell me why???

---

### Post by kcode on 2008-11-27
Well definitely yes...you can create a device driver of your own if you cant find any existing driver that drives your device. Drivers are OS specific, therefore you need to write a driver which is Linux specific. Check out this book which is about Linux device drivers([http://lwn.net/Kernel/LDD3/](http://lwn.net/Kernel/LDD3/)). You can look at windows specific driver only if its open sourced.

Cheers

---

### Post by Uchiha_madara on 2008-11-27
> **kcode said:**
> Well definitely yes...you can create a device driver of your own if you cant find any existing driver that drives your device. Drivers are OS specific, therefore you need to write a driver which is Linux specific. Check out this book which is about Linux device drivers([http://lwn.net/Kernel/LDD3/](http://lwn.net/Kernel/LDD3/)). You can look at windows specific driver only if its open sourced.

Cheers

thank you very much...

---

### Post by Uchiha_madara on 2008-11-27
Any new Ideas??

---

