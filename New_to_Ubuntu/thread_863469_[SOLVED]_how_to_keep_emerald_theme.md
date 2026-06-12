---
title: "[SOLVED] how to keep emerald theme???"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-07-18
i can install an emerald theme but when i turn off my computer it goes back to default,is there any way to keep the emerald theme on all the time?
i have to use emerald--replace in the run command to get it to work.
any ideas?????
rick

---

### Post by jerome1232 on 2008-07-18
There's a spot to do this in compiz but i'm in windows and don't remember, so the other way is to go system>>preferences>>session

hit add, and type in emerald --replace

reboot it should work.

---

### Post by LowSky on 2008-07-18
(im also in windows so bear with me)
make sure you have CCSM installed
open it and look for window management
Look for something that say something about defult window manager (it might say metacity?) type in emerald

---

### Post by rixtr66 on 2008-07-18
what is ccsm??

---

### Post by jerome1232 on 2008-07-18
It's a settings manager for compiz, for more
info you can type
```
sudo apt-cache show ccsm
```
to install
```
sudo apt-get install ccsm
```

---

### Post by rixtr66 on 2008-07-18
rick@rick-laptop:~$ sudo apt-cache show ccsm
W: Unable to locate package ccsm
E: No packages found
rick@rick-laptop:~$ sudo apt-get install ccsm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ccsm
rick@rick-laptop:~$ 


thats what i got
rick

---

### Post by LittleLORDevil on 2008-07-18
Look for compiz settings manager in Add/Remove. Install that.

---

### Post by jerome1232 on 2008-07-18
might need to enable multiverse or universe repositories.

you can do that under
system>>administration>>software sources

poke around you should be able 
to check multiverse and universe

once enabled do
```
sudo apt-get update
```
and rerun the other commands

---

### Post by philinux on 2008-07-18
sudo apt-get install compizconfig-settings-manager

sudo apt-get install fusion-icon

Should help

---

