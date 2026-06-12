---
title: "Strange NTFS Issues"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by jmrother on 2008-08-28
Hey everyone.. at the risk of sounding like a complete n00b, I'm having trouble mounting my internal NTFS drives.  Going to Applications -> System Tools -> NTFS Configuration Tool does not list any drives.

Going to the terminal to mount them yields the following:

me@computer:/dev$ sudo mount /dev/sdc /media/windows -t ntfs -o nls=utf8,umask=0222
NTFS signature is missing.
Failed to mount '/dev/sdc1': Invalid argument
The device '/dev/sdc1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

Any ideas?  I must be missing something small.  Thanks!

---

### Post by nicedude on 2008-08-28
In a terminal do the following install command and then launch the program called pysdm that I recommend you install.


COMMAND TO INSTALL PROGRAM YOU NEED
sudo apt-get install pysdm

COMMAND TO LAUNCH THE PROGRAM
sudo pysdm


now look at the different disks and select one you want to mount and click mount and it can do it for you automatically.

Hope this gets it all working :-)

---

### Post by jmrother on 2008-08-28
Ok.. so I insalled pysdm and got some strange results.  I'm starting to wonder if my hd's somehow got messed up (I certainly hope not!).  It shows me three drives: sda, sdb, sdc.  sdb is my ubuntu drive with appropriate partitions.  sda is supposed to be my windows drive in NTFS and shows one partition (sda1), but shows that it is formatted as swap for some reason.  I'm wondering if it could be because I overwrote my Vista bootloader on this drive with the Ubuntu bootloader on install (a n00b mistake, I know).  To add to the confusion it lists sdc (my data drive), but no partitions.. and gives me no information on the drive when I click on it.

Just to avoid confusion, I'll paste the results of running an fdisk -l
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9730    78148608    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x630d5261

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       18705   150247881   83  Linux
/dev/sdb2           18706       19457     6040440    5  Extended
/dev/sdb5           18706       19457     6040408+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xde6ec0e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      969018   488385040+   7  HPFS/NTFS

Thanks for your help!

---

### Post by nicedude on 2008-08-28
As to messing up your Vista MBR that would only cause Vista to not boot but the actual data partition should be accessible via either pysdm or by using a mount command to mount it. Does your Vista still boot up correctly as if it does then the MBR of sdb is handling your grub stuff and sda's MBR would not be being used.


Here is your data disks partition
/dev/sdc1   *           1      969018   488385040+   7  HPFS/NTFS

Nothing seems out of the ordinary in your fdisk output to me and I see both sda & sdc has partitions on them formated in NTFS. And your sdb disk looks ok too as far as I see as it has a Linux partition and then an extended container that houses sda5 which is your linux swap.

I would try messing around with mount command and see if you can't get your data partition to mount. Here is an example of how this can be done although you might want to look up the mount command and learn what you are doing yourself.

sudo mkdir /media/datastorage
sudo mount -t ntfs /dev/sdc1 /media/datastorage 


Running both of those one then the other should mount your sdc drives NTFS partition with a name tag of datastorage

---

### Post by jmrother on 2008-08-28
No, Vista actually doesn't boot, though it is listed in grub... no big loss though... it didn't work well anyway lol.  My main concern is my data drive.  I tried what you mentioned and have been trying to mount it that way and I keep getting errors.  The latest is:

Unexpected clusters per mft record (-127).
Failed to mount '/dev/sdc1': Invalid argument
The device '/dev/sdc1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

Wouldn't be because the drive is large would it?  It's 500GB.  Thanks for your help!

---

### Post by jmrother on 2008-08-28
Crap.. did some poking around.  I got ntfsfix and ran a check on the drive.  The result was pretty straight-forward:

me@computer:~$ sudo ntfsfix /dev/sdc1
Mounting volume... Failed to startup volume: Invalid argument.
FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk.

I ran it on sda1 and got an ok result... it now mounts.

I can't believe my data drive got corrupted though.. could that have happened during my ubuntu install?  I made 100% sure not to leave it alone.

---

### Post by nicedude on 2008-08-28
I doubt that it got corrupted during your Ubuntu install. The 500GB part should not matter either since I use pull out hotswap sata drives with my desktop which are 250GB - 300GB and also a 500GB USB portable and I have never had anything happen like this to any of them, beyond having my USB portable not mount sometimes when it has been improperly unmounted without first choosing to eject it. Even that problem was fixable with a forced mount of the partition with no data loss or corruption. I would also point out that you could try installing testdisk from the repositories and try to see if that can get your data back for you as it is a partition fixing recovery tool.

---

### Post by kansasnoob on 2008-08-28
OK, this will not make your Vista drive bootable but you should be able to read it if you install ntfs-config. You can find it in synaptic or go to terminal and:

```
sudo apt-get install ntfs-config
```

Actually ntfsprogs will even extend write privileges but it's a bit more fiddly.

[http://www.linux-ntfs.org/doku.php](http://www.linux-ntfs.org/doku.php)

---

### Post by kansasnoob on 2008-08-28
Actually you may be able to make that bootable.

The multiple drive thing can get testy and I have too many projects going right now.

---

