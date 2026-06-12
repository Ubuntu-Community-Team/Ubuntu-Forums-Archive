---
title: "Help me find a disappearing hard drive"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by jasontu on 2008-09-16
I have a hard drive that I barely use on my Ubuntu box.  It was recognized and mounted just fine on boot up when I first got it.  I was going to back-up some data this morning and I discovered that it was no longer available in my Places menu.  It is detected in BIOS.  Can anyone help me re-detect it or re-mount it?

Thanks

---

### Post by Harisz750 on 2008-09-16
first post results of ```
sudo fdisk -l
```

and then let's see your fstab ```
gksudo gedit /etc/fstab
```

---

### Post by Elfy on 2008-09-16
> and then let's see your fstabyou don't need to open it as root to view it, ```
cat /etc/fstab
``` will show it as easily.

It would probably help to post the UUIDs as well

```
sudo blkid
```

---

### Post by Mornedhel on 2008-09-16
Sorry, what, "cat nano" ?! I think you forgot to erase "nano" here.

---

### Post by Elfy on 2008-09-16
:D - it lives up the road

---

### Post by jasontu on 2008-09-17
```
jason@timmy:~$ sudo fdisk -l
[sudo] password for jason: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000078e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris
jason@timmy:~$ sudo blkid
/dev/sda1: UUID="e5651685-d49d-453d-b6a8-87d831e2daf0" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="904c355a-07fa-4bbd-70b3-aeac0e940556" 
jason@timmy:~$ 

```

---

### Post by jasontu on 2008-09-20
```
jason@timmy:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e5651685-d49d-453d-b6a8-87d831e2daf0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=904c355a-07fa-4bbd-70b3-aeac0e940556 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
jason@timmy:~$ 
```

Still not sure what to do with this information.

---

### Post by Elfy on 2008-09-20
All of the harddrive you have in 2 partitions - both are being mounted - one is the root drive and the other is swap.

It would appear from the information available that all drives/partitions are available to you.

Do you have 2 hard drives in your pc - if so then the second appears not to be working.

Reboot, when you get the opportunity do escape or del or whatever you need to get into bios - make sure that all harddrives are being recognised. If you believe you have more than 1 harddrive then you are going to need to make sure that 2nd is actually physically working. Check the cable s for your drives.

---

### Post by jasontu on 2008-09-30
The second harddrive is seen in BIOS, but still not seen in Ubuntu.

What is the next step from here?  Could it still be something physical (like cables, etc.) if it is seen in the BIOS?

Thanks all for the help.

---

### Post by Elfy on 2008-09-30
I would yes, if I had a drive recognised in BIOS but not appearing in ubuntu at all then I would make sure that all the cables are seated properly. Remove and  check the cables and plug back together, same for the power connectors.

---

### Post by tiggsy on 2008-10-18
I have a similar problem. The command
```
sudo lshw -C disk
```
shows 
/dev/sdc (an external drive)
/dev/sda (the drive i use all the time) and 
/dev/sdb (a new drive i installed a while back but haven't been able to access).

The command 
```
sudo fdisk -l
```
shows all three

But the command
```
cat /etc/fstab
```
shows this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=976d125a-3a43-472c-9907-48d97c8302c2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=750be057-3b60-424f-a928-4d283e84d457 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0

There's no reference to sdb or sdc, and the lines relating to sda seem to be commented out. But i have access to sda and sdc (not sdb).

Help!

---

### Post by Elfy on 2008-10-18
In fstab the important parts are uncommented - # /dev/sda1 is just a label :)

if sdc is likely accessible it will be recognised when you plug it in, you need to add the other drive to fstab.

IF you're up to do it yourself and come back with errors then you will need the UUID for the partition in sdb - ```
sudo blkid
``` will give you that, you will need to make a folder for it to mount in and then add the necessary to a new line in fstab.

This goes through it for an ext3 partition - [http://ubuntuforums.org/showpost.php?p=5720510&postcount=5](http://ubuntuforums.org/showpost.php?p=5720510&postcount=5)

This will help for other formats (and a whole lot more) - [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

If you want help post back with results of these commands

```
sudo fdisk -l
sudo blkid
df -h
```

---

### Post by tiggsy on 2008-10-21
> **forestpixie said:**
> This goes through it for an ext3 partition - [http://ubuntuforums.org/showpost.php?p=5720510&postcount=5](http://ubuntuforums.org/showpost.php?p=5720510&postcount=5)

This will help for other formats (and a whole lot more) - [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)


Right...

I tried to amend fstab and ended up with a right royal cockup, as we say over here. Was not able to use the computer at all until i installed a fresh version of Ubuntu onto the "missing drive", which was blank in any case (unfortunately, this is Gutsy, as i don't have a Hardy disk atm - which will soon be dealt with), and mucked about in the BIOS so as to get the new disk booting, rather than the other one...

In order to avoid doing the same thing again and ending up with no bootable disk at all! i am going to paste the output of the various commands here, and pray that you can guide me to getting access to the other disk. They are both (ext2) according to the output from sudo blkid, although fstab refers to sda as ext3, so im a bit confuzzled...

```

