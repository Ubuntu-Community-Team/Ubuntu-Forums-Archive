---
title: "Repairing a corrupt USB drive"
date: 2011-12-28
forum: New to Ubuntu
---

### Post by Neon_Knight on 2011-12-28
Hi guys, here's my problem:

Foolishly, while accessing files on a USB drive on my netbook, I managed to accidentally pull the drive out of the USB socket in the middle of a procedure, and since then it's become totally un-usable.   It's not mountable, it appears in gparted as an unallocated drive.  Attempts to add a partition to the drive gives "No partition table found",  and on trying to create a partition table, I get (in the terminal) "/dev/sdb: unrecognised disk label".

It's clear that something horrible has happened to the partition table, and that it's totally corrupt and broken, but surely this should be fixable?

I'm not particularly worried about my data - it's surely gone by now, and there's nothing on there that I particularly need.  I just need to reformat the thing at this point and get it working again.

Oh, and here's the output of fdisk -l  

```

david@david-netbook:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc12b5115

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         784     6297448+  12  Compaq diagnostics
/dev/sda2   *         785       10059    74495096    7  HPFS/NTFS
/dev/sda3           10059       19177    73242187+  83  Linux
/dev/sda4           19178       19457     2249100    5  Extended
/dev/sda5           19178       19457     2249068+  82  Linux swap / Solaris

Disk /dev/sdb: 4009 MB, 4009754624 bytes
124 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x74a3e94c

Disk /dev/sdb doesn't contain a valid partition table

```

Running Ubuntu 10.04 LTS, 32-bit. 

I've seen this problem crop up around in my pre-thread googling, but I've yet to come across a conclusive solution to it.

I guess what I'm really looking for is a program that can just scan my drive and repair my partition table for me. 

Thanks for any help you can give.

---

### Post by searchfgold6789 on 2011-12-28
GParted is the one. Simply delete anything on the drive and start anew by adding a FAT32 partition on the drive. There are plenty of Docs and Manuals - just open GParted and press F1.

---

### Post by BBQdave on 2011-12-28
> **Neon_Knight said:**
> I'm not particularly worried about my data - it's surely gone by now, and there's nothing on there that I particularly need.  I just need to reformat the thing at this point and get it working again.

And just that, reformatting would seem to be the easiest way to go.  An additional question, does pulling the thumb drive while in use, toast the the thumb drive :confused:

---

### Post by Neon_Knight on 2011-12-28
Well, see, I've tried that, but gparted doesn't let me add any partitions to the drive.  It doesn't believe that it has a partition table.  Trying to add a partition table to the drive with gparted outputs the "unrecognised disk label" error to the terminal, and simply returns, after a bit of loading, to the main gparted screen, with no changes.  After that, I still can't add any partitions to the partition table. 

I don't think gparted is going to fix it.

I used gpart to try to "guess" and write a new partition table to the device, but here is the output of the scan:

```

Guessed primary partition table:
Primary partition(1)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(2)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

```

Every number is a 0.  Clearly this is not a valid partition table.  So I didn't write that to the device.  

I also used testdisk but it doesn't seem to have any options that can help me. 

I also tried using parted from the command-line.  'Rescuing' the device outputs "unrecognised disk label".

Any other ideas? :confused:

---

### Post by Rex Bouwense on 2011-12-28
Are you saying that Gparted will not even reformat the flash drive?  What kind of flash drive are you talking about?

---

### Post by Neon_Knight on 2011-12-28
Yes, that's what the situation appears to be.

Reformat is greyed out in the gparted GUI.  All is greyed out except for "new" (as in, create new partition).

