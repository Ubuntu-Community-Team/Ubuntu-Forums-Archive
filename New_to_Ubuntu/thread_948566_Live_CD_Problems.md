---
title: "Live CD Problems"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by Orca239 on 2008-10-15
I'm trying to run Ubuntu from a Live CD (the Try It option), but I'm having a few problems (and this is my first time trying Linux-based stuff).  I downloaded it, checked the hash thing, and burned the image to a CD.

I'm able to get to the screen that asks for the language and gives the options to try it or install, etc.  The first time I started up with the CD in there, I came back to find the language screen had frozen and a horizontal scratchy white-ish looking line had appeared over the center of the screen.

I ctrl+alt+del'ed and it re-did the boot up.  This time I selected English and it went into the options.  I selected the Check for Errors or whatever option, and came back a bit later to find that it hadn't frozen, but the scratchy line was back.

I re-did the boot up again, and this time went straight for the Try It option.  The screen goes unresponsive, but the line doesn't appear.  I waited for a few minutes and eventually it allowed me to move around the menu again.  I tried it twice more, but nothing ever happens.

The computer I'm trying to use it on is a Dell Dimension E510 with Windows XP (SP2).

Thanks for any help, and sorry for not knowing what I'm doing. =P

---

### Post by SunnyRabbiera on 2008-10-15
Mybe it is a bad burn, you may wish to try to burn your Ubuntu disk at a lower speed.

---

### Post by Orca239 on 2008-10-15
I just tried burning it at half the speed (5x) and now when I choose Try It, it shows a loading box and says something like "Loading Linux kernel..." and gets to 100%, and then freezes.  When I tried to check the CD from the menu, it did the same thing, but at 100% a much bigger color-specked staticy line came up, and then it froze.

Edit:  Error came up

[179.097774] invalid compressed format (err=2)
[179.097774] Kernel panic-not syncing: VFS: unable to mount root fs (can't see some text) wn-block(104,1)

---

### Post by az on 2008-10-15
Does memtest show any errors?

---

### Post by Duck2006 on 2008-10-15
Try a text base install.

---

### Post by Orca239 on 2008-10-15
Well I'm not actually installing Ubuntu, so unless there's some type of Try It that way as well...

And I'm running the memtest now.  It's been going for almost four hours.  About how long does it take or how many tests are there?  I think it's on #7 right now.

Edit:  Oh, it just went to #4, so I guess those aren't what I thought they were.  =P

---

### Post by LowSky on 2008-10-15
memtest is testing your systems memory, nothing to do with the CD being burnt properly... end it at any time

if you want to try it out you can do so from Windows using Wubi
[http://wubi-installer.org/](http://wubi-installer.org/)
it will install ubuntu as if it was a windows program. I personal hate it and have said my piece a while ago, but it make unistalling very easy

---

### Post by Orca239 on 2008-10-15
Alright I installed that thing you suggested to try it, rebooted and chose Ubuntu, and then it went into some sort of installation thing.  I went away for a bit and came back to find that Windows XP had loaded. o.O;  Any ideas?  Thanks.

---

### Post by Splappy on 2008-10-15
Reboot and chose Ubuntu again.

---

