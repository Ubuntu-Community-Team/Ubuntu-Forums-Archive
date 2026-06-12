---
title: "[SOLVED] simple way to speed up applications and use your ram effeciently"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by stinger30au on 2008-08-20
i have just stumbled across this

[http://www.techthrob.com/tech/preload.php](http://www.techthrob.com/tech/preload.php)

Introduction
 Preload is an "adaptive readahead daemon" that runs in the background of your system, and observes what programs you use most often, caching them in order to speed up application load time. By using Preload, you can put unused RAM to good work, and improve the overall performance of your desktop system. 


Installation
 Installing Preload on Ubuntu is easily done with the command:

sudo apt-get install preload


Preload is in the package repositories of many different managers, so users of other distributions should check their appropriate package managers to see if it's available. If not, you can always install Preload via [its page on SourceForge.net]("http://preload.sourceforge.net/") 

Once installed, Preload will start, and no further action is necessary, but read on for configuration options, to learn how to monitor Preload's activities, and see what kind of improvements Preload will bring to your system.

---

### Post by Gregmond on 2008-08-20
you can also edit the grub menu on startup and add the profile command (only do it once) to get it to profile what you load up.

---

### Post by praveenpious on 2008-08-20
Thanks for the info :)

---

### Post by sdennie on 2008-08-20
Preload is very useful if you have a lot of extra RAM.  You can also see this thread for ideas on how to force things into cache: [http://ubuntuforums.org/showthread.php?t=565651](http://ubuntuforums.org/showthread.php?t=565651)

---

### Post by pi.boy.travis on 2008-08-20
This is awesome!  Sort of like Windows' superfetch. . .

---