(Yes, I've run gparted as su)

It's a 4GB USB flash drive that I bought quite recently. It was working just fine until I accidentally pulled it out of the USB drive in the middle of a read/write operation.

It's now totally totally messed up, and all I want to do with it at this stage is completely re-format the thing to fat32, with a new partition table.

---

### Post by Rex Bouwense on 2011-12-28
I had to check Gparted because I couldn't remember all of the stuff.  When you go to Partition does it show the flash drive as mounted or mounted?  You cannot format with the drive mounted (as you know).  If it shows that it is mounted will it allow you to unmount or conversely if it is unmounted will it allow you to mount?  The flash drive may be fried although I have done exactly what you have done before without internal damage.  I could have been very lucky though.

---

### Post by westie457 on 2011-12-28
In Gparted with the USB drive plugged in [U]and[U] unmounted have you tried the 'Device' menu option to Create New Partition Table.

This usually works well at wiping the info of drives and creating a MBR for the drive.

---

### Post by Neon_Knight on 2011-12-28
No, the drive is not mounted.

Although oddly enough, on the "Partition" menu of Gparted, it has the option to "unmount" rather than to "mount", implying that it's mounted (It's greyed-out, however).  But a command-line umount confirmed that/dev/sdb is not mounted. So I'm not really sure what's going on there.

@westie457, that option fails.  I click it and all that happens is that all the drives reload in gparted. The terminal outputs "unrecognised disk label"

---

### Post by utnubuuser on 2011-12-28
dd is a very powerful command-line partitioning tool...

---

### Post by lukeiamyourfather on 2011-12-28
A possibility is the drive may have actual damage to the flash memory or auxiliary circuitry. Either coincidentally or directly related to removing it while in use. If GParted doesn't get it going I'd move on. A few weeks ago I bought a 16GB flash drive for $11 and I see 4GB drives for $5 all the time.

---

### Post by Rhizoid on 2011-12-28
I would give Testdisk a shot before you completely write it off...  [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by HermanAB on 2011-12-28
Howdy,

It seems that no-one gave you much low level advice.  The GUI tools work fine when everything is working properly, but once things go wrong, you need the command line tools, so that you can see the error messages.

So, plug the drive in.  Now run dmesg:
$ sudo dmesg

Note the device name e.g. sdb
(If your machine has one hard disk, it will be sda)

Confirm what is going on by looking at /dev:
$ ls /dev

You should see /dev/sda and /dev/sdb.  Partitions on sda will show up as sda1, sda2 and so on.

Now run fdisk and delete whatever partitions it sees on the USB disk:
$ sudo fdisk /dev/sdb
Type p to list the partitions.  Use d (repeatedly) to delete all of them, then use n to make one new primary partition.  Use t to rename the partition type to c (FAT32). Finally use w to write the partition table and exit.

The device is now partitioned, but still unformatted.  Use the mkfs.vfat command to create a file system on the partition you created and give it a meaningful label:
$ sudo mkfs.vfat -n USBDISK /dev/sdb1

The device is now formatted and ready for use.

Unplug it and replug it and the desktop system should offer to mount it for you as /media/USBDISK.

---

### Post by Zill on 2011-12-28
Neon_Knight:  Can you reformat the drive using the terminal? eg.
```
sudo mkfs -t vfat -v /dev/sdb1
```

Also, could their be some kind of write-protect switch tucked-away on the drive?

---

### Post by Neon_Knight on 2011-12-28
> **HermanAB said:**
> Howdy,

It seems that no-one gave you much low level advice.  The GUI tools work fine when everything is working properly, but once things go wrong, you need the command line tools, so that you can see the error messages.

So, plug the drive in.  Now run dmesg:
$ sudo dmesg

Note the device name e.g. sdb
(If your machine has one hard disk, it will be sda)

Confirm what is going on by looking at /dev:
$ ls /dev

You should see /dev/sda and /dev/sdb.  Partitions on sda will show up as sda1, sda2 and so on.

Now run fdisk and delete whatever partitions it sees on the USB disk:
$ sudo fdisk /dev/sdb
Type p to list the partitions.  Use d (repeatedly) to delete all of them, then use n to make one new primary partition.  Use t to rename the partition type to c (FAT32). Finally use w to write the partition table and exit.

The device is now partitioned, but still unformatted.  Use the mkfs.vfat command to create a file system on the partition you created and give it a meaningful label:
$ sudo mkfs.vfat -n USBDISK /dev/sdb1

The device is now formatted and ready for use.

Unplug it and replug it and the desktop system should offer to mount it for you as /media/USBDISK.

Thanks for the advice.

It didn't fully work - somehow fdisk failed to write sdc1 to the disk, as the mkfs command couldn't find it. (my USB device is sdc)  Here are my outputs: 

(fdisk)
```


Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-1018, default 1): 
Using default value 1
Last cylinder, +cylinders or +size{K,M,G} (1-1018, default 1018): 
Using default value 1018

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): c
Changed system type of partition 1 to c (W95 FAT32 (LBA))

Command (m for help): p

Disk /dev/sdc: 4009 MB, 4009754624 bytes
124 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x520b1ea8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1018     3913161    c  W95 FAT32 (LBA)

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: If you have created or modified any DOS 6.x
partitions, please see the fdisk manual page for additional
information.
Syncing disks.

```

And mkfs
```


david@david-netbook:~$ sudo mkfs.vfat -n USBDISK /dev/sdc1
mkfs.vfat 3.0.7 (24 Dec 2009)
/dev/sdc1: No such file or directory

```

Any thoughts?

---

### Post by utnubuuser on 2011-12-28
if this has been answered already...

with gparted, when you select Device from the toolbar, is there no option to "create partition table"?

---

### Post by Neon_Knight on 2011-12-28
> **utnubuuser said:**
> if this has been answered already...

with gparted, when you select Device from the toolbar, is there no option to "create partition table"?

No. Look. People keep suggesting this, even though I said in the very first post and in several subsequent posts that I've tried that and it gives an error "unrecognised disk label". 

Can you suggest a way to solve the "unrecognised disk label" error? If not, then "create partition table" in Gparted isn't really going to help me - my problem appears to be deeper than that.  I either have to solve the disk label error and use gparted - or use alternative software to fix my problem.

---

### Post by jockyburns on 2011-12-28
I had a very similar problem with a 2gb usb stick. Couldn't format it with any program at all. Tried GParted to no avail. Even sticking it into a computer running Windoze showed it in My Computer, but trying to format it returned the "No medium in Drive F. Please insert medium and try again." message. 
Gave up on it shortly afterwards as usb sticks are really as "Cheap as Chips" these days. ;) ;)

