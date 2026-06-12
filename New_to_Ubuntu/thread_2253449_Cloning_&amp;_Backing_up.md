---
title: "Cloning &amp; Backing up"
date: 2014-11-19
forum: New to Ubuntu
---

### Post by Greg Mueller on 2014-11-19
Recently had a hard disk failure and it was stressful getting things back together so I decided I better take steps before I have a heart attack or something.
I have Ubuntu 12.04 with KDE Plasma Desktop 4.8.5 on an 80 gb hard drive
I just bought a new 160 gb hard drive

I installed the 160 and here is what the terminal shows

greg@greg-desktop:~$ sudo lshw -C disk

  *-cdrom                 
       description: DVD writer
       product: DVD-RW  DVR-115D
       vendor: PIONEER
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: 1.13
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc
  *-disk:0
       description: ATA Disk
       product: WDC WD800JD-00MS
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sda
       version: 10.0
       serial: WD-WMAM9AES7069
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0005f530
  *-disk:1
       description: ATA Disk
       product: WDC WD1600HLFS-7
       vendor: Western Digital
       physical id: 0.1.0
       bus info: scsi@3:0.1.0
       logical name: /dev/sdb
       version: 04.0
       serial: WD-WX51C1048877
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000df207
greg@greg-desktop:~$

I want to clone the system on the 80gb to the 160gb
Then make the 160 the boot drive

I have been reading that I can use FSArchiver to clone my 160 to my 80 every once in a while (probably once a week)
I say FSArchiver because it says I can clone a bigger driver to a smaller drive unlike other cloning/backup systems that I have read about.

I think I installed FSArchiver using Synaptic but I can't find it, at least by that name

**So how do I do what I want?**

Notice this is in the begginers section (I don't understand real technical stuff)

---

### Post by yancek on 2014-11-19
You can use clonezilla to do that.  Just google 'clonezilla' and you should find there site.  There are several options to download so read through before doing so.  You will need to select the option when running clonezilla to clone the entire drive and will need to make some changes after cloning as it will be on a different drive and it will have different uuids and they will need to be changed in the grub.cfg file and the /etc/fstab file.  Are you more concerned with personal data or the entire system?  There is a backup option in the Ubuntu System Setting.

---

### Post by Greg Mueller on 2014-11-19
The 80gb is of unknown age so my first concern is getting everything cloned to the new 160gb drive.
After that I can mess with backing up.

---

### Post by oldfred on 2014-11-20
I normally suggest  a new install & copy /home over. And export a list of installed apps and reimport that.
That also does a major houseclean of old kernels, log files & other cruft that we should normally clean up but do not.

A clone works best if you restore to the same drive/partition. You have issues of duplicate UUIDs. So you have to manually change UUID, edit fstab, and reinstall grub so it finds new UUID. There are a couple of other places that should also be updated or later you may have issues as it looks for old drive not new one.

I can install faster than imaging and restoring system. And my backup procedure is to just backup configuration data so I can restore system quickly when hard drive fails. No need to backup Ubuntu itself as it is easy to download and reinstall.

       Oldfred's list of stuff to backup May 2011 (still current):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

If you have a separate /home you can easily copy it over to a new partition and then using something else mount but NOT format that partition during install. And if you do not have a separate /home now is a good time to reconfigure. I prefer smaller / (root) partition of 20 or 25GB. I now do not use separate /home but data partitions, but that has to be done after the install and is a bit more complicated.
      
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[URL="https://help.ubuntu.com/community/Partitioning/Home/Moving"]https://help.ubuntu.com/community/Partitioning/Home/Moving

[/URL] Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

[URL="https://help.ubuntu.com/community/Partitioning/Home/Moving"]
[/URL]

---

### Post by monkeybrain20122 on 2014-11-21
If you use MBR instead of GPT I suggest fsarchiver, which basically clones the file system (instead of cloning the disk, so it works on different hds as long as it is big enough to hold the content, unlike sector by sector cloning like clonzilla)

 It is fast and easy to use. Last time when my hd failed I restored an image and was back in business in less than 15 minutes during which I just read a book (I don't clone the data, they are backed up separately, so the image consists of only /root and /home without Vides, Downloads, Music etc) I don't have to worry about installing all the apps again, tweaking configurations and so on.  It will take longer just to reinstal the OS, let alone the applications, the tweaks and system config etc (not all the config files are in /home)

Unless you want to boot the clone and the original on the same machine (say you have cloned your system to an external drive as a portable and boot it off your own computer to update, or f you use the clone for tests) you don't need to wrry about uuid and fstab, everything is copied exactly. 

You need two commands, one to clone/copy, another to restore. A external drive to hold the image, a live usb with fsarchiver to restore it ( e.g a rescue CD from link below, or a ubuntu live usb and install fsarchiver from the repo, or you may also use it to clone but you can do it live when in the original install) That is ALL you have to worry about. 
[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)

---

### Post by mastablasta on 2014-11-21
wow I am amazed you found a 160 GB drive. here they do not sell anything below 500GB.

anyway disk to disk clone with clonezilla - step by step - print it out and do it-> [http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone](http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone)

this will do a bit by bit image.

you might also have a look at this: [http://ubuntuforums.org/showthread.php?t=2253350](http://ubuntuforums.org/showthread.php?t=2253350)

but fsarchiver is a more tried& tested solution.

however if you expect that you would be able to sqeeze say 130 GB data onto 80GB disk - you are wrong. well unless you have some awesome compression method.

what these disk images do is they compress the empty space.

---

### Post by Greg Mueller on 2014-11-21
I did download Clonezilla and ran it and it worked great.
My 80gb drive is using less than 30gb. I plan to do a Clonezilla copy every week or two, but I would like to have a daily backup of Thunderbird and Firefox and maybe a couple other things
I did download FSArchiver but am still studying it

I found the 160gb drive on Amazon for less than $50 shipped

---

