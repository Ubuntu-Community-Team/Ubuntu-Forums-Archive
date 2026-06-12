---
title: "Fatal no bootable medium found Ubuntu 12.04"
date: 2012-05-26
forum: New to Ubuntu
---

### Post by jjz on 2012-05-26
Absolute beginner here.

I'm using Oracle VM VirtualBox and have installed Ubuntu 12.04 on a laptop running Windows 7 and all is well (except my incompetence). Now I'm trying to do the same on a desktop, Oracle VM VirtualBox, Windows 7, Ubuntu 12.04. When I try to start, however, I receive the message:
FATAL: No bootable medium found! System halted.

I found other similar posts but when checking Settings, System and Storage, my settings seem to be as recommended. And they seem to match my laptop, which is working.

System Boot Order has Floppy, CD/DVD-ROM, and Hard Disk all ticked

Storage has IDE Controller VBoxGuestAdditions.iso and SATA Controller ubuntu.vdi

Any advice/thoughts gratefully received.

---

### Post by wilee-nilee on 2012-05-26
You can copy and paste the .vdi from the original to the new virtualbox vms if you like then just make a new machine when asked just link this machine to the one you put in the folder.

I have a ntfs partition I keep as a share with a W7 set-up and and 3 Linux installs I keep the vdi's of my machine there and can run vbox from all four OS's using the same vdi.

---

### Post by jjz on 2012-05-26
Thank you wilee-nilee. I have started copying the ubuntu.vdi from my laptop--it's going to take a while.

I'm lost, however, when you say "then just make a new machine when asked just link this machine to the one you put in the folder". How do I make a new machine and how do I link this to the other one? Or will it be evident once I have managed to copy the file?

---

### Post by wilee-nilee on 2012-05-26
> **jjz said:**
> Thank you wilee-nilee. I have started copying the ubuntu.vdi from my laptop--it's going to take a while.

I'm lost, however, when you say "then just make a new machine when asked just link this machine to the one you put in the folder". How do I make a new machine and how do I link this to the other one? Or will it be evident once I have managed to copy the file?

So make a new machine on the second vbox and when you get to this screen choose like I have here hit the folder and navigate to where you have put the copied vdi, finish the process like you were making a new machine. Adjust as you like in the settings and you are set.

[ATTACH]218729[/ATTACH]

You want to start with a new machine so if you have one started delete it and make a new one linking the vdi as described. Mine says inaccessible as I don't have the partition open that the vdi is in.

---

### Post by jjz on 2012-05-26
Oh, I can't use the same virtualbox I already created? You mean I have to set up another virtualbox?

---

### Post by wilee-nilee on 2012-05-26
> **jjz said:**
> Oh, I can't use the same virtualbox I already created? You mean I have to set up another virtualbox?

The main part of the virtualbox is the biggest file in its folder for the machine I use a vdi type. You transfer that vdi, make a new machine linking that vdi, and you have the same exact set up.

You only need the vdi or what ever format you have chosen probably to just load it to a different vbox set up.

The vdi contains the partitioned set up of the OS.

Kind of confusing as it is so easy, you would not think it was this easy. :wink:

---

### Post by jjz on 2012-05-26
I'm sorry I'm so slow to understand. Can I copy the whole ubuntu folder from the laptop and just plonk it in the existing virutabox? Or do I have to create a totally separate virtualbox?

---

### Post by wilee-nilee on 2012-05-26
> **jjz said:**
> I'm sorry I'm so slow to understand. Can I copy the whole ubuntu folder from the laptop and just plonk it in the existing virutabox? Or do I have to create a totally separate virtualbox?

No problem, you just want that vdi, put it in the virtualbox vms folder or anywhere really. Open the virtualbox make a new virtual machine. When you get to the screen I posted instead of choosing create a new disc choose use existing hard disc, then click that folder next to it choose other and navigate to where you have put the vdi to link it to this new machine. finish the operation, you are set, except for any tweaks you might want using the settings on the main virtualbox gui.

---

### Post by jjz on 2012-05-26
Now I understand, thanks ever so much. I'll let you know how I get on.

---

### Post by wilee-nilee on 2012-05-26
> **jjz said:**
> Now I understand, thanks ever so much. I'll let you know how I get on.

Cool, my explanations are not always succinct, hardly ever really. :)

---

### Post by jjz on 2012-05-26
Thanks again wilie-nilie, I have Ubuntu installed. Yay!

---

### Post by wilee-nilee on 2012-05-26
> **jjz said:**
> Thanks again wilie-nilie, I have Ubuntu installed. Yay!

Awesome, it is a cool way to have the same set up without all the work. ;)

---

