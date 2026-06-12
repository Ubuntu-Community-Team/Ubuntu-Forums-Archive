---
title: "Clean-install Hardy"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by cifdtruckie on 2008-05-08
I tried doing an upgrade from Gutsy, but ran into problems - mainly with the nvidia drivers - and have read that these are pretty common when doing a regular upgrade.

I'd like to clean-install Hardy, but am not completely sure how to go about doing it... I have a dual-boot with XP, and since I'm not too well-versed in this sort of thing, I was wondering if someone could give me a step-by-step on how to do this without screwing everything up...

Any help would be greatly appreciated!

---

### Post by sujoy on 2008-05-08
you already installed ubuntu once (gutsy) so its nothing new. just pop in the disc and choose install, follow the instructions on screen and intead of going with guided partition, choose manual and just format the root partition of gutsy and install hardy there. no need to format the /home and swap partitions

---

### Post by cifdtruckie on 2008-05-08
Thanks!  I wasn't sure if it was that simple!

---

### Post by cifdtruckie on 2008-05-08
Ok... things are going horribly.... I removed the Gutsy partition and recreated a partition for Hardy using the "largest contigious free space" option, but I got "error 14" when I tried to boot.  

I then remembered that Ubuntu is great about automatically setting up a dual-boot with XP, so I deleted the partition I had just created, and resized the XP partition so that it took up the entire disk.  

I then went to install Hardy, and used the "guided" option to set the Hardy partition for half the disk.  It installed just fine, but now I'm getting an "error 17" when I try to boot.  I've tried flagging both partitions as "boot" using gparted, but I get the same result either way....

This is driving me nuts!  I'm really hoping I didn't make enough foolish choices to the point that I'm going to have to reformat the entire drive and start from scratch...

Any suggestions??

---

### Post by Sef on 2008-05-08
GRUB 17 Error:

>  Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

What file system do you have?  Did you change the NTFS to ext3?

---

### Post by sujoy on 2008-05-08
yes its definitely filesystem problem

---

### Post by cifdtruckie on 2008-05-09
Upon further inspection, I noticed that the partition manager actually moved my partitons around on me... it took my windows partition and moved it to another hard drive and stuck it in the middle of a logical partition inside an extended parition that I had created as storage for my mp3s and torrents...
It also put the Ubuntu partition in the extended partition but not inside the logical partition.  It was still showing the partitions on the first hard drive, though...

I only even noticed because I wanted to make sure that I was pointing the boot loader correctly, and traced back the path.

How, and why, would partition manager do this?  At least I know for the future that I can't trust it to do anything automatically... So, yeah, it was so convoluted and confusing that I just wound up wiping both drives and starting over from the very beginning...

AARGH!!

---

