---
title: "[SOLVED] Adding Ubuntu to a Linux only system"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by Tom Atkins on 2008-08-22
I have a PC with two 74.5GB drives. Suse 10.0 is on hda, nothing on hdb, and GRUB is the loader.
hda1 109.7MB linux native /boot
hda2 1.0GB Linux swap swap
hda3 73.4 GB Linux native /
all the above are in reiser format.

I purchased the Ubuntu 8.04 LTS DVD and The official Ubuntu Book third edition.

How should I partition hdb?
What format shoud I use for the disk?
How do I add Ubuntu to GRUB?

Also, I have noticed how some people have been able to add sections of messages to their posts. Is their a manual for the Forum software? I have not been able to find it.

Thanks in advance for any help. I may not be able to reply soon as I am in the middle of TS Fay (actually it is West of here but the center did go right over us last night.) and the power keeps flicking on and off. I don't think I will try anything un till things are more stable.

Tom

---

### Post by tuxxy on 2008-08-22
The installation guide should answer your questions

[https://help.ubuntu.com/8.04/installation-guide/i386/index.html](https://help.ubuntu.com/8.04/installation-guide/i386/index.html)

---

### Post by Paqman on 2008-08-22
Depends. The easiest thing to do would be tell the installer to use the whole second drive. It will then sort out the details for you.

However, 74.5GB is a LOT for a Linux distro. You could easily put both systems on the first drive and use the second for shared data.

---

### Post by elmoosecapitan on 2008-08-22
At this point, it is a matter of taste and preference. If you use SUSE constantly and watch all your movies and listen to all your music, then clearly SUSE should have a large partition.

---

### Post by Paqman on 2008-08-22
Btw, regarding Grub, the installer will do that for you. It'll create a new Grub menu list, and update Grub to point to it instead of Suse's version.

---

