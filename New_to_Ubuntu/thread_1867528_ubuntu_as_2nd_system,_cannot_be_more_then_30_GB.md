---
title: "ubuntu as 2nd system, cannot be more then 30 GB?"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by olawola on 2011-10-23
Hi,
I already have windows on my computer, but want to intsall ubuntu. I run ubuntu installer for windows, but when I am bout to choose how much space I want to dedicate to Ubuntu, the max value is 30 GB - but I would like it to be 100 GB? How can I do it?
Best,
Ola

---

### Post by Mark Phelps on 2011-10-23
don't use Wubi, so don't have an answer --but how much free space do you have in your Windows OS partition?  If 100GB uses nearly all of that up, that will present a very real problem in that Windows needs free space to function.

---

### Post by jonnny_j22 on 2011-10-23
> **olawola said:**
> Hi,
I already have windows on my computer, but want to intsall ubuntu. I run ubuntu installer for windows, but when I am bout to choose how much space I want to dedicate to Ubuntu, the max value is 30 GB - but I would like it to be 100 GB? How can I do it?
Best,
Ola
 
 
It's usually best to get your hard drive prepared before you install I find. first things first defragment and back up your hard drive -if you are using vista or windows 7 take the opportunity to create a system image from the backup centre -this will make things much simpler if you stuff something up!
 
Once you are all backed up properly I would recommend configuring your hard drive with Gparted. You can either use a Gpated live CD, or the Ubuntu one - just click 'try' when you boot from it then go to the dash and type 'gp' and start gparted. I wouldn't recommend doing this from the WUBI, as this requires windows to be running and you may get errors.
 
Using gparted - an ideal situation would be for you to find you have two hard drives and that one of them is completly unused (double and even tripple check its COMPLETELY unused) - if this is the case, make a note of the hard drive number - probably /dev/sdb, and run the ubutnu installer using that hard drive.
 
If you don't have this set-up (the most likely case) you need to free up some space. Gparted will tell you how much free space each partitionand HDD has. to free up some space, simply shrink partitions to make a 100GB gap if possible. Remember windows likes to be the first OS on a disk, so shrink from far right to left (0 free space preceeding, 100GB following:))
 
once you have 100GB free space it's really up to you what you do with it, but the best bet is create a new partition and select type-> extended. By creating an extended partition, you can create smaller partitions within it for Ubuntu to use. You will need to create a partition for 'Swap' space (about 2-4 GB is more than enough usually) formatted as swap surprisingly, and a partition for ubuntu (formatted as ext4).
 
Once you have done these, run the Ubuntu installer, and select 'something else' or 'configure partitions manually' and select your ext4 file system, click 'change' and format - ext4, mount point /, and you'll now be ready to go!
 
 
a couple of things to concider -
 
You may want to make a seperate 'boot' partition for your .. well boot files! this should be ~100mb , format as ext4 and mount point /boot
 
a seperate partition for Home - this is like linux My documents - again format ext4 and mount point /home (size is up to you!
 
creating a Data partition - Ubuntu can read windows NTFS files, but windows can't read EXT4, or, well anything really! so concider creating a partition formatted as FAT32 for files you want to share between OS's - photos, music etc!
 
If you are using windows vista or 7, concider setting the bootloader installation location as the same partition as where you are installing ubuntu -or your boot partition if you chose to make one (basically not your windows partition(s) or the default /dev/sda). This way you don't wipe out the windows BCD. If you choose this route, reboot into windows and download and install 'easy bcd' and use this to create a en entry in the boot order for ubuntu. longer, more steps, yes... but if you choose to remove ubuntu, you just have to remove the entry from easybcd, set timeout to 0 and it'll be like it was never there - you don't have to go anywhere near a windows DVD!
 
Hope that helps!

---

### Post by critin on 2011-10-23
[jonnny_j22]("http://ubuntuforums.org/member.php?u=1063312")  -if you are using vista or windows 7 take the opportunity to create a  system image from the backup centre -this will make things much simpler  if you stuff something up!
 
Once you are all backed up properly I would recommend configuring your hard drive with Gparted>>>

jonny, I just read a day or so ago on these forums that if using Windows7, do NOT use gparted.  I would think the windows disk manager would be safer since Windows is the only os atm.  I may be wrong, but I have easeus partition manager that I've used, and it warns that if I'm using windows I shouldn't use easeus-- to use windows disk manager.

? I'm just asking so I'll know.   If a newbie used gparted  would the chance of not messing up something be small, as long as they followed the instructions of course.  I can mess up anything.  lol

---

### Post by critin on 2011-10-23
> **olawola said:**
> Hi,
I already have windows on my computer, but want to intsall ubuntu. I run ubuntu installer for windows, but when I am bout to choose how much space I want to dedicate to Ubuntu, the max value is 30 GB - but I would like it to be 100 GB? How can I do it?
Best,
Ola

Instead of using Wubi, you could simply use the live cd and let it install 'Side by Side'.  It will divide the disk into proper size so Windows and Ubuntu are safe.  Wubi goes INTO windows just like any other windows program.  If it crashes or windows crashes, you've lost both.  

It's your choice of course. ;)

---

### Post by jonnny_j22 on 2011-10-23
Thnks Critin, I wasn't aware of this error!  - I have just checked my Gparted Live CD, it can detect my windows 7 ntfs partition and edit fine (i took 100mb off then put it  back lol!

If this is an issue with some Gparted/hardware I'll add that only use Gparted so long as when you load it up it can read your windows 7 ... if it's black, got a warning flag or says a different amount of free space left to what you know to be true, then use the windows installer to edit it.

---

### Post by satanselbow on 2011-10-23
Have you got a link to the thread advising against using GParted? Could be a humorous read :D 

AFAIK the arguments against using Gparted on NTFS partitions are historic and are no longer relevant. With ANY partition tool you should use extreme caution at every step - double, triple and beyond checking before you commit any changes. 

I would use a specialist linux tool over a crippled windows half effort every time.

If you are resizing you main windows partition be sure to defrag **properly** (ie with a 3rd party tool - not Windows Defrag. Piriform's Defraggler is excellent and free!) before you start moving anything ;)

---

