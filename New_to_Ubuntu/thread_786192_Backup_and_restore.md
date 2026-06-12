---
title: "Backup and restore"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by laffinet on 2008-05-07
Hi.

I'm currently running Ubuntu 8.04 on my laptop, everything is configured to my liking and running beautifully and I'd like to keep it that way. 
However, I'm planning to install Vista in a dual boot configuration. The only way I can do that is through recovery CDs, which no doubt will wipe my entire hard drive.

Therefore I'm planning to back up and restore my entire system using this [method]("http://ubuntuforums.org/showthread.php?t=35087")

I have two linux partitions, root and home, so I guess I will be creating separate backups.

One thing I haven't figured out yet is how to create the dual boot part, ie installing grub etc. 

Can anyone help me with this ? Thank you.

---

### Post by baddnady23 on 2008-05-07
Try looking here.  It helped me back everything up into a .tar when i was doing some extensive work on my system.   
[http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")

---

### Post by laffinet on 2008-05-07
Oops, should have noticed myself that the grub part is covered in the guide.

Question: how do I determine which hard drive to choose ? See step 4:
> 4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).

In other words, how do I get from dev/sda7 to hd0,6 ?

Other question:
I'm asssuming that my separate /home partition will be mounted automatically when finally booting into the restored Ubuntu since the settings will all be restored as well. Is this correct ?

---

### Post by kansasnoob on 2008-05-07
I installed partimage & partimage-doc from synaptic, and used it to create backups of both my Ubuntu partition and my Windows partition, but I can't verify that I did it right ............ I won't know until I must inevitably someday restore.

As far as the dual-booting goes, I've had excellent luck with APC,s guides:

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

As you can see, it's quite possible to perform a dual boot with Ubuntu installed first. I've done it a couple of times with XP and, other than a bit more fiddling with the GRUB menu, the only real problem is that Windows will assign itself an odd drive letter.

---

