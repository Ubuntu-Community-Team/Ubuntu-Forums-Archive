---
title: "The greatest IDE never known"
date: 2007-01-31
forum: Programming Talk
---

### Post by maxamillion on 2007-01-31
I stumbled upon this IDE while I was reading about Xfce4.4 Stable release because I noticed a very clean, very appealing IDE running in one of the screenshots hosted on the xfce.org site so I felt the need to check it out and I can honestly say that this is my favorite IDE I have touched to date and I felt the need to share it with everyone else....

The IDE is named [Geany]("http://geany.uvena.de/") and is available in the repositories for installation

[Screenshots]("http://geany.uvena.de/Documentation/Screenshots")

Happy hacking.

---

### Post by yabbadabbadont on 2007-01-31
It looks really nice, but it isn't the greatest.  It would have to allow for vim keybindings in the editor before it could be considered the greatest...  :D

OK, OK, just to head off a flame-fest, it should have fully configurable keybindings with presets for the various existing major editors.  (vim, emacs, wordstar, ... ;))

---

### Post by Ghil on 2007-01-31
seems nice, I'll download it and test it out :)

---

### Post by maxamillion on 2007-01-31
Well ... it might not be the greatest, but I had to think of a snazzy title so people would check it out :)

---

### Post by Turner.kj on 2007-01-31
First of all the greatest IDE as not been developed yet.  Second of all, what this better then say, Eclipse.  Third of all, ask 20 programmers what the best IDE is and you will get 20 different answers.  Forth of all, it looks better cool, I think I will try it out.  Thanks for the heads up.  :D

---

### Post by maxamillion on 2007-01-31
> **Turner.kj said:**
> First of all the greatest IDE as not been developed yet.  Second of all, what this better then say, Eclipse.  Third of all, ask 20 programmers what the best IDE is and you will get 20 different answers.  Forth of all, it looks better cool, I think I will try it out.  Thanks for the heads up.  :D

Point well taken :D ... but Eclipse+AMD64 don't seem to get along :(

I was on gvim for the longest time and I am getting lazy so this seemed like a nice alternative until it (if it ever does) fails me and i resort back to old faithful.

---

### Post by phossal on 2007-01-31
> **maxamillion said:**
> ... Eclipse+AMD64 don't seem to get along

Download a 32Bit eclipse and a 32Bit JDK. Install them using the directions in my sig. While the java tutorial has grown into something *else*, I initially wrote it because I installed all possible combinations of Java/eclipse until I found the combo that worked as well on my AMD64 as it did on my Windows boxes.

Mirrorball pointed me to CDT, the C/C++ plugin for eclipse, and I've never been happier. I use eclipse on Ubuntu for everything. 

If you *don't* want eclipse, or are an Ubuntu purist (and only use the package managers), just ignore me. ;)

---

### Post by Ghil on 2007-01-31
I won't. point taken, I'll try Eclipse too :)

---

### Post by yabbadabbadont on 2007-01-31
> **Turner.kj said:**
> Third of all, ask 20 programmers what the best IDE is and you will get 20 different answers.

You'll probably get more than 20 different answers...  :lol:

Edit: I looked through the manual.  It appears that it doesn't provide a debugging interface.  :(  I would consider that a "must" for any IDE.  (greatest or otherwise :D)

---

### Post by raul_ on 2007-02-01
Is this an IDE or a text editor? it seems like a text editor to me :-k

---

### Post by antenna on 2007-02-01
I've been using this for some time, it makes a nice change from vim & is certainly worthy of attention.

---

### Post by reacocard on 2007-02-02
Very nice. I'm fairly new to programming (python) and I was using gedit, but this is much nicer.

@raul_: It seems about halfway between an IDE and a text editor. Contains a number of useful programming features, but doesn't aim to have everything.

---

### Post by maddog39 on 2007-02-02
I have been using Geany for ages, have always loved it. It aims to be a "lightweight" IDE which is why its not wicked bloated and stuff like we normally think of IDEs.

My Personal Geany Screenshot:
[http://www.dximages.uni.cc/files/1/screenshots/linux/geany.png](http://www.dximages.uni.cc/files/1/screenshots/linux/geany.png)

---

### Post by Hendrixski on 2007-02-02
> **maddog39 said:**
> I have been using Geany for ages, have always loved it. It aims to be a "lightweight" IDE which is why its not wicked bloated and stuff like we normally think of IDEs.

My Personal Geany Screenshot:
[http://www.dximages.uni.cc/files/1/screenshots/linux/geany.png](http://www.dximages.uni.cc/files/1/screenshots/linux/geany.png)

Anyone whose computer is not ancient won't notice if the IDE is old.  What they will notice is how much slower their programming is when they don't have a good IDE.

I'll look into geanny

---

### Post by Null Reference Exception on 2007-02-02
> **yabbadabbadont said:**
> It appears that it doesn't provide a debugging interface.  :(  I would consider that a "must" for any IDE.  (greatest or otherwise :D)

I concur ;)

---

### Post by zgornel on 2007-02-03
I gave it a try. It does not include a debugger from what I've seen (actually a front end for the debugger) and it crashed while compiling a simple program. Thumbs down. I'll stick to joe + scripts.

---

### Post by reacocard on 2007-02-03
I've compiled a deb of the latest version for edgy. You can get it from my repo:
```
deb http://download.tuxfamily.org/syzygy42 edgy universe
deb-src http://download.tuxfamily.org/syzygy42 edgy universe
```
GPG Key:
```
wget http://download.tuxfamily.org/syzygy42/8434D43A.gpg -O- | sudo apt-key add -
```

---

### Post by blanky on 2007-02-05
> 
If you don't want eclipse, or are an Ubuntu purist (and only use the package managers), just ignore me.


I installed eclipse-sdk and eclipse-cdt from the repositories on my friend's computer last wednesday.

---

### Post by cybrid on 2007-02-23
Hey, hello, I've began using geany as IDE, and I've been trying to setup it for GTK development with libglademm and gtkmm, the problem is that even putting into the build options -llibglademm-2.4 -lgtkmm-2.4 , when I do #include <libglademm/xml.h> and #include <gtkmm.h> into a file, the compiler says that those files cannot be found; could somebody point out where the problem may be?

---

### Post by geakMonkey on 2007-02-26
...code is text unless you code 1s and 0s. 

This editor looks cool, similar to the ones I am accustomed to using for coding. I will try it out when I get some time. 

On a different note, when I opened the geany pages, my Dappy zapped out and I had to reboot. I was logged onto the default desktop. I relogged onto Fluxbox and the website was fine without causing a crash. 

Where's the bug?

---

### Post by jvc26 on 2007-02-27
Hmm I quite like that to be honest  - might start using it!
Il

---

