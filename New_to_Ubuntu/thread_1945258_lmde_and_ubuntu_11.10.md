---
title: "lmde and ubuntu 11.10"
date: 2012-03-22
forum: New to Ubuntu
---

### Post by rosswmcgee on 2012-03-22
Hi I  installed ubuntu 11.10 and for the first time allowed

ubuntu to partition, alongside Mint lmde. Ubuntu starts up just fine. How do

get LMDE to start and not Ubuntu? In other words how do I switch boot ups?

If I can't do it then I will do a new install and use the all the space, which is what I normally do. This my first attempt at a dual boot.  ):P

---

### Post by wildmanne39 on 2012-03-22
Hi, in ubuntu try:
```
sudo update-grub
```
Then reboot and you should get a boot menu.
Thanks

---

### Post by rosswmcgee on 2012-03-22
Thanks, I ran it successfully terminal showed the lmde but after shut down still booted to 11.10 with no option other wise.

---

### Post by wildmanne39 on 2012-03-23
Hi, both systems are on the same drive right?

Post the output of:
```
sudo fdisk -lu
```
and we will see if the other system is still there.
Thanks

---

### Post by rosswmcgee on 2012-03-23
Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00089971

  Device Boot      Start        End      Blocks  Id  System
/dev/sdc1  *        2048  319540635  159769294  83  Linux
/dev/sdc2      319541246  625141759  152800257    5  Extended
/dev/sdc5      621475840  625141759    1832960  82  Linux swap / Solaris
/dev/sdc6      319541248  617807871  149133312  83  Linux
/dev/sdc7      617809920  621473791    1831936  82  Linux swap / Solaris

Partition table entries are not in disk order


Yes all on same drive.

---

### Post by wildmanne39 on 2012-03-23
Hi, when you boot have you tried tapping the shift key to see if you get the grub menu?
Thanks

---

### Post by rosswmcgee on 2012-03-23
Ok tried it several times tapping the shift key. Still no option goes straight to Ubuntu 11.10

---

### Post by wildmanne39 on 2012-03-23
Hi, I am going to give you a link to download the boot info script run it and post the results here using code tags which is the # sign and someone with more experience reading it can help figure out what is going on, I thought that the information you posted would make it clear to me but I am not sure if your mint is still there.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Thanks

---

### Post by rosswmcgee on 2012-03-23
Ok will do. It did show up with terminal command sudo update-grub

---

### Post by rosswmcgee on 2012-03-23
Not going to do it lmde is on there when I put the ubuntu install disk it shows it is 

there. I am just going to do a re-install.

---

