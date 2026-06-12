---
title: "Installation woes"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by VAinWI on 2008-09-28
I'm new to ubuntu/edubuntu/linux.. I've decided I'm using edubuntu at my school but am having trouble getting it installed correctly.

I downloaded/verified/burned/verified the Live CD. Tried installing, it boots from CD, gives me a menu, I tell it to install, screen goes blank, monitor turns off.

I downloaded/verified/burned/verified the alternate CD.  Tried installing, it boots from CD, gives me a menu, installs, goes all the way through to the end, congratulates me, telling me I only have to reboot and I'll be up and running.  It reboots, loads grub, etc., starts ubuntu splash screen w/ progress bar, turns off.

I'm running rescue at the moment.  When I got to where it asked what device I wanted to use for the root file system, I selected /dev/sda1 since it was highlighted. It's now sitting at a blue screen, with rescue mode in the upper left corner, seemingly doing nothing.

I'm a tch frustrated.. I NEED to figure this out - and soon, I have 20 machines to load this onto.

Help?:confused:

---

### Post by Hobo Joe on 2008-09-28
I'd suggest trying the alternate install disk.

---

### Post by VAinWI on 2008-09-28
I did that, that's how I got as far as I did.

---

### Post by Rayaz on 2008-09-28
In the alternate CD install, what option did you select?
     Install to hard drive
     Install a workstation

You have to select Install a workstation.

---

### Post by Gannon8 on 2008-09-28
Does the computer turn off? Or just the monitor?

If the computer turns off, it may be a hardware problem. Perhaps they are overheating? </wildguess>:D

---

### Post by VAinWI on 2008-09-28
My options:\
Install Ubuntu
Check CD for defects (did that)
Rescue a broken system (was doing that)
Test memory (did that)
Boot from first hard disk

I chose "Install Ubuntu".  Remember, I'm running the alternate installation.. not sure how different they are.

---

### Post by VAinWI on 2008-09-28
It seems like just the monitor turns off - the fan on the computer is still running, lights are still on.  When I hit the power button, it brings up the progress bar for a second before it turns off.

---

### Post by VAinWI on 2008-09-28
Oh - and when it does that, I hear the little drumbeat (that means it's shutting down, doesn't it?)

---

### Post by Gannon8 on 2008-09-28
1.) Please edit your post instead of double (Or triple) posting.
2.) The drum beat is the little splash noise. That means your computer is at the login screen

Anyway, I had this problem once I think, but it was with a laptop and I cannot use that solution.

Ubuntu is not detecting the monitor correctly. Do you know what graphics card you have?

---

### Post by VAinWI on 2008-09-28
Sorry, didn't realize.

ok, that's (maybe) starting to make sense.  I'm running a Inspiron 8000 in a docking station, w/ external monitor/keyboard/mouse.  I don't know what graphics card is in it, Radeon, I think?

On another note - I decided to try to install the OS on another of the machines for school. It's also a P3, ran the Live CD and it seems to be installing correctly up to where it is trying to create partitions.  It starts the partitioner, the status bar shows and completes, but no partitions are showing and I get an error: No root file system is defined. Please correct this from the partitioning menu.  ??

---

### Post by Gannon8 on 2008-09-28
Try using GParted to set up the partitions, then just mark which partitions you want to use for what.

---

### Post by VAinWI on 2008-09-28
Ok. going back to issue #1 - the monitor that turns off.  I think you're right, there's a problem between the graphics driver and the monitor.  The LCD doesn't work on the laptop, which is why I have it in the dock w/ external monitor in the first place.  How do I fix this if I can't see what's on the screen?

Issue #2: GParted doesn't recognize a device.  Does that mean my hard drive is bad?  When I get to the partitioning part of the install, I have no options. It runs the partitioner and then tells me I have no root file system defined and that I should take care of that. I found a page in documentation talking about partitioning through the Live CD, tried that, still no option to create partitions manually.

Thanks for the help.. I'm getting a crash course in PC rehabilitation. :p

Virginia

---

### Post by Excalibre on 2008-09-29
> **VAinWI said:**
> Issue #2: GParted doesn't recognize a device.  Does that mean my hard drive is bad?  When I get to the partitioning part of the install, I have no options. It runs the partitioner and then tells me I have no root file system defined and that I should take care of that. I found a page in documentation talking about partitioning through the Live CD, tried that, still no option to create partitions manually.

Thanks for the help.. I'm getting a crash course in PC rehabilitation. :p

Virginia
I'm pretty sure issue #2 means you didn't assign a partition to be the root file system -- the "mount point" in the partition editor should be set to /

You will normally make at least three partitions: a root partition, which is mounted at "/", (just a slash, it's where most of the operating system and the applications get installed), a swap partition (which doesn't have a mount point, you just select "swap"), and probably a home partition, mounted at "/home", which is where all the users' personal settings and files are. If you don't at very least have a / partition, there's no place for the thing to install it.

---