tiggsy@tiggsys-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a2a475cc-be6b-4085-8add-97d032bde767 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=f9cb8f15-33f6-4160-ae9f-4b4ab70ce62e none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


tiggsy@tiggsys-desktop:~$ sudo blkid
/dev/sda1: UUID="a2a475cc-be6b-4085-8add-97d032bde767" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="f9cb8f15-33f6-4160-ae9f-4b4ab70ce62e" 
/dev/sdb1: UUID="976d125a-3a43-472c-9907-48d97c8302c2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="750be057-3b60-424f-a928-4d283e84d457" 
/dev/sdc1: UUID="DE14FCE414FCC117" LABEL="New Volume" TYPE="ntfs" 
/dev/sdc5: UUID="B6E884C0E884807B" TYPE="ntfs" 


tiggsy@tiggsys-desktop:~$ fdisk -l

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a2487d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       15210   122174293+   7  HPFS/NTFS
/dev/sdc2           15211       30401   122021707+   f  W95 Ext'd (LBA)
/dev/sdc5           15211       30401   122021676    7  HPFS/NTFS


tiggsy@tiggsys-desktop:~$ sudo lshw -C disk
  *-cdrom                 
       description: DVD writer
       product: _NEC DVD_RW ND-3540A
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: 1.01
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
       configuration: mode=udma2 status=nodisc
  *-disk:0
       description: SCSI Disk
       product: ST3250410AS
       vendor: ATA
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 3.AA
       serial: 9RY28SKQ
       size: 232GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-disk:1
       description: SCSI Disk
       product: WDC WD2500JD-22H
       vendor: ATA
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/sdb
       version: 08.0
       serial: WD-WCAL73259870
       size: 232GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-disk
       description: SCSI Disk
       product: TM3250310AS
       vendor: MAXTOR S
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdc
       size: 232GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=2


tiggsy@tiggsys-desktop:~$  df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             227G  2.1G  213G   1% /
varrun                506M   88K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M  104K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sdc5             117G   48G   70G  41% /media/disk
/dev/sdc1             117G   36G   82G  31% /media/New Volume

