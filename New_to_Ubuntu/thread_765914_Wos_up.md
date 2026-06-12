---
title: "Wos up?"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by twp_twm on 2008-04-24
Have successfully downloaded and burnt to CD:
Ubuntu-8.04-desktop-i386.iso. So having changed the boot sequence so that i can boot up from a CD. I placed the cd into the drive and the first thing i saw was the language option. So i choose English and pressed enter. I then selected: Install Ubuntu. The next thing that appeared on the screen was:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash) enter 'help' for a list of built-in commands. 

After waiting a while, just a blank screen?

---

### Post by riven0 on 2008-04-24
It's possible there is something wrong with the cd. Did you burn it at a low speed and do a md5 checksum? Also, there should be an option to check the cd when you first boot up. I would first check it with that if I were you.

---

### Post by twp_twm on 2008-04-24
Hi riven()
I burnt the iso image at the lowest possible speed 16x 
and the Md5 Sum was: 8895167a794c5d8dedcc312fc62f1f1f. I did select the option: Check CD for Defects. But i got the same message as before?

---

### Post by sam_delta on 2008-04-24
did you clicked on start/install ubuntu, in order to boot into live session?

have you tried to install from wubi? (windows)

sam

---

### Post by spiderbatdad on 2008-04-24
Try this: press f6 at the boot options screen. A command line will appear. Go to the end of it and delete --quiet splash. Type in: all_generic_ide and hit enter. If that doesn't work try again with: noapic nolapic

If you can't get any results, you may need to try the alternate cd.

---

### Post by twp_twm on 2008-04-24
Sorry Sam but i don't have a clue who or what "wubi" is?

Tried your suggestions spiderbatdad but still no luck. 
Suppose the only option is i shall have to try the "alternate" cd. Thanks for all the replies though.

---

### Post by sam_delta on 2008-04-24
wubi is a new feature of ubuntu 8.04 that lets you install ubuntu from windows, just insert the cd while in windows

---

### Post by jimrz on 2008-04-24
try this:

At the CD boot menu
Press the F6 key and type in 
```
live boot=break
```
from resulting cli prompt type in
```
modprobe piix
```
```
exit
```

---

