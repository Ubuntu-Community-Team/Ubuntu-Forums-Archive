---
title: "One last duel boot question,Thanks ya'll"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by TymeKyller on 2008-09-04
OK, I was having problems with installing windows, the problem was when I got a new drive I put one to master and one to slave, well Compaq doesn't like that and would not allow me to install windows or Linux or anything, I had to move the master to cable select, took me three days to figure that one out...

Here is where I am at... I have a 40GB and I installed xp pro on a 20GB partition, I have a free 20GB partition and I want to put Linux on it. Will Linux Grub loader automatically set up the duel boot option when I install Linux on the spare partition?

Also I have a 1.0GHz amd cpu and 512MB ram, ati 9000 radeon, When I had Ubuntu installed on here by itself it was severely chugging out on me and when I even had Firefox open and tried to move the curser over the file, edit, view, history etc. buttons it would take like 10 seconds to highlight and allow me to click on them. Even when I scrolled down sites online it was be very choppy scrolling.  I would assume my pc is good enough for Linux, I heard Linux is much more stable and faster on a pc then windows but xp pro seemed to be a lot faster, anyone know why? is my pc good enough for Linux?

Thanks for the help...Really appreciate it.
Tyme

---

### Post by snowpine on 2008-09-04
> **TymeKyller said:**
> OK, I was having problems with installing windows, the problem was when I got a new drive I put one to master and one to slave, well Compaq doesn't like that and would not allow me to install windows or Linux or anything, I had to move the master to cable select, took me three days to figure that one out...

Here is where I am at... I have a 40GB and I installed xp pro on a 20GB partition, I have a free 20GB partition and I want to put Linux on it. Will Linux Grub loader automatically set up the duel boot option when I install Linux on the spare partition?

Also I have a 1.0GHz amd cpu and 512MB ram, When I had Ubuntu installed on here by itself it was severely chugging out on me and when I even had Firefox open and tried to move the curser over the file, edit, view, history etc. buttons it would take like 10 seconds to highlight and allow me to click on them. I would assume my pc is good enough for Linux, I heard Linux is much more stable and faster on a pc then windows but xp pro seemed to be a lot faster, anyone know why? is my pc good enough for Linux?

Thanks for the help...Really appreciate it.
Tyme

Hi Tyme, yes, the Ubuntu installer is very good at finding the Windows XP partition and setting up Grub correctly. The only dangerous part of the install process is the Partition stage; you want to be sure NOT to choose "Guided--Use Entire Disk"! :)

To answer your question, your computer should be okay for Ubuntu, not super-fast, but good enough. I would strongly recommend disabling compiz desktop effects, which you can do by right clicking on the desktop, choosing set wallpaper, then clicking the Desktop Effects tab. I think that may solve the problem you had last time around. There are also "lighter" distros such as Xubuntu (for example) that use fewer system resources.

As far as the Ubuntu vs. XP argument, XP is an 8 year old, DISCONTINUED by MS operating system. I don't think it's reasonable to compare it with the latest and greatest Linux distro (Ubuntu, of course :)) which will place heavier demands on your system. A better comparison would be Vista vs. Ubuntu.

---

### Post by HunterA3 on 2008-09-04
If your install will see the drive, it should give you the option of installing it on the entire disk or on the available free space. I've not installed ubuntu on a pre-partitioned system I've usually had the partition wizard do that for me during the linux install. The amount of RAM you're using should work, but the CPU may be a bit on the slow side. You may be able to compensate for that by using an other flavor of ubuntu with a slightly lighter DE like xubuntu.

---

### Post by eggdeng on 2008-09-04
> Will Linux Grub loader automatically set up the duel (sic) boot option
Yes, it will.
> xp pro seemed to be a lot faster, anyone know why
Could be that you didn't install the best driver for your graphics card. Those specs are very tight for a fully fleged Ubuntu, you might look into something more lightweight like Xubuntu.

---

### Post by TymeKyller on 2008-09-04
Your awesome!!!
Thanks a bunch.... I will make sure not to use "Guided--Use Entire Disk" option!!!!
Thanks again, these forums are great!
Tyme

---

