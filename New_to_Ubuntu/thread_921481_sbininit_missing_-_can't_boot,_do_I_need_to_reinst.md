---
title: "/sbin/init missing - can't boot, do I need to reinstall?"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by Rorke on 2008-09-16
OK - I have no file /sbin/init
I don't know what else is missing.
I have retrieved all the essential data, but it did take me quite a few weeks to get Ubuntu working properly (sound, graphics, java etc).
I have run Super Grub Boot but that doesn't fix the problem.
Any ideas? Otherwise I toast the system and start again!
Thanks in advance.

---

### Post by phidia on 2008-09-16
If you feel experimental you could run the livecd and compare & copy missing directories/files to your install. If not re-install.

---

### Post by Rorke on 2008-09-16
Is there some kind of 'repair' option (such as in the competitor's install disk)?
I just copied the entire /sbin dir from a rescue disk, but I can only guess at what will happen when I reboot! (Or how it disappeared in the first place!)

---

### Post by Rorke on 2008-09-16
Also I'm still unable to mount the selected partition (or any) from Grub.

---

### Post by bodhi.zazen on 2008-09-16
What did you do to get yourself into this predicament ?

---

### Post by Rorke on 2008-09-16
Well, I was moving my partitions with GParted and had a power failure.
I tried repairing with GParted from the Live CD, but there seemed to be a problem.
I got a copy of testdisk and found 2 deleted Linux partitions.
At first I undeleted the wrong one.
Then I undeleted the correct one and re-deleted the old one.
Then I got Super Boot Grub and tried repairing the Grub, but I get 'Unable to mount'
Don't know why, really. I just wanted to play Medieval Total War 2 so was installing XP on a new partition.

---

### Post by bodhi.zazen on 2008-09-16
OUCH !!!!

Well, unfortunately it seems the partition is incompletely recovered and it is probably best to recover what data you can and re-install.

---

### Post by Rorke on 2008-09-17
Yeah - luckily I managed to get all the data off! I'd like to learn more about partitions and recovery, but for today I'll just be reinstalling!
I guess it'll also teach me to buy a Chinese Toaster from ASDA for £3.95 coupled with an oversensivive house electrics trip switch!

---