PS, just out of interest, a few years ago my digital camera's SD Card got fried by an electrostatic shock, and no amount of fiddling about with programs on computers could solve that either. The situation with the SD card was almost exactly the same. Card reader detected the card, but couldn't format it as "No medium detected" message came up.

---

### Post by Zill on 2011-12-28
> **Neon_Knight said:**
> ... my problem appears to be deeper than that.  I either have to solve the disk label error and use gparted - or use alternative software to fix my problem.
At around [$5 (£3) for another 4GB USB drive ]("http://www.ebay.co.uk/itm/6-Style-2GB-4GB-USB-2-0-Flash-Memory-Thumb-Stick-Storage-Drive-Pen-Device-2G-4G-/130613523635?pt=LH_DefaultDomain_0&var=&hash=item6420702b6a") I would just bin it. ;-)

---

### Post by westie457 on 2011-12-28
Last chance saloon. This command dd if=/dev/zero of=/dev/sda will fill a hard drive with 0's allowing it to be re-partitioned and formatted. Type it in and edit the last part to match the usb drive.

If you cannot partition and format after this then as someone has already said 'bin it and get another one'.

---

### Post by Neon_Knight on 2011-12-29
Alas, that didn't work.   It copied the 0s successfully, but I still have the same issue with "unrecognised disk label".  I could just bin it and get another one, I know they're not particularly expensive, but it just seems like a bit of a shame really.  All I did was accidentally pull it out, by rights it really should be fixable.  Oh well.

Thanks for your help, everyone.

---

### Post by lkraemer on 2011-12-30
There is an older HP format program that might do the trick.
I don't remember the software's name, and I'm out of state,
but I'll search old hard drives to see if I can locate it.

I've had the same type of problem once, when I unplugged a USB
Flash drive from a USB 1.0 port.  I ended up getting it replaced
by LG since it was still under warranty.  I since purchased a PCMCIA
USB 2.0 card to fix that problem.

