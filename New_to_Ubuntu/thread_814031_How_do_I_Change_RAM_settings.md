---
title: "How do I Change RAM settings?"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by arashiko28 on 2008-05-31
I have been using Xubuntu nearly for a year now, but my RAM capacity has been diminished to 122MB from 256MB, I guess that I did it by myself when I changed on the Xorg the amount of MB for video, since it's integrated withing board, I took 32MB for video. But now, there's this bug and I can't change anything on Xorg more than the keyboard layout. How do I change it back to it's original capacity?

---

### Post by SOULRiDER on 2008-05-31
Check this out, it might help you.
[http://ubuntuforums.org/showthread.php?t=789196](http://ubuntuforums.org/showthread.php?t=789196)

---

### Post by arashiko28 on 2008-05-31
Has nothing to do, on Bios setup I get to change between 32MB and 64 MB, I selected 64MB, with dmesg it shows:

> [  47.430378] Linux agpgart interface v0.102
[   47.704611] agpgart: Detected an Intel i810 Chipset.
[   47.837954] agpgart: AGP aperture is 64M @ 0xd0000000

What i mean is that I have something like a RAM kidnap, when I started the thread I was working with only 256MB of RAM, so I added another 256MB and it raised to 248.7 MiB, so what's really going on?! It should be 512MB detected, or if it's sharing at least a bit over 400.

I have tested both memories, individually and in both sluts, I know they are working, so the problem is configuration. Please help!

---

### Post by arashiko28 on 2008-05-31
Please, I need some help in this, I can't access xorg to change the configuration, it only allows me to change it on the keyboard. How do I get rid of this bug? all i have found is that the bug exists, but nothing about fixes. Also, I have now lost my panels and can't make it come back.

---

