---
title: "[SOLVED] which IDE should i use?"
date: 2008-02-13
forum: Programming Talk
---

### Post by ghettosamson on 2008-02-13
good day everyone. I am running ubunut gutsy 64bit. I am currently programming in c++. I have been using g++ on the command line and compiling that way. however i am looking for an IDE. I ran into a problem yesterday with a program I wrote in emacs and had to revert to visual C++ studio so i could use the interactive debugger and view the code and values to find my error. i just want to know if there is a good ide for ubuntu with a good debugger like that of microsoft visual studio? can anyone recommend me anything? any tips or tricks i dont know about.
cheers

---

### Post by Shin_Gouki2501 on 2008-02-13
Eclipse CDT?

---

### Post by amingv on 2008-02-13
Check the FAQs in the stickies.

---

### Post by LaRoza on 2008-02-13
There is one sticky, and the IDE question is the first link. You can't miss it, it is a different colour...

---

### Post by Kadrus on 2008-02-13
I think Gedit is a great IDE...but there are many alternatives I suggest reading the stickies..

---

### Post by CptPicard on 2008-02-13
You can run the GNU debugger in Emacs as well... google for it :)

---

### Post by Sockerdrickan on 2008-02-13
Gedit maybe isn't an IDE but you can make it act like one and it rocks.

---

### Post by LaRoza on 2008-02-13
> **Tux0r said:**
> Gedit maybe isn't an IDE but you can make it act like one and it rocks.

"IDE" is just an "Intergrated Development Environment", and since one could do everything from Gedit, compiling, running, etc, it can be called an IDE.

---

### Post by naugiedoggie on 2008-02-13
> **ghettosamson said:**
> good day everyone. I am running ubunut gutsy 64bit. I am currently programming in c++. I have been using g++ on the command line and compiling that way. however i am looking for an IDE. I ran into a problem yesterday with a program I wrote in emacs and had to revert to visual C++ studio so i could use the interactive debugger and view the code and values to find my error. i just want to know if there is a good ide for ubuntu with a good debugger like that of microsoft visual studio? can anyone recommend me anything? any tips or tricks i dont know about.
cheers

Hello,

I did quite a bit of C programming in emacs, using gdb as the debugger.  It's been quite a while since I did that, but it worked fine for me.  It's a bit daunting to get used to the debugger, but it repays work.  If you don't like gdb in emacs, you also have the option of ddd, which is a graphical front end to gdb.

This is kind of interesting, though.  [RHIDE]("http://www.rhide.com")  According to the site, there is a debian version available.  I used this years ago, on DOS systems.  It was originally for the DJGPP port of gcc.   It is a decent IDE, though I wouldn't want to write an operating system in it.  ;-)  Debugger included.

Debugging aside, I also strongly recommend getting down with 'make' for build management.  Makes it a lot easier.

Thanks.

mp

---

### Post by johnnyb1726 on 2008-02-13
> **naugiedoggie said:**
> Hello,

I did quite a bit of C programming in emacs, using gdb as the debugger.  It's been quite a while since I did that, but it worked fine for me.  It's a bit daunting to get used to the debugger, but it repays work.  If you don't like gdb in emacs, you also have the option of ddd, which is a graphical front end to gdb.

I have to second the notion of using gdb or ddd as a debugger.  Once you get use to them they work great.  I do a lot of C/C++ programming just using vim, gdb, valgrind, and the command line.  I think sometimes it is more efficient then using an IDE.  However, sometimes I am forced to use an IDE and out of all the IDEs i have used I do like eclipse the best.  With CDT you can do C/C++ programming.

--cheers

---

