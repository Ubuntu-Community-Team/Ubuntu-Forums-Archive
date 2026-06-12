---
title: "Grub error, can't repair from live cd"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by poisonborz on 2008-04-25
Hola, I've tried to install ubuntu with dual boot XP, but... well, something wrong happened.

here's my hdd structure:


sda
  1. win system
  2. ---
  3. linux system
sdb
  1 ---
sdc
  1 ---

So, I've had a live cd install, rebooted, and XP booted in. I realized the livecd default for grub was hd0 (hda=hd0?) so grub was installed to the wrong drive. 

I've followed this tutorial: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

and installed grub on hd1 ( setup (hd1) )
I've restarted, grub started to load, and gave error 17 :(
What can I do now? I guess hd1 is the main hdd, grub is installed, and it should have worked..any time I reinstall it (with above method) it gaves error 17...

---

### Post by aeiah on 2008-04-25
try the supergrub livecd perhaps? is it my understanding that you cant boot to either ubuntu nor windows xp?

---

### Post by aeiah on 2008-04-25
you might want to also check the boot order in the bios, to make sure grub isnt on both but still looking for it on the wrong hdd. if you end up having to reinstall and you cant choose where to put grub, you could always unplug your other drive to force it onto the correct one i suppose. but you shouldnt need to reinstall ubuntu to get this working right. best of luck.

---

### Post by poisonborz on 2008-04-25
Yup, it won't boot, I get error. I'm writing this with the livecd.
What I fear is to lose the ability to boot into XP :(

It is quite possible that right now grub is installed on both drives.
Unplugging a drive wouldn't help, since it's already installed on the right drive, but gives error, even after a reinstall.

---

### Post by ace007 on 2008-04-25
> 
17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.


maybe look at these pages?

[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

[http://www.3till7.net/2007/10/25/grub-error-17/](http://www.3till7.net/2007/10/25/grub-error-17/)

---

### Post by poisonborz on 2008-04-25
Thanks for the links, I begin to understand why I get the error.
I guess this would be the solution (mismatch in bios/grub hdd priority):
[http://ubuntuforums.org/showpost.php?p=3518911&postcount=9](http://ubuntuforums.org/showpost.php?p=3518911&postcount=9)

How can I view the hdd priority map that ubuntu/grub generates? Based on the partition manager results I've wrote on the first post, I've tried a few commands, but terminal says they don't exist...

---

### Post by poisonborz on 2008-04-25
...okay, I've reached the point of desperation.
No matter how I modify my devices.map file, or where I install grub, it gives error 17.

Can anyone give me a suggestion about this? My physical drive map is in the first post, my current devices.map is
```

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

```

I know I just could pop in a Supergrub CD, but I can't burn since I'm with livecd (and I can't install on usb, I'm stuck on the 'mount' part, I don't know how to mount and where) and anyway I want a stable proper solution...

---

### Post by cmo220 on 2008-04-25
Have you tried Super Grub Disk?  I have used it many times for similar issues and it usually surprises me how quickly and easily it fixes the problem.  [http://www.supergrubdisk.org/index.php](http://www.supergrubdisk.org/index.php)    

Nevermind, just saw the end of the last post.  Try using a friends computer to burn it, always works for me.

---

### Post by poisonborz on 2008-04-26
Got supergrub, and I can boot into windows alright - but can't boot to Ubuntu. Supergrub just can't find the system... (when choosing grub&linux, grub gives error 21 - disk not found). Ubuntu is installed for sure. What could be the problem? I did not dare to use supergrub's more advanced tools to find the partition... any help?

---

### Post by poisonborz on 2008-05-10
Okay, for anyone interested, I've finally found the solution, partly by mistake. In the bios, AHCPI mode (so in fact, SATA itself) was not turned on, this caused GRUB somehow not to see any Linux partitions. So, if you install to SATA drives, remember to check in the BIOS if they're set as SATA.

---

