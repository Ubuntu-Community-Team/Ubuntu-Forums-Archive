---
title: "can't compile amsn from source"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by Linux_noob616 on 2008-09-14
i got the latest amsn from their site since it's not in the ubuntu reposotories yet. But i can't compile it, i have the build essentials but when i do ./configure i get this
```
checking for prefix by checking for wish... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking tcl build dir... using tcl library in /usr/lib/tcl8.5
checking tk build dir... configure: error: Unable to find Tk directory or Tk package is not tk-dev

```

So i tried getting the tcl8.5 dev like it said by using
```
 sudo apt-get install tcl8.5-dev
```
says it installed, But i still get the error above..:confused:

---

### Post by Mornedhel on 2008-09-14
Read again. It's asking for tk-dev.

Also, are you sure the Ubuntu reps are outdated re aMSN ? I just checked and the site says aMSN is currently at 0.97.2. The reps are at 0.97, Ubuntu variant. I wouldn't consider that *outdated*.

---

### Post by Linux_noob616 on 2008-09-14
the one they have in there hangs for me after one use for some reason. Figured that they might have fixed that in the lastest version.

Just got the tk-dev and about to finish compiling, thanks

EDIT: well i'm getting more errors... I'm just gonna try the one from the repos again. maybe it'll work right this time..

---

### Post by Mornedhel on 2008-09-14
Also, have you checked other IM programs ? Gnome has Pidgin installed by default (multi-protocol IM client, including MSN), KDE uses Kopete (same deal). Or are you set on aMSN for the audio/video support ?

---

