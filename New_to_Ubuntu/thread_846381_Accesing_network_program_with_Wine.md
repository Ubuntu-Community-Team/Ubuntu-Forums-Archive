---
title: "Accesing network program with Wine"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by thomsany on 2008-07-01
Hi!!
I am trying to access a program on my company's network but I am running into some difficulties.
If I go into the network share and locate the EXE file to open the program, it opens normally, no hassles.
However, if I want to create a launcher on the desktop that would go for example:
/media/share/yedidwin/Menu.exe
The program opens but sends me an error on files its trying to locate on my local drive. However if I open it up opening the folders and locating the file it opens just fine.
I haven't figured out a way to place an icon on the desktop. Any suggestions?

Regards,
Teo

---

### Post by nowshining on 2008-07-01
add wine in front of the command.

I suggest removing the ver. in synaptic and installing the one from winehq.com - latest stable is 1.0 - if you must and u use anything below hardy - go into the older debs and to ur ver. of ubuntu, etc.. and find the deb version for your system, and then the one with i386 - 32bit computers and x86_64 and AMD64 for 64bit computers.

---

