---
title: "Install from CD problem"
date: 2013-02-22
forum: New to Ubuntu
---

### Post by rubyondine on 2013-02-22
So it's getting stuck on "Please remove installation media and close the tray (if any) then press ENTER:"

Enter doesn't do anything. I restarted with the power button and there is no ubuntu installed. I searched for similar problem topics and I think I have too many partitions or something? I'm a complete noob though so I'm not sure what to do from there.

I had installed ubuntu twice before (12.04 but from a windows installer) and uninstalled (just being indecisive and dumb), so maybe that has something to do with it? But I have no idea where to go from here though.

This is what I get from sudo parted /dev/sda unit s print 

Model: ATA ST9750420AS (scsi)
Disk /dev/sda: 1465149168s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

No. _Start________End___________Size__________Type____File system__Flags
 1.......2048s..............409599s..............407552s............primary..ntfs..................boot
 2.......409600s.........1411893247s.....1411483648s..primary...ntfs
 3......1411893248s..1456826367s....44933120s.......primary...ntfs
 4......1456826368s..1465145343s....8318976s.........primary...fat32................lba

---

### Post by fdrake on 2013-02-22
> **rubyondine said:**
> So it's getting stuck on "Please remove installation media and close the tray (if any) then press ENTER:"

Enter doesn't do anything. I restarted with the power button and there is no ubuntu installed. I searched for similar problem topics and I think I have too many partitions or something? I'm a complete noob though so I'm not sure what to do from there.

I had installed ubuntu twice before (12.04 but from a windows installer) and uninstalled, so maybe that has something to do with it? But I have no idea where to go from here though.

This is what I get from sudo parted /dev/sda unit s print 

Model: ATA ST9750420AS (scsi)
Disk /dev/sda: 1465149168s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

No.   Start                         End                              Size                   Type             File system    Flags
 1           2048s                       409599s                  407552s                primary    ntfs                         boot
 2           409600s                 1411893247s    1411483648s  primary    ntfs
 3           1411893248s    1456826367s    44933120s          primary    ntfs
 4      1456826368s    1465145343s    8318976s         primary    fat32                      lba

