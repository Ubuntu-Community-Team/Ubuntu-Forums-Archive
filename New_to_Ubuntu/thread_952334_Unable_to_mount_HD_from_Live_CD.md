---
title: "Unable to mount HD from Live CD"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by quarkbot24 on 2008-10-19
[SIZE="3"][SIZE="4"][SIZE="3"][SIZE="2"]PLEASE HELP! -- I'm an extreme newbie -- I have a friend with a PC (I'm a Mac dude, myself) and she probably has some sort of malware that has her PC unable to boot up (in any mode). She's interested in Ubuntu, willing to completely reformat her hard drive, BUT ONLY AFTER she can recover a number of important files (jpegs & docs), and save to a thumb drive.

She bought the CPU from a local Oklahoma City, OK computer store, but received NO CDs... pre-installed software only, including the OS (Win. XP pro, I think).

I downloaded the Ubuntu Live CD iso, and it seems to run on her PC...  BUT, we can't seem to mount the Hard Drive to look for her pictures and docs in order to save them to Thumb Drive. I found some instructions on the web dealing with Terminal, but no luck.

Any advice???

THANKS!
KW[/SIZE][/SIZE][/SIZE][/SIZE]

---

### Post by wolfen69 on 2008-10-19
try the [PuppyLinux live CD]("http://www.puppylinux.org/home"). it will mount any drive and recovery is easy. plus it is only like 80MB. and, it's a good cd to have for your "toolbox".

---

### Post by Dark006 on 2008-10-19
Try this: 
```
sudo /bin/bash

Create Mount Point for HDD: mkdir /media/disk

Mount NTFS HDD: mount -t ntfs-3g /dev/<device> /media/disk -o force
```

where /dev/<device> is your hard drive, you can find the correct one by typing 
```
fdisk -l
```
Mine is /dev/sda1 for example.

---

### Post by quarkbot24 on 2008-10-21
THANKS Wolfen69!
The PuppyLinux worked.
I off-loaded the important files and have since installed Ubuntu.
My friend is truly happy and thankful.

KW - quarkbot24

---

