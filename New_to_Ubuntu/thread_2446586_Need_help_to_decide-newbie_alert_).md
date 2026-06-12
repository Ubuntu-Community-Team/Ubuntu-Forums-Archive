---
title: "Need help to decide-newbie alert :)"
date: 2020-07-03
forum: New to Ubuntu
---

### Post by mariannagr1 on 2020-07-03
Hi everyone,

I have been considering to switch to Linux many years now, main drawback being a game that I have been playing. However, I now have a new laptop, so my previous one is available. Also, I was lazy, but a new motive emerged, another windows drawback that got me active. I will describe the issue and my questions as clearly as possible. Please mind that I am not a tech guru (but not extremely bad at it) and that I have never tried Linux before.

So what happened is that my external HDD became RAW. However, my smart TV still sees everything in it. I suspect my TV is somehow similar to linux in terms of ignoring windows ''dirty'' flags and file system structure. Please correct me if I am wrong.

What I was thinking to do is try access the drive through a linux environment, retrieve my files and move them to a new drive. But, I am not sure if I need to re-format my laptop to linux only or try dual windows/linux setup, or running linux from an external drive. I need some help to get me started. I have been reading a bit about Linux, ounting drives etc but I would appreciate some initial guidance.

Thank you for your time and tolerance.

Update: I am currently running ubuntu from CD, as it seems to be the best option for a newbie to check it out. Trying to find out how to read my external drive and save my files.

---

### Post by Autodave on 2020-07-03
While booted to the CD, can you read the files on the HDD?  Just boot the machine with your CD and then connect the drive.  You should then see an icon representing the HDD.  If it doesn't mount by itself, double-click on the icon and see what happens.

---

### Post by mariannagr1 on 2020-07-03
I tried ''mount and open'' Results in ''unable to access, unknown error''. 

It shows up in disks, as 2 NTFS partitions. 

