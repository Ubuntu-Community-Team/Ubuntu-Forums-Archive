---
title: "Shortcut to a folder on a FAT32 or FAT data partition?"
date: 2013-06-28
forum: New to Ubuntu
---

### Post by CrankyOldMan on 2013-06-28
My laptop boots Windows 2K and Ubuntu.   I've upgraded from 9.XX to 12.04LTS over the past 5 or more years.  Despite this, I consider myself an inexperienced Linux user.  So please keep that in mind, should you decide to answer my questions.  

I have several FAT32 partitions, FAT thumbdrives, and a FAT32 external drives which I use for data storage and data backup.  I used to have shortcuts to folders on these drives, on my Linux desktop.  I had no more problem creating a shortcut in Linux than I did creating s shortcut in Windows.

Sometime after a Linux upgrade, I lost the shortcuts, and the ability to re-create them.    I can find and mount the partitions, and read /edit folders and files on them.  But when I try to "Make Link" for a folder, I get a popup saying "The target doesn't support symbolic links".

When I searched for a solution to this online, people were saying you CAN'T make a "symbolic link" to a FAT32 partition.  But I KNOW I had desktop shortcuts to those partitions in the past.   Something has changed.

Thank you for your time.

---

### Post by oldfred on 2013-06-28
With 9.04 I still used FAT32 for my shared data partition, but as part of upgrading to 64 bit, ext4, and new drive I converted my data from FAT32 to NTFS. I found I was losing some large files over 4GB as FAT32 does not support large files and does not have a journal so chkdsk can take longer or not repair a damaged partition.

I have not heard that you could not link to FAT32 and would not think format matters.

This is all NTFS as FAT32 is not really recommended anymore. But process is the same.
 Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Mount NTFS partition:
