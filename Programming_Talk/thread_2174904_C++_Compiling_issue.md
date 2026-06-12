---
title: "C++ Compiling issue"
date: 2013-09-16
forum: Programming Talk
---

### Post by Ultimatefry on 2013-09-16
OK, so I got bored on Sunday after morning service was over, so I returned to messing around with C++ with the little knowledge I have and started making a text-based adventure game (the last two words being used lightly), and followed a guide I found online[SUP]1[/SUP] to install the compiler. When I got to the third line in the compiling guide, it gave me an error saying that the file could not be found. Trying to start the needed program outside of Notepad++ resulted in this:

[IMG]http://i44.tinypic.com/2ntvb10.jpg[/IMG]

What do?

---

### Post by monkeybrain20122 on 2013-09-16
This is WIndows??

---

### Post by Ultimatefry on 2013-09-16
Yeah, this is the faster computer.

---

### Post by oldos2er on 2013-09-17
Moved to Programming Talk.

---

### Post by r-senior on 2013-09-17
You need the right compiler binary for your version of Windows. The error message is not helping much but your first step should be to work out whether you are running 32-bit or 64-bit:

[http://pcsupport.about.com/od/windowsvista/ht/windows-vista-32-bit-64-bit.htm](http://pcsupport.about.com/od/windowsvista/ht/windows-vista-32-bit-64-bit.htm)

I'm assuming Vista. It stirs my hazy memory of what Vista looked like before I uninstalled it.

---

### Post by dwhitney67 on 2013-09-17
> **r-senior said:**
> You need the right compiler binary for your version of Windows. The error message is not helping much but your first step should be to work out whether you are running 32-bit or 64-bit:


On Windows, one can use Visual Studio YYYY Express Edition (where YYYY is some release year), which is basically the free edition.  It only compiles 32-bit libraries and apps, but these are usable on a 64-bit system.

To compile 64-bit libraries and apps, one must upgrade to Visual Studio YYYY Standard or Professional Edition.  This costs a good load of money, and it baffles me why anyone in their right mind would ever go this route.

Just use Linux, and the tools are free... thanks to some generous people out there in the World.

As for the OP, it seems he is using MinGW, Notepad++, and god knows what else.

---

### Post by Ultimatefry on 2013-09-18
> **r-senior said:**
> You need the right compiler binary for your version of Windows. The error message is not helping much but your first step should be to work out whether you are running 32-bit or 64-bit:

[http://pcsupport.about.com/od/windowsvista/ht/windows-vista-32-bit-64-bit.htm](http://pcsupport.about.com/od/windowsvista/ht/windows-vista-32-bit-64-bit.htm)

I'm assuming Vista. It stirs my hazy memory of what Vista looked like before I uninstalled it.

Windows 7 Ultimate
Service Pack 1
32-bit Operating System

---

