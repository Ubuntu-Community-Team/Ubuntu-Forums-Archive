---
title: "?? Clone to larger drive &amp; enlarge partitions"
date: 2012-09-08
forum: New to Ubuntu
---

### Post by franklin_m on 2012-09-08
Hello,

I want to clone my 160Gb drive to a 256Gb SSD, enlarging my Windows and my Ubuntu partitions in the process, and I have some specific "how to do this" questions. I've done some basic stuff, but this is a pretty big deal, and I want to make sure I get it right.

I'm running Release 12.04 (precise) 32-bit, Kernel Linux 3.2.0-29-generic, GNOME 3.4.2 in a dual boot configuration on a Dell Mini 10V netbook. My existing drive has 5 partitions, displayed in GParted from left to right in the folloowing order:

/dev/sda1 fat16 (no mount pt) Dell Utility 39.19Gb (used 9.39)
/dev/sda2 ntfs  (no mount pt) WinXP 70.0Gb (used 48.41)
/dev/sda4 extended (no mount pt) 69.26Gb
/dev/sda5 ext3 / Linux 67.25GB (used 41.43)
/dev/sda6 linux swap (no mount pt) 2.0Gb
/dev/sda3 fat32 (no mount pt) DELLRESTORE 9.76Gb (used 3.03)
unallocated 2.49Gb

What I want to do is to copy these to a new SSD, minimize unallocated space, expand space to both windows and linux, and optimize my swap etc. to appropriate sizes.

I've read to use dd to clone, but do I have to set up partitions first on new drive? Or do I clone first, the use GParted later to expand? will they still be contiguous on the new drive? How do I make sure they are? Does it even matter?

Thanks, [email removed by oldfred]

---

### Post by oldfred on 2012-09-08
Please do not post emails. You will get spammed immediately. We are constantly fighting spammers and they scan our system. 
We also are a forum where everyone is helping everyone and others may want to see what helps solve your issue.

I recently installed a 60GB SSD, but had (still have but not used) XP on another 160GB drive. With SSD you need to use AHCI for trim to work and you really need trim. But XP usually does not have the AHCI drivers. You can reinstall XP with the AHCI driver. I think I found instructions to add AHCI after the fact but it was pretty complicated with direct registry edits. So I just converted to AHCI and stopped using XP. I had promised to stop using XP for 5 years so it was time anyhow. Not sure if XP supports trim or not??

I am a believer in clean installs and have tried to help a few that have used dd and had issues. dd is a low level bit for bit copy and is intended for identical size to identical size copies. dd also has the nickname Data Destroyer as it is very powerful and with that power is the power to overwrite the wrong drive with just a minor typo.

Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

I might partition in advance, restore Windows and do a clean install of Ubuntu. How are you connecting both drives? Or does system support two drives?

Some good technical info on SSDs.
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

### Post by franklin_m on 2012-09-09
Fred,

Thanks for the tip on email addresses.

As for doing a clean install, I'm ok with that, but don't want to lose my data etc. from ubuntu.

What folders should I backup from my existing install to later copy into the new install?

Thanks,
Frank

---

### Post by LiamOS on 2012-09-09
I'm not sure if this will work properly, but I can't see why it wouldn't. If you're interested in this approach, it's probably okay to try, since it's non-destructive to your existing system, but I'd wait until somebody points out any flaws in this, if there are any.
If you mess up, you should just have to reformat your new drive. That's probably not much of a problem. 


My recommendation is the following(assuming sda is your new disk, and assuming you plan on swapping the new for the old in your machine):