you have already 4 primary partitions. you cannot dual boot with ubuntu unless you delete one of the partitions and create a extended one with logical volumes.
check wiki and [http://www.werockyourweb.com/primary-vs-extended-logical-partition](http://www.werockyourweb.com/primary-vs-extended-logical-partition)

---

### Post by joco1500 on 2013-02-22
first off, use a usb

then you can use it mutual times.

just re download it to the usb

---

### Post by rubyondine on 2013-02-22
> **fdrake said:**
> you have already 4 primary partitions. you cannot dual boot with ubuntu unless you delete one of the partitions and create a extended one with logical volumes.
check wiki and [http://www.werockyourweb.com/primary-vs-extended-logical-partition](http://www.werockyourweb.com/primary-vs-extended-logical-partition)

How do I know which one to delete?

---

### Post by fdrake on 2013-02-22
you can do using windows. ussually 1 partition is for the windows system, 1 is fo recovery . the other 2 i don't know what they are used for . you have to check in "My Computer". You may need admin priviledges to se the different Unit Drives. You can reformat the partition usinf windows too.
[http://technet.microsoft.com/en-us/magazine/gg309170.aspx](http://technet.microsoft.com/en-us/magazine/gg309170.aspx)

be carefull of what you are doing you may reformat the wrong partition.

---

### Post by varunendra on 2013-02-23
Welcome to the forums rubyondine! :)

Instead of manually formatting a terminal output, just put it in a 'Code' box using code tags (follow the 'Code tags example' link in my signature to see how). It will preserve the original formatting and make the post more readable.

Onto your question -
> **rubyondine said:**
> 
Model: ATA ST9750420AS (scsi)
Disk /dev/sda: 1465149168s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

No. _Start________End___________Size__________Type____File system__Flags
 1.......2048s..............409599s..............**[COLOR="Red"]407552s[/COLOR]**............primary..ntfs..................boot
 2.......409600s.........1411893247s.....**[COLOR="Red"]1411483648s[/COLOR]**..primary...ntfs
 3......1411893248s..1456826367s....**44933120s**.......primary...ntfs
 4......1456826368s..1465145343s....**[COLOR="Navy"]8318976s[/COLOR]**.........primary...fat32................lba
The first one, 199 MB in size,  in the above output is your Boot partition - don't touch that!

The second one, approx 673 GiB, is obviously your Windows partition - may be shrinked from within Windows.

The third one, approx. 21 GiB, is *perhaps* your recovery partition - don't touch that one too, if it really is!

The fourth one, approx. 4 GiB Fat32 partition maybe system utility partition that contains system utilities provided by the laptop manufacturer.

I'm a little confused between partitions 3 and 4. The one with system utilities should be visible from Windows. So you can confirm which ones are visible from within Windows, and what are their contents (roughly). If not sure, just post a screen shot of your Windows disk manager showing all the partitions.

Once the utility partition is identified, it can be safely deleted.

But before doing anything destructive, I STRONGLY recommend to create a System Recovery CD + System Backup DVDs from Control Panel > System Backup & Recovery option (or something similar) in Windows.

Afterwards, you can do the following (from within windows)-
[LIST=1]
[*]Defragment the Windows partition.
[*]Using the Windows disk management tool, Shrink the Windows partition to gain at least 26 GiB (or more) unused space for Ubuntu.
[*]Leave the space unused and reboot with Ubuntu live cd/usb.
[/LIST]

Once in Ubuntu with the desired unused disk space, do the following -
[LIST=1]
[*]Run gparted
[*]In the just created unused space, create an 'Extended Partition'
[*]Within the extended partition, create an EXT4 partition using all but 1 or 2 GiB space (for swap)
[*]In the remaining 1 or 2 GiB space, create a swap partition.
[*]Close Gparted.
[*]Start installation, and at the installation type selection stage, select "Something Else" option.
[*]In the next, partition selection menu, select the just created EXT4 partition and make it a mount point for '/'. There is no need to format it here.
[*]Proceed to installation and ignore the warning about formatting the partition (you have already done it in Gparted).
[*]Complete the setup and reboot - from hard disk this time.
[/LIST]

Hopefully, everything would go smoothly this time. If yes - Congratulations!! If not, post back the error.

In any case, post back how it goes, and do not forget to create System Recovery CD / Backup DVDs.

Good Luck!

---

### Post by Mark Phelps on 2013-02-23
You didn't say, but with this layout, my guess is that the last partition may be HP_TOOLS.  IF that is the case, read through the material below -- perhaps it will help:

Since you already have four partitions, that is the maximum allowed. Simply removing HP_TOOLS is not the solution -- as it is too small to be of any use.

So first, copy all the files and folders inside the HP_TOOLS partition into your Win7 OS partition.  

Second, open up the Win 7 Disk Management tool.  NOW, you can remove the HP_TOOLS partition.

Third, shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

Fourth, you will need a way, in the future, to restore Win7 to its present state -- and you can do that without using the Recovery partition.  Download and install the free version of Macrium Reflect.  Hook up an external drive, and use MR to image off the Win7 OS and its boot partition to that drive.  Then, use the MR option to create and burn a Linux Boot CD.

Now, using that CD, you have the ability to restore your current Win7 setup from that backup. 

Fifth, you can now go back into the Win7 Disk Management tool and remove the Recovery partition. Do not format the free space, leave it as is.

Finally, BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by rubyondine on 2013-02-23
Okay thank you all for the help!

So I looked in My Computer, and  yes it turns out the 673 GB is my Windows partition, ~21 GB is my  Recovery, and the ~4 GB is HP Tools.

Everything is backed up so I'm fine with that.

So since one is HP Tools, I followed what Mark Phelps had to say, and it worked out perfectly. 

Thank you all :)

---

### Post by fdrake on 2013-02-23
> **rubyondine said:**
> Okay thank you all for the help!

So I looked in My Computer, and  yes it turns out the 673 GB is my Windows partition, ~21 GB is my  Recovery, and the ~4 GB is HP Tools.

Everything is backed up so I'm fine with that.

So since one is HP Tools, I followed what Mark Phelps had to say, and it worked out perfectly. 

Thank you all :)
good we are glad it worked out for you. Now mark the thread as "Solved" please. Thank you.

---

