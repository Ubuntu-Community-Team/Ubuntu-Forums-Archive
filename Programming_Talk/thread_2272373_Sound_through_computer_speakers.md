---
title: "Sound through computer speakers"
date: 2015-04-06
forum: Programming Talk
---

### Post by ethan26 on 2015-04-06
Hi people, I am atempting to create a program that plays sound throgh computer speakers but with a twist.it should play a generic beep through the *built in* computer speaker now the external one. Like an old MS DOS virus.
thanks in advance!:KS

---

### Post by wannabegeek2 on 2015-04-08
You can try the program, "beep". 

 I've used it before and at one time it stopped working on an old distribution and I ended up using mplayer and redirecting all the the output to /dev/null. That way you can play any sound file you want.

---

### Post by Holger_Gehrke on 2015-04-10
"beep" doesn't work any more because the kernel module it uses has been blacklisted. Comment out the line 'blacklist pcspkr' in /etc/modprobe.d/blacklist.conf' and beep works as advertised ...

---

### Post by xb12x2 on 2015-04-10
> **Holger_Gehrke said:**
> "beep" doesn't work any more because the kernel module it uses has been blacklisted. Comment out the line 'blacklist pcspkr' in /etc/modprobe.d/blacklist.conf' and beep works as advertised ...

You might not need to edit blacklist.conf. You could just dynamically insert the driver:

**sudo insmod /lib/modules/`uname -r`/kernel/drivers/input/misc/pcspkr.ko**

Check that the driver is installed:

**lsmod | grep -i pcspkr**

If the driver is installed run beep:

**sudo ./beep -f 440 -l 100 -r 5**

When you're done playing with beep, remove the driver pcspkr.ko:

**sudo rmmod pcspkr**

-

---

