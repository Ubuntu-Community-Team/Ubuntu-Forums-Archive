---
title: "Buffer I/O error on device hda Logical block"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by 4ph3x7w1n on 2008-05-15
I am not very computer savvy, i was given i live disk for ubuntu and tried to put it on one of my hard drives...after completing the installation (about 7 times) i kept receiving a message saying, disk boot failure, insert system disk and press enter. after i got this message multiple times, it finally comes up with this message saying buffer I/O error logical boot, i am completely clueless on other forums i have read, is there any way some one could take me through this?

---

### Post by spiderbatdad on 2008-05-15
Can you post some specs regarding this computer ie. model, memory, graphics card?
It sounds like you need to specify some boot parameters from the installation options screen by pressing F6 and deleting --quiet splash from the end of the line, then adding the appropriate parameters: for example noapic nolapic.

---

### Post by john_spiral on 2008-05-15
> **4ph3x7w1n said:**
> I am not very computer savvy, i was given i live disk for ubuntu and tried to put it on one of my hard drives...after completing the installation (about 7 times) i kept receiving a message saying, disk boot failure, insert system disk and press enter. after i got this message multiple times, it finally comes up with this message saying buffer I/O error logical boot, i am completely clueless on other forums i have read, is there any way some one could take me through this?

before your computer starts press F2 or del to get into the BIOS.

within the BIOS check your boot order, i.e what disc the computer uses first to boot from.

John

---

### Post by 4ph3x7w1n on 2008-05-15
Here is the order

Hdd-1
Hdd-2
CDROM
Disabled

i have messed around with the order multiple times, i see many post of this type of problem, but like i said, my computer skills aren't that high so i don't understand most of what they are saying

---

### Post by 4ph3x7w1n on 2008-05-15
> **spiderbatdad said:**
> Can you post some specs regarding this computer ie. model, memory, graphics card?
It sounds like you need to specify some boot parameters from the installation options screen by pressing F6 and deleting --quiet splash from the end of the line, then adding the appropriate parameters: for example noapic nolapic.

I bought this computer off of a friend, its custom made..
I have currently 3 harddrives (2 40gigs and a 30gig), i have a broken IDE cable, one female port works, the other is broken... i have an ATI graphics card but im not sure of the model

---