How can I repair filesystem? Please guide me, I dont want to destroy the drive :(

---

### Post by TheFu on 2020-07-03
**To fix Windows drive problems, use Windows.** Don't use Linux. That is asking for corruption.

Often it is possible to use Linux to mount NTFS storage as **read-only** just to copy off files.  But if Windows has left the file system "open" and corrupted, there isn't anything that Linux can really do.

For data recovery, [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

As for what and how you could/should do on your new system with Linux, there are multiple choices as you've seen. Each has pros/cons.  Since 2006 (or so), I've selected running the OS in a virtual machine almost always.  Most computers are fast enough and have more than enough RAM to use a VM for on or multiple OSes.  For years, I ran 15 VMs on a Core2 Duo E6600 with 8GB of RAM, including my Windows and Linux desktops. Those VMs have been migrated to newer hardware a few times.  Core2 Duo 8400, Core i5-750, Core i7-920, and the last few years on a Ryzen 2600.  Until last month, the Core i5/i7 computers had 16G of RAM.

[LIST]
[*]Dual boot has the negative that MSFT updates seem to break Linux booting about once a year.
[*]Running from a CD or USB-Flash device tends to be noticeably slower than a proper install.
[*]Using virtual machines means that only virtual hardware is seen by the OS. That limitation isn't usually a problem for "productivity" tools or servers, but if you plan to edit videos or run FPS games, the virtual GPU just isn't up to the task. For 10 yr old games, the v-GPU probably is just fine. Just depends on what you want/need.  For experts and computers with multiple GPUs and some other specific hardware required, it is possible to pass one of the GPUs into the virtual machine for exclusive use to get 100% of that GPUs capability. In general, laptops cannot do this and low-end computers with GPUs that aren't at least $250 won't work.
[/LIST]
If you don't game or do video editing, then a virtual machine solution is almost always fine and fast.  Only the GPU becomes slower, not disk, not CPU, not RAM, not the networking.  All of those will run at 90-95% the speed of the same machine without virtualization.
Plus, virtual machines provide all sorts of abstraction and safety from failures, backups, and makes moving to different hardware pretty trivial.  I moved a Windows VM from a Core i5 to the Ryzen a few months ago, just by moving a few times and changing 2 lines in the XML configuration file. That was it. The machine runs much faster. Windows never saw any hardware changes.

---

### Post by ActionParsnip on 2020-07-03
You could wipe the drive, recreate the partition and restore the data from your backups. You do have backups, right?

---

### Post by mariannagr1 on 2020-07-03
TheFu, thank you for your detailed reply. I fell in love with Ubuntu so I installed it fully to explore its possibilities. 
ActionParsnip, if I had a backup I would bin the drive. It is a drive mostly containing movies and old files that I don't really need. However, I have some files in it that did not have time to backup, as the error occurred a few days after switching to a new laptop. Murphy's law...
Luckily, drive still plays in my TV as mentioned in first post so I doubt there is a huge corruption involved. I am currently trying to create an image of it so I stop reproducing bad sectors, as I found a few.
I was able to see the files with TestDisc in Windows but not to recover them. 
I am back to trying with windows, so will post under that forum section if needed. 
Since my TV was reading the files I was hoping linux will. After image is done I will try access that.

---

### Post by mastablasta on 2020-07-03
sometimes it sees the files but you can't actually recover them. while bits and pieces may be missing in media files, they might still play. but that might not work for other files. i had similar issue with backup disk. i could see it but could not recover all files from it. windows didn't show anything, linux could at leats read and copy the files to new drive.

---

### Post by mariannagr1 on 2020-07-03
Alright. Now tying to mount the drive. I try and fail, any tips? The partition I need is /dev/sdc1

---

### Post by kurt18947 on 2020-07-03
I would heed TheFu's advice to try to recover your hard drive with Windows tools if possible. I've used a live USB to recover a drive that a Windows Update borked but the drive mounted right up in the Live session and I was able to copy files to a Flash Drive. That is not happening for you. Given that the file system on your subject drive has issues, trying to read and write them with Ubuntu may make those issues worse. If Windows tools absolutely will not read and copy those files, you have nothing to lose trying Ubuntu.

You mentioned Testdisk. Is that from GCSecurity? Testdisk is available to Linux as well. Photorec which seems to be part of Testdisk has a pretty good reputation for recovering files but any file names or structures will be toast I think. Disclaimer: I'm a hobbyist, nobody's idea of an expert.

---

### Post by mariannagr1 on 2020-07-03
sudo   fdisk  -l
sudo   mkdir   /media/external
sudo   mount   -t   ntfs-3g   /dev/sdc1   /media/external

I get the message ''Failed to read ntfs bitmap...blah blah'' and getting prompted to use chkdsk /f in windows. Is there a workaround here?

Otherwise, Photorec is probably my last hope...

---

### Post by oldfred on 2020-07-03
RAW is what Windows reports when drive is not formatted.
But it really sees that from PBR - partition boot sector, not from partition table.

Running chkdsk from Windows may repair it, you may have to run more than once.
Or other Windows repairs, you do not want to reformat it, just update PBR.

With NTFS there is also a backup PBR. You can use testdisk or many Windows tools to see if backup is correct & then can be restored. But still may need chkdsk.

PBR - partition boot sector NTFS must be Windows
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
[http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486](http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486)
As described, testdisk has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS, otherwise Windows repairs will not work 
Instructions - see section on NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]

Testdisks create of a new PBR, used to be and may still be the XP type. But then running chkdsk from a newer Windows usually repairs it.
Still usually better to use Windows tools as they understand all the details and may work better with the newer versions of Windows.

---

### Post by mariannagr1 on 2020-07-05
Update:

Since ddrescue was too complicated for me, I managed to create an image using disks. around 1300 bad sectors were found and 0.5% of data were lost-replaced with zeros. That is kinda good, right?

Now in the process of trying to extract the files from this image - unable to do directly as it is RAW. 

Apologies for my incompetence, very new to this.

---

### Post by oldfred on 2020-07-05
1300 bad sectors is not good.

In Disks and upper right corner icon is Smart Status. It can run a lot of tests and show details on drive. Some know about the details, but all I really know is whether it says drive is good or bad.

---

### Post by sudodus on 2020-07-05
If you spend some time and effort to learn how to use ddrescue, you will recover at least 50% of those 1300 bad sectors, maybe as much as 90% of the bad sectors. I write this because of my own experience with this tool.

Read

```

info ddrescue

```

very carefully. There are **examples in the tutorial section of 'info ddrescue'** that describe how to set up a recovery session with input file, output file and log file. I think Example 1 could be good in your case (with modifications for the actual drive letters and partition numbers in your case).

```

Example 1: Fully automatic rescue of a whole disc with two ext2
partitions in /dev/sda to /dev/sdb.
Note: you don't need to partition /dev/sdb beforehand, but if the
partition table on /dev/sda is damaged, you'll need to recreate it
somehow on /dev/sdb.

     ddrescue -f -r3 /dev/sda /dev/sdb mapfile
     fdisk /dev/sdb
     e2fsck -v -f /dev/sdb1
     e2fsck -v -f /dev/sdb2

```

---

### Post by mariannagr1 on 2020-07-06
Thank you all for trying to help! Surely learned a bit in the process.

I managed to recover all my files. In case someone has a similar issue what I did, is:
1. Created a disk image with Disks. For me it was the fastest/easiest way, since doing so under windows would take months :) For 1Tb drive with 3,000 bad sectors, took 24 hours.
2. Used windows software to recover the files from the image, as there are many programs that are more user-friendly for a newbie like myself. Scanning the image file took around 6 hours (much faster than trying to scan the original hard disk, plus safer). And add some time to copy the recovered files to new drive. Done.

As per my other question, as to where to start with Ubuntu, I am currently exploring Ubuntu with dual boot. Really appreciate all the suggestions and the effort to help me.

---

### Post by mastablasta on 2020-07-06
wow, that's great. thank for the update and possible solution. this might come in handy for someone. many here use Windows and Linux or we have NTFS drives as we share the files with windows machines.

---

