---
title: "HowTo: Preconfigured Dapper reinstall Script..."
date: 2006-07-27
forum: Outdated Tutorials &amp; Tips
---

### Post by codejunkie on 2006-07-27
With the release of the dapper the installer has undergone quite a few changes, from the text only install, to the livecd installer that gives you a full livecd environment that gives you some customization options. 

This How To will describe how to use that Desktop/Live CD to install Dapper, then with a few common Linux tricks have an up to date, Preconfigured to your liking ubuntu install.

What is needed for this to work:
1: a little time
2: an Ubuntu/Kubuntu/Xubuntu Live/Install Cd
3: knowing what extra packages you want prior to the install
4: a working Internet connection
5: USB Drive, Floppy disk, or some other type of portable/removable media
---------------------------------------------------------------------------

**SCRIPT OVERVIEW:**

As of right now the script package can install custom kernels restore/install your xorg.conf file install nvidia drivers and install a custom selection of packages. 

to install a custom or reinstall your xorg.conf file you need to place one in the /myinstall/xorg folder an uncomment lines 93-100 in the installer script

to install the nvidia-glx package you need to uncomment line 128 in the installer script.
to install the nvidia-glx-legacy package uncomment line 129 in the installer script.
 
Uncomment Line 113 to install the k7 kernel for newer 32bit AMD cpu's
Uncomment Line 114 to install the 686 kernel for newer 32bit INTEL cpu's
Uncomment Line 115 to install the k7-smp kernel for newer 32/64bit multiple processor/dual core AMD cpu's
Uncomment Line 116 to install the 686-smp kernel for newer 32/64bit multiple processor/dual core INTEL cpu's
Uncomment Line 117 to install a custom kernel package you've created yourself.

to install all multimedia codecs, xchat and the nautilus-open-terminal extension Uncomment line 148 in the installer script.
---------------------------------------------------------------------------

Well lets get Started...

download the attached script package extract it by right clicking on it and choosing extract here, add the files you want, and enable the options in the installer script.

after you've personalized the script package containing the custom options/files you want to use for installing/reinstalling ubuntu, you need to rearchive the myinstall folder to preserve file permissions right click on the folder and choose Create Archive then Create. after you've repackaged the archive copy it to a portable device like a usb drive, floppy, etc 

now boot from the install/live cd and preform the install, when the install finishes do not choose to reboot, instead choose the option to continue using the live cd.

now open a terminal and you need to find your root partition so run ```
sudo fdisk -l
```in the terminal it should output something like this 
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         191     1534176   82  Linux swap / Solaris
/dev/hdb2             192        4998    38612227+  83  Linux
ubuntu@ubuntu:~$

```

on mine the root partition is /dev/hdb2 you can find yours by looking at the id number, the root partition usually has an id number of 83. 
now this partition needs to be mounted, start this by creating a mount point, to do that run this in the terminal ```
sudo mkdir /ubuntu
``` now mount the partition with ```
sudo mount /dev/hdx /ubuntu
```remember to replace /dev/hdx with your actual root partition.

now that the root partition is mounted you need to copy the script package onto it. 
open a root file browser, by pressing alt+F2 and enter sudo nautilus, now insert the media that you copied the script package to, and copy and paste the file to /ubuntu and extract the file by right clicking and choose extract here. now we need to chroot into your ubuntu partition do that by opening a terminal and run ```
sudo chroot /ubuntu
```
and last run the script by entering ```
/myinstall/installer
```

when the installer is finished close the terminal and reboot into your new 
system, with no tweaking xsettings, installing extra packages etc. if your like me and reinstall quiet frequently this comes in really handy hope you like it, and any feedback is greatly appreicated.

---

