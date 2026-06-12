---
title: "Problem in installing Windows XP after installing Ubuntu 8.04"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by derisen on 2008-11-08
Hai

Am new to the linux world... and ofcourse to ubuntu!!!

With the CD of [COLOR="Blue"]Ubuntu 8.04.1 LTS Desktop Edition[/COLOR], i installed the linux os in my PC. But after that [COLOR="Blue"]wasn't able to install Windows XP [/COLOR]in the same HDD. 
The bootable CD of windows xp was loaded on the startup but seemed to be in an 'infinite loop checking' after showing the following on the screen - setting up the hardware Configuration...

My [COLOR="Blue"]HDD is of size 40GB[/COLOR]. 
And I partitioned the HDD, on the ubuntu installation, in the following manner.
/dev/sda
//dev/sda1  ext3    /boot      98MB(Primary partition)
//dev/sda2  ext3    /          100001MB(Primary partition)
//dev/sda3  swap               10003MB(Primary partition)
//dev/sda4  Fat32   /windows   28952MB(Primary partition)


I just [COLOR="Blue"]want to configure my pc in such a manner that, it should have a dual boot configuration with Ubuntu and WinXP as OS's[/COLOR].

Any help will be appriciated...

By checking the above HDD size and details [COLOR="Blue"]please give a step by step process(from partition itself) to have the installations[/COLOR].

Thanks in Advance...

---

### Post by roscal on 2008-11-08
Best way I would think is to re-do your installation.
Install XP on a partition first, then install Ubuntu on the remaining free space.

If your XP disc won't install at boot, go to recovery mode and wipe the disc out, then install XP first on a Fat32 or NTFS partition.
You only have 40 gigs?

Ouch.

Maybe split it 22 gigs (or whatever) for Xp, Format the space as Fat32 or Ntfs. Install XP.
Then reboot and install the Ubuntu cd onto the largest free remaining space.

Format this space as ext3 when prompted, and let the Ubuntu install decide its own swaps etc..
.
Now. when you re-boot, you will be presented with the choice of what OS to boot to.

Hope this might helps, I'm a somewhat newb myself (2 years), but I love it.

---

### Post by ugm6hr on 2008-11-08
My suggestion:
Use Ubuntu LiveCD to repartition drive first using GParted (Partition Editor).

Create an NTFS or FAT partition for Windows as sda1 (~20GB).
Then create an extended partition (sda5) for all Linux stuff
ext3 partition for /home (~10GB)
ext3 partition for / (~9GB)
swap partition (1GB or 3xswap is enough unless you use suspend to RAM function)

I don't bother with a /boot partition - but you can have one if you prefer.

Then, restart with Windows CD, and install Windows.  Make sure you pick the correct partition (it will likely only offer one option), and tell it to reformat it before installing (either NTFS or fat - your choice).

Then, restart with Ubuntu LiveCD.  Use manual install option, and select mountpoints as appropriate.

In Windows, install [http://www.fs-driver.org/](http://www.fs-driver.org/) to give you access to /home from Windows.  You will also want ntfs-3g in Ubuntu for access to your Windows partition.

---

### Post by derisen on 2008-11-08
[COLOR="Blue"]roscal and ugm6hr, thanks[/COLOR] for both of you. Your suggestions really helped me in solving the issue.

Iam also posting the [COLOR="Blue"]issue and its solution[/COLOR] for those who want to know about it. Can take it as a reference..

[COLOR="blue"]To have Ubuntu 8.04.1 and WindowsXP in the same PC with dualboot option[/COLOR]:
1. Partition the HDD where the file system can be FAT/NTFS.
2. Install WindowsXP in the primary partition.
3. Create an extended partition for Linux installation with file system as ext3.
4. Install ubuntu 8.04.1 using LiveCD(what i had was LiveCD).    
Create two logical partitions(within the extented partitions) for the root(\) and for linux-swap.

On ubuntu installation, it will automatically check for other operating systems([COLOR="blue"]thanks for ubuntu[/COLOR]) and will add on to the boot loader and Dual boot option will be enabled.

---

### Post by kansasnoob on 2008-11-08
Simple guide:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

