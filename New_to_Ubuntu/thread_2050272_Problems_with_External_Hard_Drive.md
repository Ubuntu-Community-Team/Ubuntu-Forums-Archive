---
title: "Problems with External Hard Drive"
date: 2012-08-30
forum: New to Ubuntu
---

### Post by emshen on 2012-08-30
Hello All,
I'm brand new to Linux, so please bear with me.  I'm having issues with my WD My Book Essential.  It seems I've been locked out with some type of Password Lock that I never set.  According to WD the only way to recover all my files is to Format the drive, then pay someone to perform a data recovery.  I just got the drive and really do not want to invest anymore money.  I was hoping I could recover my files using Ubuntu (command line).  I'll post some commands below that I think may help.  Any suggestions are welcomed, please keep in mind I am new to Linux so you may have to 'dumb' down the responses.
Thanks in advance

***It's listed here in the blkid******
ubuntu:~$ blkid -po udev /dev/sr2
ID_FS_LABEL=WD_Unlocker
ID_FS_LABEL_ENC=WD\x20Unlocker
ID_FS_TYPE=udf
ID_FS_USAGE=filesystem


***Doesn't appear in fdisk*****
ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00051651

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   155203583    77600768   83  Linux
/dev/sda2       155205630   156248063      521217    5  Extended
/dev/sda5       155205632   156248063      521216   82  Linux swap / Solaris


***Does see it here****
ubuntu:~$ sudo lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 1058:1140 Western Digital Technologies, Inc.


***Not listed here either***
ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c43f12d7-a188-4c67-bd9c-8a4eae0f529d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=53c3ab83-4940-4056-bc4e-5876e29ba058 none            swap    sw

---

### Post by Mark Phelps on 2012-08-30
Sorry, but I think you're totally out of luck, here.

From what I read, with recent WD drive, the screen you see only allows you to unlock the drive or set a password.  If it is prompting you for a password, and you don't know that, there is no way around it.

I have seen threads about removing the VCD (which is what does the prompting) -- but the same threads claim the drive is encrypted in HARDWARE, meaning, the once you remove the VCD, there would be no way to get to the existing data.

If these threads are true, then you also would NOT be able to use data recovery software to get access to your files, because that can not read encrypted drives.

---

### Post by coldraven on 2012-08-30
I have never tried this but can the OP use a bruteforce password cracker on it?
The chances are that the password is a simple one and might be found quickly.

---

### Post by Hadaka on 2012-08-30
Hi, this may be a way to recover some data.


How to rescue a CD or DVD, HDD, flash drive or photos:  	Code:
 	 ddrescue -b 2048 -d -e 20 -r 300 -v /dev/hdc /home/sam/dvd.iso log.txt 
 If **/home/sam/dvd.iso** won't mount, carve it:  	Code:
 	foremost -t all -k 256 -v -b 2048 -i ~/dvd.iso -o ~/dvd/ 
 Your files will be in directory: **/home/sam/dvd**.

---

### Post by OmegaShadowwraith on 2012-08-30
Basically from what i have read about WD My Book Essential Hard Drives the only way you can use the drive again is if you format it. :(

How ever i suggest looking up [http://community.wdc.com](http://community.wdc.com) which is the official Western Digital Community Forum.  Perhaps if you posted your query there you may find a solution or workaround, that i may have missed or have been posted more recently.

Regards. 

OmegaShadowwraith

---

### Post by Mark Phelps on 2012-08-30
> **coldraven said:**
> I have never tried this but can the OP use a bruteforce password cracker on it?
The chances are that the password is a simple one and might be found quickly.

The unpopular truth about these brute force password crackers is that, except for something absurdly simple like "abc" or "123", they're a waste of time.

The problem isn't how fast they can generate passwords.  With a modern PC, you could conceivable generate hundreds or thousands of passwords a minute!

The problem -- the thing that all these crackers make a point of NOT mentioning -- is the rate at which you can CHECK the password.  It does you no good to generate 1000 passwords in 5 minutes, if the only way to check each one is to try it -- and that takes 15 seconds to do.  That then throttles your password generation to FOUR per minute, not thousands.

And, the other thing they fail to mention, is that in many password-protected devices, you are given only so many attempts and the device then locks itself against further tries.

From what I've read, the WD code does this after five attempts.

That doesn't leave much hope for actually cracking the password -- which is the whole idea of encryption in the first place!

---

### Post by Mark Phelps on 2012-08-30
> **OmegaShadowwraith said:**
> Basically from what i have read about WD My Book Essential Hard Drives the only way you can use the drive again is if you format it. :(

How ever i suggest looking up [http://community.wdc.com](http://community.wdc.com) which is the official Western Digital Community Forum.  Perhaps if you posted your query there you may find a solution or workaround, that i may have missed or have been posted more recently.

Regards. 

OmegaShadowwraith

Excellent idea -- except I already went there (before writing my comments) and they said what had already been said -- there is no way to get around the password.  If you have forgotten the password, the interface will only allow you to reformat the "drive" -- which basically, wipes out all the data.

---

### Post by Mark Phelps on 2012-08-30
> **Hadaka said:**
> Hi, this may be a way to recover some data.


How to rescue a CD or DVD, HDD, flash drive or photos:  	Code:
 	 ddrescue -b 2048 -d -e 20 -r 300 -v /dev/hdc /home/sam/dvd.iso log.txt 
 If **/home/sam/dvd.iso** won't mount, carve it:  	Code:
 	foremost -t all -k 256 -v -b 2048 -i ~/dvd.iso -o ~/dvd/ 
 Your files will be in directory: **/home/sam/dvd**.

Except ... according to WD, the drive is HARDWARE encrypted -- which you can not bypass using software, otherwise, what would be the point of hardware encryption?

---

### Post by emshen on 2012-08-30
Thanks for all the feedback, much appreciated.  I'll review your suggestions when I have an opportunity and post results.

---

### Post by emshen on 2012-09-18
Sorry for the delay.  Just to wrap up this thread, the data is hardware encrypted on the hard drive.  It's a common problem with these devices that WD takes no responsibility.  I decided to wipe out my data and start over.
 
Thanks

---

