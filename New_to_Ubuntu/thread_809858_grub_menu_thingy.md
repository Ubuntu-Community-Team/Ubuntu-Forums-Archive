---
title: "grub menu thingy?"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by roflatlife on 2008-05-27
hi everyone
i have ubuntu 8.04 and i want to know how to get rid of the grub(?) menu or something. the thing that lets you choose between which OS to boot into when you turn your computer on. i want to get rid of it so that my computer boots directly into ubuntu. thanks

---

### Post by quelx on 2008-05-27
It's the boot loader so you can't get rid of it. You can change the timeout to 1 second so it doesn't stick around that long.

```
sudo nano -w /boot/grub/menu.lst
```

change the  **timeout         10** to a lower value.

---

### Post by Duck2006 on 2008-05-27
From your Synaptic Package Manager load startup manager.
Then go to System -> Administration -> startup manager.
Then in the boot options ajust the time to 0

---

### Post by cardinals_fan on 2008-05-27
> **roflatlife said:**
> hi everyone
i have ubuntu 8.04 and i want to know how to get rid of the grub(?) menu or something. the thing that lets you choose between which OS to boot into when you turn your computer on. i want to get rid of it so that my computer boots directly into ubuntu. thanks
Before following any of this advice, make a copy of the file /boot/grub/menu.lst.  You don't want to lose it ;)

Hit Alt-F2 and type the following:```
gksudo gedit /boot/grub/menu.lst
```
Find the place where it says "timeout" and change the number after it from 30 to however many seconds you want GRUB to wait (0?).  

**NOTE:** If "timeout" has a '#' before it, type "timeout {your second amount here}" underneath on another line.

EDIT: We all replied at the same time ;)

---

### Post by tk03759 on 2008-05-27
well grub isn't just a menu. it's also a bootloader. it tells your computer to boot into the operating system, so you can't remove it.

you can make it boot automatically though if you'd like.

go into ubuntu and open a terminal.

type:

```
sudo gedit /boot/grub/menu.lst
```

Now in menu.lst, find the text "timeout     10" and remove the "#" before it, if there is one. This will tell grub to boot the default operating system after 10 seconds, normally the first operating system that would appear in the menu. If that operating system is not ubuntu, you can take the ## out before "default num" to tell it what os to boot. The numbering is based on where the selection would be in the list, starting from the top with 0.

You can change the amount of seconds too if you'd like by changing the number after timeout.

Hope that helps.

---

### Post by kansasnoob on 2008-05-27
I got some great suggestions here:

[http://ubuntuforums.org/showthread.php?t=808132](http://ubuntuforums.org/showthread.php?t=808132)

But before I ever fiddled with the GRUB menu I'd burn a Super GRUB Disk just in case you hose things:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

But it's fairly easy to "hide" the GRUB menu, but that will not reduce the boot time.

Why is this bothering you? Long boot time? I doubt editing GRUB would change that unless someone manually increased the "timeout" to a ridiculous sum, 3 seconds is normal on a full install and 10 seconds is the default on a dual boot.

---

### Post by kansasnoob on 2008-05-27
This is probably WRONG:

"3 seconds is normal on a full install and 10 seconds is the default on a dual boot"

I forgot that I use my own repetitive install disc that I created with Partimage. Sorry.

Sometimes my fingers (and/or mouth) get ahead of my brain.

---

### Post by spiderbatdad on 2008-05-27
There is a hide menu option in the /boot/grub/menu.lst file:
```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		6

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
**#hiddenmenu**

```
Simply uncommenting will hide the grub menu. As the above comment says, "Press esc (at start up) to see the menu."

---

### Post by mwillams73 on 2009-04-20
mine is already uncommented and yet i still see the menu, so how do i go about fixing this ? I just dont want to see the menu, Im not running anything else but hardy on my box and if i have to get to the grub i can always just hit escape.

Heres what my menu.lst shows: 
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu


So my question is why do i still see the menu ?

---

### Post by mwillams73 on 2009-04-20
Nevermind I had to uncomment the timeout for some reason, but that still doesnt explain why in start up manager i have it set to not show the grub menu, and also to not have the countdown and yet the menu and the countdown still occured. Oh well i figured it out even if it doesnt make sense. I think this is the reason many noobies think its so hard to get things working in ubuntu, whats the point of Start up manager if it doesnt do anything? well other than sorta easily change the usplash( that is of course if you can find one that works, cause the guys that make them dont say what version they are!) Any ways Thanks you guys!!

---

### Post by mikechant on 2009-04-20
> whats the point of Start up manager if it doesnt do anything? 

But it does do something - even if you've got one OS, don't need any choices etc., it actually starts the process of booting Ubuntu. Also, when you apply routine security updates etc. which affect the kernel, menu.lst will be automatically updated and then grub will know that it should load the new kernel. And if that new kernel fails (not likely, but if it does) then grub gives you the ability to load the previous kernel. It also gives you the ability to boot in recovery mode - e.g. if you forgot your password. And it lets you run memtest86 if you suspect you have bad RAM. So grub does a number of useful things even if you're not booting multiple operating systems.

---

