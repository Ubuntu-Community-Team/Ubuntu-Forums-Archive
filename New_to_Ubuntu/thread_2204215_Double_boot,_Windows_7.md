---
title: "Double boot, Windows 7"
date: 2014-02-07
forum: New to Ubuntu
---

### Post by yash2 on 2014-02-07
I have a PC running Windows 7, 2.5 GB RAM, And a total HDD space of 160 GB, divided into 3 partitions, 
C, D, & E, with 50 GB each, and Windows 7 is Installed on C:.
All my business data is Stored on the windows partition and the D: partition, and i do not want to use it.
I want to  install Ubuntu (or lubuntu) on the E Partition (dual Booting), what is the minimum space required for a ubuntu install? i want to resize the E: partition to the minimum required size. 
I would like to allocate any excess to the D: partition so that i can access it from both Windows and ubuntu.
is this possible?
and ive read about some home adn swap partitions needed, is that necessary for a PC having  2.5 Gb ram? I NEVER put my PC into hibernate. its either On of Off, sometimes sleep mode.
How do i go about installing without touching the C and D partitions?

please provide a noob proof answer:)

Thanks a lot!

---

### Post by Frogs Hair on 2014-02-07
Hello and Welcome

Lubuntu requires a minimum of 2Gb  of space  depending on version,  but 3 to 5 would be a comfortable amount of space.  If not hibernating swap would be much less than than the  recommendations I found as long as hibernation is not unintentionally used. . Wubi systems had a swap file rather than a partition and only set aside 255 Mb and windows installer systems were  capible of sleep but not hibernation even by accident. One current swap recommendation I found  is equal to the amount of physical memory and yet another suggested double, but that was a rule of thumb when computers had far less memory and disk space.

---

### Post by G_Ajith_Kumar on 2014-02-07
The minimum recommended size of Hard Disk for Ubuntu12.04 is 5 GB with 512 MB RAM. this would basically take care fo the installation requirements and normal storage. However depending on the type of utilisation of the system, both Disk Space as well as RAM would vary. So with 50 GB disk space avaialbility as well as 2 GB RAM you are likely to be quiet comfortable. 

          You can do some further reading at [https://help.ubuntu.com/12.04/installation-guide/powerpc/minimum-hardware-reqts.html](https://help.ubuntu.com/12.04/installation-guide/powerpc/minimum-hardware-reqts.html) .  The official installation guide covers this topic in very good details. 

         Good Luck.

---

### Post by Votlon on 2014-02-07
found this helpful thankyou :)

---

### Post by oldfred on 2014-02-07
Best to fully back up you important data before attempting install.
With all those partitions, is drive still using basic or did it convert to dynamic partitions. Windows likes to convert to dynamic which is Windows proprietary and does not work with Linux.

Also Linux does not install to NTFS except with wubi, which is now being discontinued as it does not work with new UEFI systems which all new computers are.

Post this from Ubuntu live installer's terminal.
sudo parted -l

       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