Use a LiveCD(I recommend GParted live, Ubuntu's CD works well, too) to partition your new hard drive in the manner you want.
Now, tar up your old Ubuntu installation. In Ubuntu, cd to / and then do something like
```
tar cvfj system.tar.bz2 / --exlude={use the exclude option to ignore proc,dev,sys}
```Copy this new file to a usb stick or something similar.  
Install Windows on the new drive, whereever you want it to go.

Boot into a livecd again. Mount your new Ubuntu partitions(replacing sdaX with appropriate)
```
mkdir /mnt/ubuntu
mount /dev/sda3 /mnt/ubuntu
mkdir /mnt/ubuntu/boot
mount /dev/sda1 /mnt/ubuntu/boot
mkdir /mnt/ubuntu/var
mount /dev/sda4 /mnt/ubuntu/var
swapon /dev/sda2
```and then open your tarred image in /mnt/ubuntu
```
cd /mnt/ubuntu
tar xfvj system.tar.bz2
```mount proc,dev,sys
```
mount -t proc none /mnt/ubuntu/proc
mount -R /dev /mnt/ubuntu/dev
mount -R /sys /mnt/ubuntu/sys
```and now you can chroot into your Ubuntu installation on the new disk
```
chroot /mnt/ubuntu /bin/bash
source /etc/profile
```Now, you can sort out your bootloader. You'll probably have to do something like
```
os-prober
grub-mkconfig
grub-install --no-floppy /dev/sda
```

---

### Post by mips on 2012-09-09
> **franklin_m said:**
> 
As for doing a clean install, I'm ok with that, but don't want to lose my data etc. from ubuntu.


Simplest way to be safe is to remove/unplug your existing 160GB HDD. Make sure AHCI is enabled in your BIOS. Install the 256GB SSD and install away!

Once your installation is complete shutdown, connect old drive, power up & copy whatever you want over to the new install.

EDIT: Check if there is a newer firmware update available for Make/Model SSD from the manufacturers site before installing, this could be important!!

---

### Post by oldfred on 2012-09-09
You want to primarily backup /home, any manually edited files from /etc,  and a list of installed applications. If both drives are connected you can use rsync to copy. But you probably should have been backing up all of this anyway?

Since my plan on a major failure is a clean install, this is my backup:

Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

Since then I found that I can exclude a lot of temporary files:
Files to include or exclude from full system backup. Post #7
[http://ubuntuforums.org/showthread.php?t=1903085](http://ubuntuforums.org/showthread.php?t=1903085)

---

### Post by franklin_m on 2012-09-10
Thanks everyone.

Plan is as follows:

(1) Check/update firmware on new drive
(2) Install new SSD
(3) Install Windows 7 Professional (gift from son)
(4) Install Ubuntu from LiveUSB (clean install for dual boot)
(5) Mount old drive via USB connector cable
(6) Copy /home from old drive to /home on new drive

??? Anything else?

---

### Post by LiamOS on 2012-09-11
> **franklin_m said:**
> Thanks everyone.

Plan is as follows:

(1) Check/update firmware on new drive
(2) Install new SSD
(3) Install Windows 7 Professional (gift from son)
(4) Install Ubuntu from LiveUSB (clean install for dual boot)
(5) Mount old drive via USB connector cable
(6) Copy /home from old drive to /home on new drive

??? Anything else?
Copy over any files from /etc you've edited manually, and possibly some of the files apt-get uses for installation, to save redownloading. I don't know where apt-get stores them, but they should be easy to find.

---

### Post by mastablasta on 2012-09-11
> **franklin_m said:**
>  
What folders should I backup from my existing install to later copy into the new install?
 

use Linux Mint backup tool. it is very simple to use. one button will copy/backup the home file, the other one software selection. the two other buttons are there for restoring the data:
 
[IMG]http://community.linuxmint.com/img/screenshots/mintbackup.png[/IMG]
 
[http://community.linuxmint.com/software/view/mintbackup](http://community.linuxmint.com/software/view/mintbackup)
 
 
an ubuntu PPA is available.: [http://www.webupd8.org/2010/07/install-mintbackup-linux-mint-backup.html](http://www.webupd8.org/2010/07/install-mintbackup-linux-mint-backup.html)
 
dejadup is similar application.

---

### Post by mips on 2012-09-11
> **LiamOS said:**
> Copy over any files from /etc you've edited manually, and possibly some of the files apt-get uses for installation, to save redownloading. I don't know where apt-get stores them, but they should be easy to find.

Good advice ;)

Downloaded packages are stored in /var/cache/apt/archives you will have to copy them back as root and make sure permissions are set as -rw-r--r--

---

### Post by shreepads on 2012-09-11
Err.. Why not use Clonezilla to clone as-is and then GParted to re-size partitions?

---

### Post by franklin_m on 2012-09-12
I downloaded mintbackup, but it doesn't show in my system tools. Says that I have to run from a terminal. Is there a gui somewhere that I'm missing?

Frank

---

### Post by jerome1232 on 2012-09-12
I use USC's (Ubuntu Software Center) sync feature to keep my package selection across installs, If I reinstall I can log into my account and use the sync to reinstall all of my packages again.

Bonus is if you have multiple Ubuntu computers you can compare their package lists. I used to hate USC, however it's starting to grow on me.

---

### Post by kherring7383 on 2012-09-12
There are so many ways to accomplish this and the suggestions that have been posted are helpful. However, have you checked into Clonezilla. I am constantly backing up my Ubuntu drive and moving  everything from one drive to another regardless of the size as long as its the other drive is the same size or larger. With Clonezilla, you can back it up by partition or the whole drive and save the image to another drive or even a net share. Once you have made the image, use clonezilla to copy it to a new drive. As for partitioning, you can use GParted to change partition sizes to suit your needs. Personally I use [PMagic]("http://partedmagic.com/doku.php?id=downloads") from a USB stick that has all the tools you need to manage partitions and resizing your drives.

---