```

---

### Post by Elfy on 2008-10-21
You should have just used the fstab backup to get back where you were.

Your fdisk -l output is missing sda and sdb, can you run it again please.

You also appear to have 2 swaps is that intentional?

---

### Post by tiggsy on 2008-10-21
(well, i thought i did that, but it all went belly up anyway.)

I just installed 8.04 to replace Gutsy, so here is the new output. 

Both sda and sdb appear in fdisk now, but not in fstab,

The reason there are 2 swaps is because sdb used to be boot, but as it wouldn't i installed a fresh copy on sda, swapped them over in BIOS (as it was still trying to boot from sdb even after doing stuff in grub) and havent yet got round to making sdb one big disk again - if thats even a good idea... think so?

sdb still isnt showing up. not in fstab, so understandable, i guess

As i did a fresh install, will paste all the new output, in case it's different 

```
tiggsy@tiggsys-desktop:~$ sudo lshw -C disk
[sudo] password for tiggsy: 
  *-cdrom                 
       description: DVD writer
       product: DVD_RW ND-3540A
       vendor: _NEC
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.01
       serial: [_NEC    DVD_RW ND-3540A 1.0105031600
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=open
  *-disk:0
       description: ATA Disk
       product: ST3250410AS
       vendor: Seagate
       physical id: 0
       bus info: scsi@5:0.0.0
       logical name: /dev/sda
       version: 3.AA
       serial: 9RY28SKQ
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=8d628d62
  *-disk:1
       description: ATA Disk
       product: WDC WD2500JD-22H
       vendor: Western Digital
       physical id: 1
       bus info: scsi@6:0.0.0
       logical name: /dev/sdb
       version: 08.0
       serial: WD-WCAL73259870
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0000130e
  *-disk
       description: SCSI Disk
       product: TM3250310AS
       vendor: MAXTOR S
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdc
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=2 signature=1a2487d0
tiggsy@tiggsys-desktop:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d628d62

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30024   241167748+  83  Linux
/dev/sda2           30025       30401     3028252+   5  Extended
/dev/sda5           30025       30401     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000130e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30024   241167748+  83  Linux
/dev/sdb2           30025       30401     3028252+   5  Extended
/dev/sdb5           30025       30401     3028221   82  Linux swap / Solaris

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a2487d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       15210   122174293+   7  HPFS/NTFS
/dev/sdc2           15211       30401   122021707+   f  W95 Ext'd (LBA)
/dev/sdc5           15211       30401   122021676    7  HPFS/NTFS
tiggsy@tiggsys-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=03be116b-dd48-45ae-a203-51589cabc5c1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=f9cb8f15-33f6-4160-ae9f-4b4ab70ce62e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
tiggsy@tiggsys-desktop:~$ sudo blkid
/dev/sda1: UUID="03be116b-dd48-45ae-a203-51589cabc5c1" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="f9cb8f15-33f6-4160-ae9f-4b4ab70ce62e" 
/dev/sdb1: UUID="976d125a-3a43-472c-9907-48d97c8302c2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="750be057-3b60-424f-a928-4d283e84d457" 
/dev/sdc1: UUID="DE14FCE414FCC117" LABEL="New Volume" TYPE="ntfs" 
/dev/sdc5: UUID="B6E884C0E884807B" TYPE="ntfs" 
tiggsy@tiggsys-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             229G  2.2G  215G   2% /
varrun                506M  100K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   80K  506M   1% /dev
devshm                506M   12K  506M   1% /dev/shm
lrm                   506M   38M  468M   8% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon      229G  2.2G  215G   2% /home/tiggsy/.gvfs
/dev/sdc5             117G   48G   70G  41% /media/disk
/dev/sdc1             117G   36G   82G  31% /media/New Volume
tiggsy@tiggsys-desktop:~$ 
```

---

### Post by Elfy on 2008-10-21
Ok I would indeed lose the extra swap you can do that first and as nothing is mounted you should be able to do so without booting a livecd, install gparted and turn of the swap for the moment incase it's being used

```
sudo apt-get install gparted
sudo swapoff -a
```

Run gparted ```
gksudo gparted
``` delet the swap from sdb5, apply, delete the extended partitiona, apply and then resize sda1 to take up rest of drive, apply and close.

Turn swap on again```
sudo swapon -a
```

Run sudo blkid again to ge tthe new UUID for sdb1

Make a folder to mount it in ```
sudo mkdir /media/data
``` - look at link to my post in #12 above for difference between mounting in /media and /mnt

Backup and edit fstab

```
sudo cp /etc/fstab /etc/fstab.2110
gksudo gedit /etc/fstab
```

At end of the file add, remember to use new UUID

```
#dev/sdb1
UUID=number /media/data ext3 relatime 0 2
```

Run command to mount drive

```
sudo mount -a
```
check it's there with ```
df -h
```

Ensure permissions ok, replace user with your username

```
sudo chown user.user /media/data
sudo chmod 770 /media/disc
```

That should give you the full drive available

---

### Post by tiggsy on 2008-10-21
Thanks. That all seemed to go fine 

I used mnt instead of media, as i already have the 2 halves of my external drive cluttering up the desktop

When you said 
```
sudo chown user.user /media/data
sudo chmod 770 /media/disc
```

should the second one have been media/data?? Hope so, I used /mnt/data 

So i went to places->computer and looked at the list, but the new drive doesnt show up. Should I reboot? I thought it would show up with the command mount -a??

This is df -h

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             229G  2.6G  215G   2% /
varrun                506M  116K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   64K  506M   1% /dev
devshm                506M   12K  506M   1% /dev/shm
/dev/sdc5             117G   48G   70G  41% /media/disk
/dev/sdc1             117G   36G   82G  31% /media/New Volume
tmpfs                 506M   39M  467M   8% /lib/modules/2.6.24-21-generic/volatile
tmpfs                 506M   39M  467M   8% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon      229G  2.6G  215G   2% /home/tiggsy/.gvfs
/dev/sdb1             230G  206G   15G  94% /mnt/data

```

---

### Post by Elfy on 2008-10-21
> **tiggsy said:**
> Thanks. That all seemed to go fine 

I used mnt instead of media, as i already have the 2 halves of my external drive cluttering up the desktop

When you said 
```
sudo chown user.user /media/data
sudo chmod 770 /media/disc
```

should the second one have been media/data?? Hope so, I used /mnt/data 

So i went to places->computer and looked at the list, but the new drive doesnt show up. Should I reboot? I thought it would show up with the command mount -a??

This is df -h

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             229G  2.6G  215G   2% /
varrun                506M  116K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   64K  506M   1% /dev
devshm                506M   12K  506M   1% /dev/shm
/dev/sdc5             117G   48G   70G  41% /media/disk
/dev/sdc1             117G   36G   82G  31% /media/New Volume
tmpfs                 506M   39M  467M   8% /lib/modules/2.6.24-21-generic/volatile
tmpfs                 506M   39M  467M   8% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon      229G  2.6G  215G   2% /home/tiggsy/.gvfs
/dev/sdb1             230G  206G   15G  94% /mnt/data

```

Yes it should have been chmod /mnt/data - recycling posts I am :)

The drive is there at the end 
/dev/sdb1             230G  206G   15G  94% /mnt/data

---

### Post by tiggsy on 2008-10-21
Why isnt it shown in my list at places->computer?

That shows 
125.0 GB Media (usb)
CD-RW/DVD RW Drive
Floppy Drive
New Volume (usb)
Filesystem

the last seems to be sda, as it has virtually nothing on it

---

### Post by Elfy on 2008-10-21
To give it a name 

```
sudo tune2fs -L *name* /dev/sdb1
```

It might need to be rebooted, but it should show

Edit - it also appears that it only shows in places in nautilus if it's mounted to /media - you can make a shortcut for it though

Open nautilus - filesystem - mnt - then drag the folder form the right hands pane to the shortcuts in the left pane

Or unmount form /mnt and redo fstab and folder to be /media/data

---

### Post by tiggsy on 2008-10-21
Well, that didnt work, so i decided to let it show on the desktop, and did it all again with /media/data

That worked (after a boot).

Now for the final step - hopefully.

How do I get all the settings and stuff that i had on the old disk onto the new one, without having to try and remember the numerous different things i've added?

---

### Post by Elfy on 2008-10-21
Did you see my edit - it said that amongst other things :)

The old drive has your old /home in it I assume - if you used the same username it should just be a case of copying the hidden folder.

If that doesn't work then start a new thread for it.

---

### Post by tiggsy on 2008-10-21
Yeah. i spotted that after i did my reply. :))

Thanks a lot. id've been lost without yer, forestpixie.

The second forest pixie ive ever known...

---

### Post by Elfy on 2008-10-21
There's another? :)

---

