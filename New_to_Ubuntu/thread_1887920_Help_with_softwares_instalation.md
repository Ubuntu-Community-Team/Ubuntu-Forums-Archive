---
title: "Help with softwares instalation"
date: 2011-11-28
forum: New to Ubuntu
---

### Post by Jonatan Formentera on 2011-11-28
Hi, this is Jonatan from Formentera Island (Spain). I've a problem. I installed Ubuntu 11.10 a few days ago. I'm trying to install softwares but any time I try it the acces is denied. Wether if I try it from the Ubuntu softwares center or from softtonic or from the program that is searching for complements, I find always the same answer: acces denied, this software could require the installation of not authorised paquets.
Could some from you help me
Thank you very much

---

### Post by cavh on 2011-11-28
What exactly is the package you are trying to install?

---

### Post by Birlamedisoft123 on 2011-11-28
Mention ur OS of the PC.

---

### Post by Jonatan Formentera on 2011-11-28
I'm trying to use a video player. When I try it it answer me that it needs coplements. I let it search them, but when I press the bottom for installation it denies the acces.Anyway I can't install any kind of softwares

---

### Post by enjoijesus94 on 2011-11-28
get the software name and open a terminal

then type 
sudo apt-get install thesoftwarename:D

---

### Post by Jonatan Formentera on 2011-11-28
I don't know what you mean with OS. I have got a Windows 7 starter and I have install in it Ubuntu 11.10 with the help of WUBU

---

### Post by enjoijesus94 on 2011-11-28
why dont you install ubuntu through live CD or USB?

:D

---

### Post by enjoijesus94 on 2011-11-28
I never use Wubi for some reason
It always crashes on me and gives me errors 
Just grab a CD and burn the Ubuntu ISO file And pop it in 
and boot it from the LIVE CD and install from there :popcorn:

---

### Post by Jonatan Formentera on 2011-11-28
Thank you enjoijesus94 but the problem is, I don't know how to open a terminal. Could you tell me how to do it, the steps I have to do ?

---

### Post by Jonatan Formentera on 2011-11-28
I tried it with a cd and with a pen but it was impossible. I tried from the boot system to start teh system with Linux but it didn't work with two computers. That's why I used wubu

---

### Post by enjoijesus94 on 2011-11-28
yes no problem

When you open a terminal 
just got to Applications On the top bar
and go to accessories 
and look for terminal

or Alt+F2:o:D

---

### Post by enjoijesus94 on 2011-11-28
Ok
so what happens when you try to boot from the BootMenu??

how old is the machine your booting it from?:guitar:

---

### Post by Paqman on 2011-11-28
Your problem is that you're missing one or more authentication keys that your system needs to ensure that the packages it installs are from a trustworthy source.

Hit Ctrl-Alt-T to open a terminal then enter:
```
sudo apt-get update
```
and post the output here between some [noparse]```

```[/noparse] tags.

---

### Post by Jonatan Formentera on 2011-11-28
I have two computers. I micro one I bouht a few weeks ago, with Window7 Starter. I tried it with an USB, I tried to start it from the boot with the USB in which I had copied Ubuntu, but It went dirently to windows and answer me: Linux, no kernel found. With another computer, windows 7 premium, that is a year and a half old,it was the same. I Tried it from the boot system and the answer was the same. It even eliminated the possibility of starting with the CD from the boot system for a time

---

### Post by enjoijesus94 on 2011-11-28
try Paqman's method and see if it works for you :popcorn:

---

### Post by Jonatan Formentera on 2011-11-28
I'll try it tomorrow with the help of a frien
Thank youto everrone

---

