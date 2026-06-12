---
title: "Unable to install GRUB in (hd0) This is a fatal error"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by Gyrotwister on 2008-05-07
Hi,  
I have a new computer with Windows Xp Pro on an 80 Gb drive and
a second 320Gb drive on which I tried to install Ubuntu 8.04.  

I went through the process of manually partitioning separate /, /home and swap partitions and then clicked [install].  
Everything was going swimmingly until a box popped up saying 
**Unable to install GRUB in (hd0)... This is a fatal error**.  

Does anyone know why?  

Could it be because I've not yet activated Windows?

---

### Post by mapes12 on 2008-05-07
I don't think activating windows is the issue. Is XP on hdo? If so then that may be the problem. Here's an interesting thread I found that may have the bones of a solution in it:

[http://ubuntuforums.org/showthread.php?t=740221](http://ubuntuforums.org/showthread.php?t=740221)

---

### Post by Gyrotwister on 2008-05-08
Yes Xp is on hd0.  

Thanks for the link.  That thread will come in handy if I ever lose GRUB.  
My situation is/was different as GRUB would not install off the live CD.  

Anyway, I came home from work this afternoon and went through the same process.  This time it installed OK.  Yippee!  

Now, to move my data over and get the new machine onto the Internet...

---

### Post by ahskrenaim on 2008-05-27
Hey, I have the same problem, I have tried twice to install with the "Unable to install GRUB in (hd0) This is a fatal error" response. I am trying a third time and I hope it will work now. If not, any suggestions?

---

### Post by ahskrenaim on 2008-05-27
The installation failed at 94% again. 
"Unable to install GRUB in (hd0)
Executing 'grub-install (hd0); failed.
This is a fatal error."

---

### Post by ahskrenaim on 2008-05-27
I have a single 500GB hard drive split int 3 partitions, One I already have XP Pro on, one I am trying to put Ubuntu 8.04 desktop edition on, and one I plan to put Vista Business on.

---

### Post by mick8985 on 2008-05-27
can you type ```
sudo fdisk -l
``` into the terminal and paste the results here (terminal is in Applications > accessories > terminal)

---

### Post by ahskrenaim on 2008-05-27
I also am pretty sure the CD is good because I ordered it from the Ubuntu site and they sent it to me, I did not download it.

---

### Post by ahskrenaim on 2008-05-27
The 4th time it worked.

---

### Post by mick8985 on 2008-05-27
Lucky number 4, It's a shame no one seems to know why this error occurs, it doesn't create a great impression for new users.

---

### Post by ahskrenaim on 2008-05-27
true

---

### Post by mick8985 on 2008-05-27
To be honest the installation process of any distribution I always find to be quite flawed in some way, and I have tried plenty, what keeps bringing me back to Ubuntu is the repository is the most extensive of any distribution.

PS. if you have teething problems pm me (using email) and I'll point you in the right direction

---

### Post by antoin_celtic on 2008-08-19
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2c2cba63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       21992   176644769    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           21992       26215    33923072    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           26684       30401    29864835    7  HPFS/NTFS
/dev/sda4           26216       26683     3759210   82  Linux swap / Solaris

Partition table entries are not in disk order

Here's my sudo fdisk -l pasted up

I get this error and have tried installing many many times, tried goin to advanced and trying to install boot loader to other devices but to no avail - Can anyone help??
Vista on 1st partition, xp on second, trying to get ubuntu on third.

---

