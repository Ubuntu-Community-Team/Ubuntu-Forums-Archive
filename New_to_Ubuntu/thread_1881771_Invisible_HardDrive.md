---
title: "Invisible HardDrive"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by SamUs34 on 2011-11-16
I would like to have gparted help me erase then be able to install windows 7 on to the hard drive i have currently.  As of now when i pop in my windows disc i have an invisible hard drive.  now i would first like some info how to use gparted.  I have Linux on my computer.  I was told there are live discs before accessing gparted.  After that i would have to be able to sell this computer off because i do not need my computer any longer.  Any help with this would be appreciated.  I would like to also know if i will be able to view the hard drive after using gparted.  Thank you for helping for future reference.

---

### Post by buntudawg on 2011-11-16
Hi

Yes Linux partitions are 'invisible' to Windows.

From what I gather you wish to completely erase the HDD and install Windows7?

Do you wish to back up anything from your existing Linux install?

You can download GParted live CD/USB .iso here:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by jjex22 on 2011-11-16
Just a couple of tips for gparted - 

0) Before all others, as buntudawg said, just double check there's nothing left on there not backed up.

1) only do one action at a time, then click 'apply' - the more you store in que, the more errors are likely imho.

2) erase partitions, then click write mbr under the device tab.

3) either leave as free space, or format as fat32 (primary partition) - windows 7 and gparted famously disagree about ntfs, and the windows installer will probably need you to delete the partition anyway!

Finally welcome to the forums! hope linux graces any machine you keep \\:D/

---

### Post by rng on 2011-11-16
There are likely to be more than one partitions on your disk (at least a swap partition in addition to main partition). You can easily find that out by following command in linux: 

sudo fdisk -l           

(it is small L and not 1 or one)
Knowing these may help you plan the easiest method.

---

### Post by Mark Phelps on 2011-11-16
IF, as you say, you are going to erase the drive and reinstall Win7, simply remove the existing partitions using GParted from a CD.  Don't create any new partitions; don't mess with the MBR.

Instead, simply then boot from the Win7 DVD and install it.  It will create and format the needed partitions and will overwrite the MBR as well.

---

### Post by SamUs34 on 2011-11-17
Damn i must say that my windows partition has been deleted.  Now I would like to also know that whenever i am to pop the disc in there is nothing to be seen by the windows setup.  Yes i have everything backed up that i want to keep and would need a new fresh install.  I am very new to ubuntu.  I do not know where i enter any of those commands, and whats the best way to get information from the .iso?

thanks all for the warm welcome.

---

### Post by SamUs34 on 2011-11-17
nvm found a disc to install gparted.

---

### Post by SamUs34 on 2011-11-17
uhg nvm i dont know

---

### Post by buntudawg on 2011-11-17
Hi again

If you have managed to download the Gparted .iso, burn it to a CD.

Boot from that CD.

Select the partitions and delete them.

Shutdown, removing Gparted CD.

Reboot with Windows disk and it should find your HDD and install as usual.

---

### Post by SamUs34 on 2011-11-17
yah i dont really know how to exactly manage Linux. at all really and so it keeps giving me errors, and i only see text files for whenever i try to do something but i understand that thx ill see what i can do for now.

---

### Post by buntudawg on 2011-11-17
Good Luck.

---

