---
title: "Only 130 of my 320 GB and 200 GB are recognized"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by Gimming on 2008-09-27
Hey Only 130 of my 320 GB and 200 GB are recognized

I use the original windows xp installation to make a NTFS system but i can only use 130 GB on both HD.

what do i do?
is there a new program there can partisionere a larger HD?

---

### Post by SunnyRabbiera on 2008-09-27
Ubuntu should be able to recognize all the drive space, but if you are dual boot it will mainly read its partition.

---

### Post by jrothwell97 on 2008-09-27
Welcome to the Ubuntu Forums!

It sounds like your motherboard can't recognise boot partitions larger than around 130gB. I've [encountered this before](http://crashedpips.co.uk/wordpress/2007/08/30/lessons-in-replacing-your-hard-disk-2-the-bios-is-not-happy/) and it's quite easy to work around, so don't worry.

If both disks are going to be in your machine at the same time, what you can do is create a Windows partition on disk 1 around 100gB in size, and a partition for your My Documents folder on the remainder of the disk (you just need to tell Windows to use that drive as your My Documents folder). The same can go for Ubuntu: create a / partition smaller than 130gB, a swap partition around twice the size of your installed RAM, and one more for /home.

Good luck.

---

### Post by Trav1s on 2008-09-27
If you used XP SP1a, then there is a size limit to 130GB...  

You will need to go into the control panel, administration, disc management and then create partitions...

It's a pain to do.  If you want to get around this, you will need XP SP2 to begin with.

---

### Post by jrothwell97 on 2008-09-27
> **Trav1s said:**
> If you used XP SP1a, then there is a size limit to 130GB...  

You will need to go into the control panel, administration, disc management and then create partitions...

It's a pain to do.  If you want to get around this, you will need XP SP2 to begin with.
That's strange... I encountered my issues using XP SP2. Maybe they were unrelated.

---

### Post by virtuallinux on 2008-09-27
If you're machine is recent enough to run XP, it's a safe bet that your motherboard can recognize the entire drive. Installing the latest service pack for XP should fix the problem.  Ubuntu shouldn't have any issues seeing the entire drive right out of the box.

---

