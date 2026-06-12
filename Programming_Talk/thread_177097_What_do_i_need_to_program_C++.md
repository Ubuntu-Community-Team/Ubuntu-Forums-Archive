---
title: "What do i need to program C++"
date: 2006-05-15
forum: Programming Talk
---

### Post by micke09 on 2006-05-15
Hi all!

This is my first day with ubuntu and linux. I want to program C++, i have program it in windows but now i want to quit useing windows and begin to use Linux. 
So plzz what do i need to install? and how do i get started? What are the comandos to compile and so on? plzz help me :confused: 

And are there any god C++ "geting started" websides?

/Mikael

---

### Post by Sef on 2006-05-15
Welcome to Ubuntu.

To compile, build-essential needs to be installed.

Open the Terminal (Application > Accessories > Terminal)

sudo apt-get update

sudo apt-get install build-essential

---

### Post by lnostdal on 2006-05-15
[http://www.network-theory.co.uk/docs/gccintro/](http://www.network-theory.co.uk/docs/gccintro/)

---

### Post by micke09 on 2006-05-16
Thanks for that!

Now i only need to install ubuntu again, i did something stupid yesterday, i was trying to change resolution and i follow a tip from the forum, but it was to advanced for me, so i screwed-up some where and now i cant get the graphic interface up =(. so for me with zero linux experience it is easyes to install it all again..... 

But thanks for all the tips i will try them all later to day =)

/Miakel

---

### Post by David Marrs on 2006-05-16
before you try a complete reinstall, try to reconfigure the graphics manager with the command, "sudo dpkg-reconfigure xserver-xorg". Follow the instructions and then type "startx" (or just reboot) to see if it worked. That should get your monitor configured again.

---

