---
title: "intel driver and videoram"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by jordanmthomas on 2008-06-11
I am having trouble reducing the amount of RAM X reserves for my graphics.  I have an Intel 915GM and it is able to use up to 128 MB.

The problem is that ALL of this 128 MB is reserved as soon as I start X up.  I'll never need all of it and I only have 512 MB of memory, so for me those extra MB are needed.  

Looking online, it seems the intel driver has an option you can put in the device section like this:
```
VideoRam  32768
``` to only reserve 32 MB of memory.  This seems nice, but if I change this X still steals 128 MB of RAM and this is put in my /var/log/Xorg.log.0:
```
(WW) intel(0): VideoRam configuration found, which is no longer recommended. 
 (II) intel(0): Continuing with default 262144kB VideoRam instead of 32768 kB. 

```
which is a little strange considering it doesn't actually steal 256 MB.

I've found if I use the old i810 driver, I CAN set the RAM but then I get problems with dual monitors.  I like to use xrandr to enable / disable my second monitor but it seems to not work right with the i810 driver.

Does anyone know if there is a way to *force* the intel driver to use the VideoRam line since it obviously understands it but is just being a jerk?  

Thanks for reading this probably lengthy post.

---

### Post by Duck2006 on 2008-06-11
Can't you set the amount of RAM that the video use in your BOIS?

---

### Post by jordanmthomas on 2008-06-11
> **Duck2006 said:**
> Can't you set the amount of RAM that the video use in your BOIS?
Unfortunately, there's no option for it.

---

### Post by jordanmthomas on 2008-06-13
bump

---

### Post by thisiam on 2008-06-13
i would say buy more physical memory. its quite cheap now.

---

### Post by jordanmthomas on 2008-06-13
It may be cheap, but so am I (hence the integrated graphics to begin with).

For the time being I am just using the intel driver until I can get two xorg.confs set up to use with the i810 driver.  One for dual monitors and one for just my laptop's screen.

---

### Post by dca on 2008-06-13
Try this at own risk:  you can try killing 'X' by hitting [Alt]-[CTRL]-[Backspace] key & at CLI type:
 
sudo dpkg-reconfigure xserver-xorg
 
I believe there's an option in there to reset memory settings for graphics card but it will only let you adjust keyboard settings if 'X' is still active and you're using Gnome Terminal, 'X' has to be off...  You may want to wait and see if someone can confirm that this has worked for them...

---

### Post by jordanmthomas on 2008-06-13
Hmm, I might boot off an Ubuntu CD and see if this might work.  I use Arch actually and assumed this problem was with the driver and not distro-specific (which is why I asked here)

It couldn't do any harm.  Worst that'd happen is X wouldn't start, which is no problem for me.

Thanks for the suggestion, I didn't realize it'd ask you about VideoRAM

---

