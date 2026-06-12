---
title: "What do i need to install to compile from source"
date: 2007-07-11
forum: Programming Talk
---

### Post by Scotty1982 on 2007-07-11
i'm wondering what i need to install to use ./configure make make install

other distro's i used had a option to install the necesary things for this, but i can't find it in ubuntu so i'm wondering what packages are needed.

any help would be highly appreciated, thanks!
~Scott.

---

### Post by Vajra Vrtti on 2007-07-11
Install package **build-essential**. 
I also recommend installing **gawk**. Some applications require it.

---

### Post by mocqueanh on 2007-07-11
You are new comer to Linux, arent you ?

If you 've just install Linux in your PC, you need to install some essential packages to use ./configure

The easiest way with Ubuntu is:
Insert your Ubuntu CD into machine, open Synaptic, mark all packages that not installed and install it.
Or, you can find: build-essentials package in Synaptic and gcc to install them, by default when you install Ubuntu, these packages are not installed. This way is the plan to install GCC (GNU C Compiler ). With some other languages, you need to download other compiler for Ubuntu(Example: Fortran Compiler).

my tips for you are: update and install softwares from Synaptic oftenly, when you install software from Synaptic, you will download many dependcies, useful for you to install software from source, because install from source you have to had enough dependcies before install app. And install online(by Synaptic), if there are missing dependcies, Ubuntu will find and  install them for you

---

### Post by Scotty1982 on 2007-07-11
ok, thanks! their downloading now. i just did all of the ones under development (had to leave a few off because of conflicts) figured that's the easiest way to make sure i have all the ones i'll need. i have plenty space anyways.

I am very new to linux, but i'm getting along pretty good. i like linux a lot better than windows, it's more customizeable. and seems to run more smoothly. only problem i have is there's no driver available for my printer and lexmark seems to want the users to make their own. but that's no big deal, i just installed it on my other pc, and i'll do any printing from there.

thanks a lot for the fast response, that's awesome!

Have fun!
~Scott.

---

### Post by Vajra Vrtti on 2007-07-11
What application do you need that requires installation from source?

---

### Post by Scotty1982 on 2007-10-14
Pidgin and PSPVC (PSP Video converter)

using gusty gibbon now though (7.10) so pidgin is now included... so just PSPVC

---

### Post by sstusick on 2007-10-15
You can get Pidgin deb at Getdeb.net

---

### Post by #Reistlehr- on 2007-10-15
If you see it fail when doing ./configure, it will tell you what it failed at. 

99% of the time, you slap lib infront and tack on -dev at the end of what it failed at, and sudo apt-get it, and you're set.

---

