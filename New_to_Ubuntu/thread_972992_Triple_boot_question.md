---
title: "Triple boot question"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by baddnady23 on 2008-11-06
Just wanted to make sure of one quick thing before i made some changes to my system.

I have windows on one HD and Ubuntu 8.04 on a separate HD.  I have an 84 GB partition at the end of the Unbuntu drive that i am currently not using and is formatted for NTFS.  I use GRUB to boot with.

I would like to install either linux mint or mandriva in the empty 84 GB space.  Can I do that with out having to alter grub or will the grub automatically get updated and all my other settings remain the same once i install the third system into the empty space?  thanks!

---

### Post by caljohnsmith on 2008-11-06
If you let the new Linux distro install its Grub to the MBR (Master Boot Record) of your booting drive, it will take over the booting process on start up; you might get lucky and it will detect your other OSes and set them up correctly in Grub's menu.lst/grub.conf. But what I would recommend is letting Ubuntu stay in control of your booting process, and when you go to install the other distro, have it install its Grub to the boot sector of its partition rather than the MBR of your HDD. Then in your Ubuntu's menu.lst, just add an entry for the new distro like:
```
title New Linux Distro Grub Menu
configfile (hdX,Y)/boot/grub/menu.lst
```
And you would have to specify the correct (hdX,Y) for the new Linux partition. That's the basic idea, let me know if you would like more specifics.

---

### Post by bscbrit on 2008-11-06
Grub **should** remain the same with the exception that there will be menu items for each of the OS that you have installed. However, I do not use Mint or Mandriva so, particularly for the latter, you might have to do some manual configuration of grub if it doesn't recognise both the Windows and Ubuntu OS.

However, just to provide a safety net, you would be wise to make a copy of /boot/grub/menu.lst before you start the upgrade.  If there is some unforeseen event (e.g. power failure or hardware problem) during the installation then you will be able to recover the situation easily. Also, if your new modified Grub is not quite correct you will have all the details to hand to change it.

During the installation, you will have to tell the installer to use the partition that is currently formatted as 84GB ntfs.  Take your time because, until you actually tell the partitioner to begin saving disk changes and reformatting the partition nothing has been changed on the drive and even a reset will simply take you back to where you are now.  the installer will give you a display when it is about to make irreversible changes so check all of the details that it gives to make sure that you are happy with what is about to be done.  You can share your existing swap partition between any number of linux installations.  Only one of them will run at once and they will each use the same space for swapping data.

---

### Post by alienexplorers on 2008-11-06
I am currently running Windows XP on drive sda and Ubuntu 8.04 and 8.10 on drive sdb.  When I loaded the 8.10 linux it detected all operating systems and setup grub correctly.  I see no reason why you could not run Linux Mint or mandriva as long as they use grub.  Not sure what would happen if the last distro ran lilo.

---

### Post by baddnady23 on 2008-11-06
what is the command for finding the HD x,y values?

---

### Post by caljohnsmith on 2008-11-06
Grub's numbering begins with 0, not 1, so it goes like:
```
sda = (hd0)
sda1 = (hd0,0)
sda2 = (hd0,1)
sda3 = (hd0,2)
sdb = (hd1)
sdb1 = (hd1,0)
sdb2 = (hd1,1)
sdb3 = (hd1,2)
...etc.
```

---

### Post by alibro on 2008-11-12
You might want to get a copy of Linux Format magazine issue 112 (not the current edition but last months). It has a four page tutorial for doing exactly what you are asking.

Cheers
Alibro

---

