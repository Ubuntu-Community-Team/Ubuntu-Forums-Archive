---
title: "Installed Ubuntu... now not given option to boot into Vista"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by MrPatton84 on 2008-08-06
Hi, 

I've installed Ubuntu onto my Samsung R60 Plus laptop, using the instructions [here]("http://ubuntuforums.org/showthread.php?p=5527348#post5527348"). Unfortunately, during the installation it failed to install the GRUB bootloader, and gave me the option to use LILO instead, which I did. 

Now I have a lovely working Ubuntu installed on my computer, but LILO boots it up automatically, without giving me the chance to boot into Vista, which I would still like to do. 

Any suggestions? 

Thanks very much in advance, 
Chris

---

### Post by OutOfReach on 2008-08-06
Type the following into the terminal:
```
sudo fdisk -l
```
and post the output here.

---

### Post by MrPatton84 on 2008-08-06
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcdec863a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1306    10485760   27  Unknown
/dev/sda2   *        1306       15912   117319680    7  HPFS/NTFS
/dev/sda3           15912       30402   116390912    7  HPFS/NTFS

Disk /dev/sdb: 262 MB, 262144000 bytes
16 heads, 32 sectors/track, 1000 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x0d0c0b0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1000      255984    6  FAT16
chrisjackson84@SamsungUbuntuCJ:~$ 





That's what I get.

---

### Post by OutOfReach on 2008-08-06
Hmm you have 2 NTFS partitions, I'm not sure which one is the Windows installation, but It looks like Windows is sitting on /dev/sda2. Hmm, do you know which partition is the Windows partition?

---

### Post by halitech on 2008-08-06
I could say something smart here like "and the problem with this is????" but that would be counter productive ;) (sorry, been wanting to say it for 2 years now :D )

I would think since the bootable partition is showing as ```
[color=red]/dev/sda2 * 1306 15912 117319680 7 HPFS/NTFS[/color]
``` that it is where your windows install is living. did you use WUBI to do the install?

---

### Post by MrPatton84 on 2008-08-07
You're right Halitech, that is where the Windows Vista installation is. /dev/sda3 is where Ubuntu is installed. 

What's WUBI? I don't think I used this for the install, on account of I don't recognise the name ;)

And yes, Halitech, my girlfriend said pretty much exactly the same thing! :D

---

