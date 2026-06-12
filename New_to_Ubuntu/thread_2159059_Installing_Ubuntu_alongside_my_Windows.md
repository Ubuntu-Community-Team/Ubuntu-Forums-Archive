---
title: "Installing Ubuntu alongside my Windows"
date: 2013-07-01
forum: New to Ubuntu
---

### Post by JohnnyCod on 2013-07-01
I have attempted several times to install Ubuntu on my hard drive.  I wish to have Ubuntu and my Windows on the same HDD.  When I first attempted it, I thought it  was installing on my HD.  But when I went to get updates, got error saying I had run out of space (I have a 600 Gb HHD).  Turns out it was installed on my USB stick. Whenever I try to go back and install, I do not get the option to install alongside windows.  My only options are to wipe Windows off and install Ubuntu, or select the partition myself.  I do not know enough to do it myself.  I did use a third party software to partition some of the HDD, where I thought I could put the UBuntu, but when I am in Ubuntu, it tells me that partition is unusable.

---

### Post by oldfred on 2013-07-01
From the live DVD or flash drive you are using, go to terminal and copy & paste this into terminal. Post output.

sudo parted -l

It may be easiest just to have an unallocated space and an available primary partition. Then you can use the auto install option. But Windows 7 usually uses all 4 primary partitions.

 Install options, Do not use erase entire drive unless that is really what you want.
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by JohnnyCod on 2013-07-03
root@bt:~# sudo parted -l
Model: ATA TOSHIBA MK6476GS (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  210MB  209MB   primary  ntfs         boot
 2      995MB   624GB  623GB   primary  ntfs
 3      624GB   640GB  15.5GB  primary  ntfs
 4      640GB   640GB  108MB   primary  fat32        lba


Model: Kingston DT 101 G2 (scsi)
Disk /dev/sdb: 31.2GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  31.2GB  31.2GB  primary  fat32        boot, lba

---

### Post by Mark Phelps on 2013-07-03
> **JohnnyCod said:**
> I do not get the option to install alongside windows.  

According to the command results, you already have the maximum of four partitions on the drive.

Did you personally add one of the NTFS partitions or the FAT32 partition? If so, you created a partition with the wrong filesystem.  Ubuntu needs a Linux filesystem -- Ext4 would probably be the best filesystem to use.

---

### Post by fantab on 2013-07-03
Linux does NOT install to NTFS partition. You need to format it with Ext4 filesystem as Mark suggests above. 

On your HDD you have only **4** **Primary** Partitions limit with 'msdos' partition table. If you force a fifth you will have problems. So what do we do? 
We create one of the four Primary Partitions as **Extended** Partition and within that Extended Partition we can have 100 or more **LOGICAL** Partitions.

For you to see the option to install Ubuntu 'Alongside Windows' you must show the installer some free space or 'unallocated space'... 
To Install Ubuntu you need atleast 2 Partitions, one for '/' and the other for 'SWAP'. To do this delete one of the FOUR Primary Partitions you have (use Windows tools only to do this). Leave the space as 'unallocated'. 
Boot with Ubuntu DVD/USB and 'Try Ubuntu without Installing'... Let the desktop load. From the desktop open the Utility GPARTED and from the 'unallocated space' create an EXTENDED Partition. After creating you will notice that you still have 'unallocated space' equal to your Extended Partition. This is normal. From the Unallocated space two or three LOGICAL partitions:
20-30GB Logical Ext4
2-4GB Logical SWAP
All the remaining GB Logical Ext4

When Installing Ubuntu choose 'Something Else' optition to manually control where Ubuntu is Installed. 
Select the 20-30GB Partition and choose MOUNTPOINT=/, USE AS=Ext4 and check Format
Select 2-4GB Partition USE AS= Linux SWAP 
Select the last Parittion MountPoint=/home, Use As=Ext4 and check format. 
Apply the changes and install.

Automated install using options like 'Alongside Windows' is a bit risky... and not recommended.

Good Luck...

---

### Post by oldfred on 2013-07-03
First make a Windows repairCD.
 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

You have to decide which partition to backup all the NTFS data and convert to the extended data.
      
 Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by JohnnyCod on 2013-07-03
I didn't create any of the partitions.  The previous screenshot was using Ubuntu.  This info I got from AOMEI Partition assistant
Partition           file System       Capacity    Used Space     Free Space         Flag           Status
*:SYSTEM     NTFS                    199.0MB      29.13MB          169.87MB               Primary     None
*                 Unallocated                749.15MB      0.00KB             749.15MB              Logical      None
C:JohnsHP     NTFS                      580.67GB   192.36GB        388.30GB               Primary     Boot
D:Recovery    NTFS                        14.47GB     12.86GB           1.61GB                  Primary     None
E:HP_Tools    FAT32       103.34MB     13.97MB         89.36MB                 Primary     None

---

### Post by JohnnyCod on 2013-07-05
Thanx for the help.  Seems to have worked.  Now on to other issues.....no sound.  :):)

---

### Post by mastablasta on 2013-07-05
first of all they are not your windows as they still belong to MS even though you purchased a copy. ;-)

yeah leaving disk space unformatted is best option as Ubutnu will automaticly put itself there.

for sound not working it would be best to open a new thread with good descriptive title and post the result of ***lspci*** command which should hopefully reveal the chip your are using. otherwise for starters run alsamixer in terminal and see if all volume meters are up. you can also see sound chip that is recognised by linux in alsamixer.

i had and still have a fair share of sound issues. it used to work fine the first couple of months but then got borked. i found a few recipes and workarrounds for my chip to force it to work.

---

### Post by gabrielquail on 2013-07-05
Thanks!! This topic helped me a lot too :)

---