[http://ubuntuforums.org/showthread.php?t=1927504](http://ubuntuforums.org/showthread.php?t=1927504)

      
 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

---

### Post by JKyleOKC on 2013-06-28
> **CrankyOldMan said:**
> Sometime after a Linux upgrade, I lost the shortcuts, and the ability to re-create them.    I can find and mount the partitions, and read /edit folders and files on them.  But when I try to "Make Link" for a folder, I get a popup saying "The target doesn't support symbolic links".

When I searched for a solution to this online, people were saying you CAN'T make a "symbolic link" to a FAT32 partition.  But I KNOW I had desktop shortcuts to those partitions in the past.   Something has changed.I'm using the current LTS release, 12.04, but it's Xubuntu rather than Ubuntu. However it uses the same kernel, just a diffent desktop environment. And I've had no trouble at all creating desktop shortcuts to FAT32 folders elsewhere on my LAN.

I do normally use the command line to create the links, however, rather than any of the desktop tools. It's possible that when Ubuntu introduced the Unity desktop they changed some of the utilities there. With Xubuntu, there's an entry on the right-click menu that says "Send to" and a submenu that includes "Desktop (create link)" which still works just fine! I've used it a few times...

But hmmm.....
I just checked my desktop links, and in every case they link to mountpoints on my local drive rather than direct to the remote folder. The remote folder is auto-mounted to the mountpoint, using the "autofs" utility. Thus my experience may not be applicable to your situation, but might offer a possible solution...

---

### Post by CrankyOldMan on 2013-06-29
Thank you Oldfred.  There is a lot to digest in the links you referenced.. This might take a while....

I have much more experience with Windows.  I stuck with FAT32 because it always seemed much faster on slower hardware.  But if  you think a conversion will help me setup the shortcuts, I might consider the change.   Is there a way to convert the FAT32 partitions to NTFS, without destroying the data on them?    As I recall, Windows used to have a "convert" tool.  But I'm afraid that will break the "mount points" the Ubuntu installer created.  If creating new mount points requires  something other than the GUI, I'm likely to screw it up.

---

### Post by cool110 on 2013-06-29
You can make symlinks TO a FAT drive but NOT FROM. The right click menu tries to create the link in the same directory which won't work. Symlinks can be created with this command ```
ln -s /path/to/original/file ~/Desktop/link
```

---

### Post by CrankyOldMan on 2013-06-29
Jim,
Thank you for your reply also.  Mabybe I don't understand Linux terminology, particularly, "mount point".    I've been accessing my data partitions by the following procedure.... I click on "home folder" in the Unity launcher.  Then I select "Go"  and "Computer" from the pulldown menu.  At that point I can see my available (mounted?) drives.  I can double click any of the listed partitions and open the folders within.  When I right click on a particular folder, and select "Send To", my options include "Bluetooth", "CD/DVD Creator", "Instant Message", "Email", and "Removable Disks and Shares".  No option to place a shortcut on the desktop. 

I selected a folder on my Linux partition (which I recall was formatted XT3) and right clicked.  Again, no option to sent a shortcut to the desktop.

Is the Autofs utility a GUI tool?

---

### Post by oldfred on 2013-06-29
You would have to change mounting if you reformat. Not sure if there are third party Windows tools to convert from FAT to NTFS, but if data is at all important, you must have backups. Hard drives do fail, users make errors and many other things happen to data.

To be able to link to your folders in the FAT32 partition, you need to permanent mount it. You have to create a mount point, add an entry to fstab and then create the link.

Some to the gui tools to create entries in fstab have not been maintained and should not be used. But you really only need to copy several commands and edit with your UUID & whatever name you want for mount point.

Shows both NTFS & FAT32.
 [http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

These were my old FAT32 fstab entries, old one by device and newer one by UUID.

 # before uuid  /dev/sda4 /home/fred/share vfat user,auto,fmask=0113,dmask=0002 0 0
UUID=46CD-C9B2 /home/fred/share vfat user,auto,fmask=0113,dmask=0002 0 0

---

### Post by JKyleOKC on 2013-06-29
> **CrankyOldMan said:**
> Jim,
Thank you for your reply also.  Mabybe I don't understand Linux terminology, particularly, "mount point".    I've been accessing my data partitions by the following procedure.... I click on "home folder" in the Unity launcher.  Then I select "Go"  and "Computer" from the pulldown menu.  At that point I can see my available (mounted?) drives.  I can double click any of the listed partitions and open the folders within.  When I right click on a particular folder, and select "Send To", my options include "Bluetooth", "CD/DVD Creator", "Instant Message", "Email", and "Removable Disks and Shares".  No option to place a shortcut on the desktop. 

I selected a folder on my Linux partition (which I recall was formatted XT3) and right clicked.  Again, no option to sent a shortcut to the desktop.

Is the Autofs utility a GUI tool?No, "autofs" is a system-level tool that, once set up, runs automatically in the background each time you power up. It may be what's doing the work when you double-click on a partition from Unity's file manager program.

Unless they changed a lot more for Unity than I believe they did, you can probably open a partition as you normally do, then open another "Go" window without closing the one you just opened, and in the new window browse to "File System" and there select the "media" folder. It should contain a sub-folder that holds the partition you opened in the original Go window. The /media/whatever (where "whatever" is probably the same name as the selected partition) folder is the "mount point" that the file manager created automatically to make things work.

Setting up the "autofs" utility is probably a lot more complicated than you'll want to deal with at this stage of your Linux experience. I've still not worked out all the details in my setup despite more than 40 years of dealing with computer systems right down at the most detailed level!

Your best bet is to follow OldFred's advice and guidance. He's the one who led me through a most complicated dual-boot installation last year. The "psychocat" tutorials he linked to are quite useful; they attempt to avoid excessive use of our jargon such as "mount point" or "symbolic link" and when such cannot be avoided, try to explain them clearly.

---

### Post by vanadium on 2013-06-29
Symbolic links indeed can only be created on file systems that support them. Thus, you cannot create symbolic links on a FAT or an ntfs formatted partition. You can, however, link to FAT or ntfs formatted partitions from an ext4 formatted partition (or any other filesystem that supports Unix links).

There remains a "graphical" way other than the right-click menu to create a link to a FAT partition. It involves dragging the target (a file/folder on a FAT volume) to the place where the link is to be created while holding the Ctrl+Alt keys pressed.

---

### Post by CrankyOldMan on 2013-07-08
Sorry if it seemed like I was ignoring everyone over the past two weeks.  Heat wave here had me in a stupor.  No A/C.  Last thing I have wanted was to put a hot notebook on my lap.

Lots of stuff to digest here, some of it over my head........  I think I will start with the psychocats tutorial.  Thanks all.

---

