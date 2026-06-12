---
title: "system being unresponsive when left on 10.04"
date: 2012-04-04
forum: New to Ubuntu
---

### Post by augustkk on 2012-04-04
Whenever I leave my computer on and unattended for a couple hours or overnight it becomes very slow and unresponsive and I'll have to restart.  Is there any way to figure out the problem and solve it?

Running ubuntu 10.04 64bit on a dell d620.
Any help appreciated

---

### Post by dolphin194 on 2012-04-04
Make sure that your computer is not overheating. D620s can get very hot if their ventilation duct on the bottom is covered, even when the computer is on a flat surface. Try to prop your laptop up with something such as a book to allow the air to circulate through the computer. You could also use a cooling pad to do this. Clean out any vents that are clogged with dust with a can of air, or air compressor.

I have Ubuntu 10.04 *32-bit *on my D620, and it runs great, except for when the computer overheats.

---

### Post by augustkk on 2012-04-07
it only seems to do it when my machine is idle for long periods. When I'm actively using it for hours this doesn't happen

---

### Post by 2F4U on 2012-04-07
Did you check memory consumption and CPU usage before and after that period? A good tool to use is, for example, htop. Is your system going into suspend or hibernate when you leave it alone for a longer period of time?

---

### Post by pqwoerituytrueiwoq on 2012-04-07
```
sudo apt-get install lm-sensors hddtemp sensors-applet 
sudo sensors-detect
```answer yes to all on the second command
you can add sensors to your panel now and watch your cpu temperature
with my laptop 10.04 runs hotter (5-7C idle) than 11.10 (i think it is the kernel)
you could try using the maverick kernel backport and see if that helps
```
sudo apt-get install linux-headers-generic-lts-backport-maverick linux-image-generic-lts-backport-maverick
```if you go beyond maverick's kernel on lucid virtualbox quits working
make sure the air intake is not full of dust

---

### Post by augustkk on 2012-04-07
I ran the commands, how do i add the sensors to panel?
Would a cooling pad work?

---

