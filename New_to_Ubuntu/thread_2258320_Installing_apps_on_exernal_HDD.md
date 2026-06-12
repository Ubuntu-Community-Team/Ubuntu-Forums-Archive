---
title: "Installing apps on exernal HDD"
date: 2014-12-26
forum: New to Ubuntu
---

### Post by andrew183 on 2014-12-26
Hi, everybody!
I have recently installed ubuntu 14.04 LTS on my internal hdd as my only OS.I have a really small HDD and i don't have enough space for all the applications that i'm going to install.However,i have an external HDD with more than enough space for all of my data.My question is, how can i install apps on my ext HDD?In the software center i do not see any option to enable this.I have searched the forum and the "Help" app with no succes.I am new to Linux,and i have only opened the terminal once or twice.

Ps:Sorry for my english.

---

### Post by Holger_Gehrke on 2014-12-26
Welcome to Ubuntu and the Forum !

The Bad News first: there is no option for this in the Software Center because that's not the way it's usually done in Unix-like operating systems. Programs need to know where in the file system they are at the time they are compiled and make assumptions about various paths at run-time. So the places the files go are fixed in the package files.

How small is "really small" ? I've been running Ubuntu 10.?? and 12.04 on a netbook with a 100GB Partition for the last four years and never even come close to filling it and a different Linux before that on an EEE 701 with only 4GB. So with a bit of care in selecting programs and regular clean-up it should not be a problem.

If the space is absolutely too tight for anything and switching out the HD for a model of larger capacity is not an option, you might thing about mounting a partition on the external disk as '/usr'. The most (actually almost all) programs will go there. Of course then the system would be useless without the external disk.

---

### Post by Impavidus on 2014-12-26
The package manager installs software in certain directories, controlled by the instructions present in the package files. It's up to you to decide which directories are on an external drive or on an additional internal drive, by automatically mounting the extra partitions at that directory. But moving applications to an external drive has some complications. If you move /usr to an external drive, the system without the external drive will be really bare bones, not even a GUI. It will boot though, and you will be able to type using nano or ed.

You should be capable of running an Ubuntu system with lots of installed software from a 15GB drive. If you're careful it may fit in 10GB. If you really must move software to an external drive, it may work best if you just move the data directories of a few data hungry applications to the external and create some symlinks to keep them accessible from their original locations or mount a partition on your external drive at the data directory of your most resource hungry application.

---

### Post by andrew183 on 2014-12-27
Thank you for your help.
My HDD has 37 GB and i plan on installing some games and other large applications.I have used windows and i have kept all of my programs on the external HDD,so i am used to keeping it connected 24/7 .Where can i find a guide for moving the data directories or mounting a partition on the external HDD as /usr ?

---

### Post by approveme on 2014-12-27
Welcome here..

---

### Post by Jonathan Precise on 2014-12-27
Hello andrew183.

Hope you don't have too many programs installed! Your best bet could be a reinstall, as moving the programs are a pain. Make sure you have a Live DVD/USB handy, or download Ubuntu ISO and burn to DVD.

**_[SIZE=5]IMPORTANT: BACK UP YOUR DATA!!![/SIZE]_**

Backup your files from your internal HDD. You can use the Backup tool to backup to another HDD that you shall not use for programs, but I prefer personally to do it by hand, so I can ensure everything gets copied. This must be copied, because the internal HDD WILL BE WIPED.
Also (this, I think, MUST be done by hand), back up the data (if any) that you have on your external HDD that you will use for programs, as it WILL BE WIPED. 

Connect your external HDD, close File Manager, right-click on the HDD on the bar on the left, and select "Unmount", and wait until the HDD icon disappears. Go through the installer, until you get to the part of "Install Ubuntu alongside them", "Erase disk and install Ubuntu", and "Something else", choose "Something else" to get to the manual partitioning (Yikes!). Don't worry, it seems harder than it actually is.

Make sure your external HDD comes up as /dev/sdb1. Now, select your main partition (the one that has Ubuntu), hit "Edit", in the combo box, choose "EXT4 Journaling Filesystem", select "FORMAT THIS PARTITION" (e.g. WIPING ALL DATA), and type "/" in the mountpoint (no quotes). Select the swap partition in the same manner, but choose Swap Space instead. Then hit OK.

Select /dev/sdb1, and hit "Edit", and preform the same procedure as the FIRST partition internal HDD, EXCEPT you should type "/usr" (again, without quotes) into the Mountpoint. Yes, mark for formating and WIPING, yes choose EXT4.

Continue the installation as normal, reboot, and it should be done!

---

### Post by Impavidus on 2014-12-27
I wouldn't move /usr to an external drive unless the root partition has to be smaller than 6GB or so. 37GB should be plenty for applications. Because of its extensive use of shared libraries, there is less duplication on Linux and therefore more efficient disk space usage than on Windows. Every application moved to an external drive will start a little slower than when it is on the internal drive. You may be able to move /usr of your installed system to an external drive (quite easy actually, using a live disk), but I really don't see the point.

You may be able to move entire directories with data belonging to applications to your external drive. Check their size first, they may be smaller than you expect them to be. Then replace the data directory on the internal drive with a symbolic link pointing to the directory on the external drive. Most applications will accept that. You can also move a very large data directory to an entire partition on the external drive and modify fstab to mount it at the original location of the data directory. It's a bit like [this]("https://help.ubuntu.com/community/Partitioning/Home/Moving"), but simpler, as the directory won't be in use during the operation. Most applications keep their data in /usr/share/appname, games often in /usr/share/games/appname.

Applications that allow for optional manual installation of large data sets (flightgear comes to mind) often allow installation in a costom directory. I sometimes keep these data in /usr/local, which is in my case on a separate partition on the same drive, but the same idea could apply to an external drive.

In any case, make sure the partitions on the external drive use a native linux file system, like ext4.

---

### Post by andrew183 on 2014-12-28
Thank you all for your replies,they satisfied my curiosity and solved my problem :) . This is solved.

---