REF: [http://files.extremeoverclocking.com/file.php?f=197](http://files.extremeoverclocking.com/file.php?f=197)
[http://download.cnet.com/HP-USB-Disk-Storage-Format-Tool/3000-2094_4-10974082.html](http://download.cnet.com/HP-USB-Disk-Storage-Format-Tool/3000-2094_4-10974082.html)
[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?swItem=MTX-UNITY-I23839](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?swItem=MTX-UNITY-I23839)
[http://h30434.www3.hp.com/t5/Other-HP-Consumer-Products-and/USB-Flash-Drive-v210w-16-GB-Write-Protected/td-p/263310](http://h30434.www3.hp.com/t5/Other-HP-Consumer-Products-and/USB-Flash-Drive-v210w-16-GB-Write-Protected/td-p/263310)
[http://www.softpedia.com/get/System/Hard-Disk-Utils/HP-USB-Disk-Storage-Format-Tool.shtml](http://www.softpedia.com/get/System/Hard-Disk-Utils/HP-USB-Disk-Storage-Format-Tool.shtml)

Extra Info:
[http://www.bootdisk.com/pendrive.htm](http://www.bootdisk.com/pendrive.htm)

I didn't check which was the latest version.......


lk

---

### Post by Hendra Fuhrer on 2012-06-29
> **Neon_Knight said:**
> Thanks for the advice.

It didn't fully work - somehow fdisk failed to write sdc1 to the disk, as the mkfs command couldn't find it. (my USB device is sdc)  Here are my outputs: 

(fdisk)
```


Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-1018, default 1): 
Using default value 1
Last cylinder, +cylinders or +size{K,M,G} (1-1018, default 1018): 
Using default value 1018

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): c
Changed system type of partition 1 to c (W95 FAT32 (LBA))

Command (m for help): p

Disk /dev/sdc: 4009 MB, 4009754624 bytes
124 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x520b1ea8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1018     3913161    c  W95 FAT32 (LBA)

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: If you have created or modified any DOS 6.x
partitions, please see the fdisk manual page for additional
information.
Syncing disks.

```

And mkfs
```


david@david-netbook:~$ sudo mkfs.vfat -n USBDISK /dev/sdc1
mkfs.vfat 3.0.7 (24 Dec 2009)
/dev/sdc1: No such file or directory

```

Any thoughts?

I did this :

sudo mkfs -t vfat -I /dev/sdc

and it worked for me

---

### Post by houseworkshy on 2012-06-29
I've had this one and gparted fixed it.  The first step is to set it up as a dos something, sorry can't remember the correct phrase but it's the first thing to do, it will mention that all data will be lost. Once that is done you can format it as FAT32. After that take a look at the flags and make sure they are as you like.  If you want to boot from it you will need to check the bootable flag for example.

---

### Post by lrcaballero on 2012-06-29
You probably don't want to hear this but if you have access to a windows computer, insert your USB drive wait to see what happens and if it works  right click to format to FAT32 a great tool to use in windows environment is parted magic or Partition Magic, or try using a Live CD such as Knoppix and see if it gets recognize this way.

Cheers,

---

### Post by jfca283 on 2012-09-17
Sometimes i experience issues as the described. The only solution to the problem is formatting the usb stick from windows. I'd love to find a way to fix this inconvenience using linux.

---

### Post by Bashing-om on 2012-09-17
ok ... I'll make my addition to the thread.
Pulled device->kernel still has the file as open, no matter what ....kernel has the "file" as open ...right ?  soooooo... gotta tell the kernel to terminate the process.

 You can use the fuser command to find out which process was keeping the device busy:
```
fuser -m /dev/sdc1

``` for instance output -> /dev/sdc1: 538
```
 ps auxw|grep 538

``` for instance output -> donncha 538 0.4 2.7 219212 56792 ? SLl Feb11 11:25 rhythmbox


Rhythmbox is the culprit! Close that down and umount the drive. Problem solved! 

This process should, imho, be adaptable to our situation.


just think'in <====BDQ

---

