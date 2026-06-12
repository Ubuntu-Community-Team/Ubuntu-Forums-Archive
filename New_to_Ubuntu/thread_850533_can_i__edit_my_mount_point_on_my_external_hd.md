---
title: "can i  edit my mount_point on my external hd?"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-07-05
i think i can fix my  hard drive if im able to edit that

---

### Post by rbprogrammer on 2008-07-05
I have never tried this before, but did you look at the drive's properties?  Insert the drive and let it auto-mount.  Then right-click and go to the "Properties" menu option.  Then go to the "Drive" tab, then under the "Settings" thing, it looks like you can change the mount point.

---

### Post by PatrickMoore on 2008-07-05
> **rbprogrammer said:**
> I have never tried this before, but did you look at the drive's properties?  Insert the drive and let it auto-mount.  Then right-click and go to the "Properties" menu option.  Then go to the "Drive" tab, then under the "Settings" thing, it looks like you can change the mount point.

the problem is that it wont mount im getting an error message.

please see attachment to see if you know whats up

---

### Post by neurostu on 2008-07-05
Have you tried mounting it from the command line?

Do you know what the file format is?

The standard mount command is:
```

sudo mount /dev/<drive> /media/MountDir

```
some times you have t ospecify the file system type...

Do you know what format the drive is?

---

### Post by PatrickMoore on 2008-07-05
> **neurostu said:**
> Have you tried mounting it from the command line?

Do you know what the file format is?

The standard mount command is:
```

sudo mount /dev/<drive> /media/MountDir

```
some times you have t ospecify the file system type...

Do you know what format the drive is?

i can mount the drive manually by using the pmount command. im going to try writting to it... no luck i do not have sufficient permission.

---

### Post by KuroYoma on 2008-07-05
Try this 

sudo mount -t <format> /dev/<drive> /media/<mountdir> -o force

I have had to use this before and it should work as long as u fill in the info correctly.

---

### Post by PatrickMoore on 2008-07-05
> **KuroYoma said:**
> Try this 

sudo mount -t <format> /dev/<drive> /media/<mountdir> -o force

I have had to use this before and it should work as long as u fill in the info correctly.

```
mount: mount point /media/sdb1 does not exist

```

/media/sdb1 is what i get when i use pmount in the terminal and go into the properties of the drive

---

### Post by KuroYoma on 2008-07-05
try this then

mkdir /media/sdb1

you might have to be in root if so then just add the sudo command

sudo mkdir /media/sdb1 
 
then remount your device with the code above or what ever method works for you.

---

### Post by neurostu on 2008-07-05
> **PatrickMoore said:**
> i can mount the drive manually by using the pmount command. im going to try writting to it... no luck i do not have sufficient permission.

You can try using:
```

chown -R <username> mountdir

```
That will give you ownership of the drive (and all sub dirs) and you should be able to write to it. 

If you can't write after that then create a newDir in your home dir and mount to that newDir. Then chown that new dir and you should be able to read/write

---

### Post by PatrickMoore on 2008-07-05
> **KuroYoma said:**
> try this then

mkdir /media/sdb1

you might have to be in root if so then just add the sudo command

sudo mkdir /media/sdb1 
 
then remount your device with the code above or what ever method works for you.

progress is sort of made... i got a new message.
```
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

its like one long logic problem

---

### Post by KuroYoma on 2008-07-05
Ok what is your fs, File system, (Format) for sdb1?

What is the EXACT code you are typing in??

---

### Post by unutbu on 2008-07-05
Please post
```

cat /etc/fstab
sudo fdisk -l

```
(The last letter is a lowercase L, not a one).

---

### Post by PatrickMoore on 2008-07-05
> **KuroYoma said:**
> Ok what is your fs, File system, (Format) for sdb1?

ext2.

---

### Post by PatrickMoore on 2008-07-05
> **unutbu said:**
> Please post
```

cat /etc/fstab
sudo fdisk -l

```
(The last letter is a lowercase L, not a one).

```
patrick@patrick-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=0073e8ca-e864-4c8b-bc81-3a701ebc97d7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=ddbc44b8-a749-419c-9b6a-60501e1488a9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

```
patrick@patrick-laptop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x282d282d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda3               1        9468    76051678+  83  Linux
/dev/sda4            9469        9729     2096482+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux

```

---

### Post by KuroYoma on 2008-07-05
also plz post the EXACT code you are typing into the terminal when you are attempting to mount the device.

---

### Post by PatrickMoore on 2008-07-05
patrick@patrick-laptop:~$ sudo mount -t ext2 /dev/sdb1 /media/sdb1 -o force
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by KuroYoma on 2008-07-05
Ok at [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=432103](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=432103)  they talk about this.

Let me know if this helps or not

---

### Post by unutbu on 2008-07-05
Here's an experiment I did with a USB key:

```

private@ease:~% sudo fdisk -l
...
Disk /dev/sdb: 2004 MB, 2004877312 bytes
16 heads, 32 sectors/track, 7648 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x000961c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7648     1957872   **83**  Linux
```
Note that Id 83 means ext3, not ext2. 

```
private@ease:~% sudo mount -t **ext2** /dev/sdb1 /media/test/ -o force
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

```
private@ease:~% sudo mount -t **ext3** /dev/sdb1 /media/test/ -o force
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

```
private@ease:~% sudo mount -t ext3 /dev/sdb1 /media/test/ 
```
By golly, it worked without the -o force option.

```

private@ease:~% mount
...
/dev/sdb1 on /media/test type ext3 (rw)
```

So, perhaps try:
```
sudo mount -t ext3 /dev/sdb1 /media/sdb1
```

---

### Post by PatrickMoore on 2008-07-05
ok i need help deciphering this...

```
patrick@patrick-laptop:~$ dmesg | tail 
[ 4424.973110] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 4424.973121] ata1.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 8 in
[ 4424.973123]          cdb 25 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 4424.973124]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 4424.973127] ata1.00: status: { DRDY }
[ 4429.674363] ata1: port is slow to respond, please be patient (Status 0xd0)
[ 4432.679488] ata1: device not ready (errno=-16), forcing hardreset
[ 4432.679494] ata1: soft resetting link
[ 4433.207134] ata1.00: configured for MWDMA2
[ 4433.207149] ata1: EH complete

```

---

### Post by unutbu on 2008-07-05
Please post
```

dmesg | grep -i ata
```

---

### Post by PatrickMoore on 2008-07-05
> **unutbu said:**
> Please post
```

dmesg | grep -i ata
```

```
patrick@patrick-laptop:~$ dmesg | grep -i ata
[    0.000000]  BIOS-e820: 000000005df00000 - 000000005df17000 (ACPI data)
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[   11.724494] Memory: 1505032k/1539072k available (2489k kernel code, 33644k reserved, 1318k data, 320k init)
[   12.437797] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[   15.445759] libata version 3.00 loaded.
[   16.205212] pata_amd 0000:00:0d.0: version 0.3.10
[   16.206089] scsi1 : pata_amd
[   16.206363] scsi2 : pata_amd
[   16.206881] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
[   16.206884] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
[   16.540522] ata1.00: ATAPI: TSSTcorpCD/DVDW TS-L632D, HH15, max MWDMA2
[   16.728163] ata1.00: configured for MWDMA2
[   16.728196] ata2: port disabled. ignoring.
[   16.742907] sata_nv 0000:00:0e.0: version 3.5
[   16.744549] scsi3 : sata_nv
[   16.744942] scsi4 : sata_nv
[   16.745080] ata3: SATA max UDMA/133 cmd 0x30c0 ctl 0x30b4 bmdma 0x3090 irq 19
[   16.745083] ata4: SATA max UDMA/133 cmd 0x30b8 ctl 0x30b0 bmdma 0x3098 irq 19
[   17.211292] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   17.219452] ata3.00: ATA-7: TOSHIBA MK8034GSX, AH301H, max UDMA/100
[   17.219456] ata3.00: 156301488 sectors, multi 16: LBA48 
[   17.227433] ata3.00: configured for UDMA/100
[   17.538817] ata4: SATA link down (SStatus 0 SControl 300)
[   17.549528] scsi 3:0:0:0: Direct-Access     ATA      TOSHIBA MK8034GS AH30 PQ: 0 ANSI: 5
[   17.911572] EXT3-fs: mounted filesystem with ordered data mode.
[ 1635.856975] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 1635.856998] ata1.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 8 in
[ 1635.857005] ata1.00: status: { DRDY }
[ 1638.990639] ata1: port is slow to respond, please be patient (Status 0xd0)
[ 1642.910481] ata1: device not ready (errno=-16), forcing hardreset
[ 1642.910487] ata1: soft resetting link
[ 1643.123109] ata1.00: configured for MWDMA2
[ 1643.123122] ata1: EH complete
[ 1719.635402] ata1.00: qc timeout (cmd 0xa0)
[ 1719.635412] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 1719.635422] ata1.00: cmd a0/00:00:00:0c:00/00:00:00:00:00/a0 tag 0 pio 12 in
[ 1719.635429] ata1.00: status: { DRDY ERR }
[ 1724.356384] ata1: port is slow to respond, please be patient (Status 0xd0)
[ 1728.521705] ata1: device not ready (errno=-16), forcing hardreset
[ 1728.521711] ata1: soft resetting link
[ 1728.988407] ata1.00: configured for MWDMA2
[ 1728.988428] ata1: EH complete
[ 2252.247570] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 2252.247581] ata1.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 8 in
[ 2252.247587] ata1.00: status: { DRDY }
[ 2256.912892] ata1: port is slow to respond, please be patient (Status 0xd0)
[ 2261.780940] ata1: device not ready (errno=-16), forcing hardreset
[ 2261.780945] ata1: soft resetting link
[ 2262.206557] ata1.00: configured for MWDMA2
[ 2262.206570] ata1: EH complete
[ 2441.764176] ata1.00: qc timeout (cmd 0xa0)
[ 2441.764187] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 2441.764196] ata1.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 8 in
[ 2441.764203] ata1.00: status: { DRDY ERR }
[ 2446.169620] ata1: port is slow to respond, please be patient (Status 0xd1)
[ 2450.275241] ata1: device not ready (errno=-16), forcing hardreset
[ 2450.275247] ata1: soft resetting link
[ 2450.794650] ata1.00: configured for MWDMA2
[ 2450.794671] ata1: EH complete
[ 2926.193898] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 2926.193910] ata1.00: cmd a0/00:00:00:0c:00/00:00:00:00:00/a0 tag 0 pio 12 in
[ 2926.193916] ata1.00: status: { DRDY }
[ 2931.230635] ata1: port is slow to respond, please be patient (Status 0xd0)
[ 2936.215476] ata1: device not ready (errno=-16), forcing hardreset
[ 2936.215482] ata1: soft resetting link
[ 2936.739032] ata1.00: configured for MWDMA2
[ 2936.739047] ata1: EH complete
[ 3334.472373] ata1.00: qc timeout (cmd 0xa0)
[ 3334.472384] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 3334.472394] ata1.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 8 in
[ 3334.472401] ata1.00: status: { DRDY ERR }
[ 3339.448973] ata1: port is slow to respond, please be patient (Status 0xd1)
[ 3344.144812] ata1: device not ready (errno=-16), forcing hardreset
[ 3344.144817] ata1: soft resetting link
[ 3344.354242] ata1.00: configured for MWDMA2
[ 3344.354260] ata1: EH complete
[ 3865.859792] ata1.00: qc timeout (cmd 0xa0)
[ 3865.859804] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 3865.859814] ata1.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 8 in
[ 3865.859820] ata1.00: status: { DRDY ERR }
[ 3870.847246] ata1: port is slow to respond, please be patient (Status 0xd0)
[ 3875.722004] ata1: device not ready (errno=-16), forcing hardreset
[ 3875.722010] ata1: soft resetting link
[ 3876.249505] ata1.00: configured for MWDMA2
[ 3876.249526] ata1: EH complete
[ 4424.973110] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 4424.973121] ata1.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 8 in
[ 4424.973127] ata1.00: status: { DRDY }
[ 4429.674363] ata1: port is slow to respond, please be patient (Status 0xd0)
[ 4432.679488] ata1: device not ready (errno=-16), forcing hardreset
[ 4432.679494] ata1: soft resetting link
[ 4433.207134] ata1.00: configured for MWDMA2
[ 4433.207149] ata1: EH complete
[ 4644.532126] ata1.00: qc timeout (cmd 0xa0)
[ 4644.532136] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 4644.532145] ata1.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 8 in
[ 4644.532152] ata1.00: status: { DRDY ERR }
[ 4649.509941] ata1: port is slow to respond, please be patient (Status 0xd1)
[ 4654.491046] ata1: device not ready (errno=-16), forcing hardreset
[ 4654.491052] ata1: soft resetting link
[ 4655.014535] ata1.00: configured for MWDMA2
[ 4655.014555] ata1: EH complete
[ 4713.989531] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 4713.989542] ata1.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 4713.989547] ata1.00: status: { DRDY }
[ 4717.892986] ata1: port is slow to respond, please be patient (Status 0xd0)
[ 4721.732069] ata1: device not ready (errno=-16), forcing hardreset
[ 4721.732075] ata1: soft resetting link
[ 4722.182068] ata1.00: configured for MWDMA2
[ 4722.182081] ata1: EH complete

```

---

### Post by KuroYoma on 2008-07-05
unutbu may be right try without -o force.  I used that command for my 500g external HD and it may be different for u.  as for the dmesg | tail, i am sry to say it makes no sense to me.  

unutbu: I like that,  the experiment i mean.  that was a neat little trik  thnx for that because i had forgotten that the -o force option doesn't always work on certain devices.  i guess i just to quick linked the simulatises of Ext HD and same msgs together and thought i would add input.

again try unutbu's theory.

---

### Post by PatrickMoore on 2008-07-05
> **KuroYoma said:**
> unutbu may be right try without -o force.  I used that command for my 500g external HD and it may be different for u.  as for the dmesg | tail, i am sry to say it makes no sense to me.  

unutbu: I like that,  the experiment i mean.  that was a neat little trik  thnx for that because i had forgotten that the -o force option doesn't always work on certain devices.  i guess i just to quick linked the simulatises of Ext HD and same msgs together and thought i would add input.

again try unutbu's theory.


i cant find the code you wanted me to try...

---

### Post by KuroYoma on 2008-07-05
mount -t <fs> /dev/sdb1 /media/<mountdir>

its in the post where he talks about his little experiment with my -o force line

basically try to mount again just don't do the -o force part.

---

### Post by PatrickMoore on 2008-07-05
beautiful... it mounts. but now comes the next piece of the puzzle how do i get it to auto mount when i plug it in?

---

### Post by unutbu on 2008-07-05
Add
```
#/dev/sdb1       /media/sdb1     defaults                0      2
UUID=85fa3d3f-7fea-44fc-8aaf-9f74aa8ce0f4       /media/sdb1     defaults                0      2
```
to the end of your /etc/fstab.

---

### Post by PatrickMoore on 2008-07-05
> **unutbu said:**
> Add
```
#/dev/sdb1       /media/sdb1     defaults                0      2
UUID=85fa3d3f-7fea-44fc-8aaf-9f74aa8ce0f4       /media/sdb1     defaults                0      2
```
to the end of your /etc/fstab. 


how do i access that.

---

### Post by louieb on 2008-07-05
Just wondering if the label on the external drives partition did not get messed up. Ubuntu will use the label to name the mount point. 

```
e2label /dev/sda# newname
```

e2label works for ext2/ext3 file systems. For other file systems the label can be set with GParted v0.3.7 or higher.

---

### Post by unutbu on 2008-07-05
Hold on -- do you want your hard drive to mount at boot time, or do you want it to be auto-detected whenever you plug it in?

If you want it to be automounted at boot time, then 
```
gksu gedit /etc/fstab
```
Add
```

#/dev/sdb1       /media/sdb1     defaults                0      2
UUID=85fa3d3f-7fea-44fc-8aaf-9f74aa8ce0f4       /media/sdb1     defaults                0      2

```
to the end of your /etc/fstab. Save and quit gedit.

If you want it to be auto-detected like a hot-swappable device, then I'm not quite sure. Can you hot-swap an external hard drive? If its possible, be sure to always umount it properly before you unplug it. 

Anyway, if it's possible, my only suggestions are to:

Click on System>Preferences>Removable drives and media.
Make sure "Mount removable drives when hot-plugged" is enabled. (The one above the red oval).
[URL="http://ubuntuforums.org/attachment.php?attachmentid=76157&stc=1&d=1215025428"]
[img]http://ubuntuforums.org/attachment.php?attachmentid=76157&stc=1&thumb=1&d=1215025426[/img]
[/URL]

Also click on System>Administration>Users and Groups.
Click your username. Click Properties. Click the User Privileges Tab. (See attachment).
Make sure "Access external storage devices automatically" is enabled.
[URL="http://ubuntuforums.org/attachment.php?attachmentid=76251&d=1215097261
"][img]http://ubuntuforums.org/attachment.php?attachmentid=76251&stc=1&thumb=1&d=1215097261[/img]
[/URL]

---

### Post by PatrickMoore on 2008-07-05
> **louieb said:**
> Just wondering if the label on the external drives partition did not get messed up. Ubuntu will use the label to name the mount point. 

```
e2label /dev/sda# newname
```

e2label works for ext2/ext3 file systems. For other file systems the label can be set with GParted v0.3.7 or higher.

patrick@patrick-laptop:~$ e2label /dev/sda1 newname
e2label: No such file or directory while trying to open /dev/sda1
Couldn't find valid filesystem superblock.

i got nothing

---

### Post by PatrickMoore on 2008-07-06
> **unutbu said:**
> Hold on -- do you want your hard drive to mount at boot time, or do you want it to be auto-detected whenever you plug it in?

If you want it to be automounted at boot time, then 
```
gksu gedit /etc/fstab
```
Add
```

#/dev/sdb1       /media/sdb1     defaults                0      2
UUID=85fa3d3f-7fea-44fc-8aaf-9f74aa8ce0f4       /media/sdb1     defaults                0      2

```
to the end of your /etc/fstab. Save and quit gedit.

If you want it to be auto-detected like a hot-swappable device, then I'm not quite sure. Can you hot-swap an external hard drive? If its possible, be sure to always umount it properly before you unplug it. 



Anyway, if it's possible, my only suggestions are to:

Click on System>Preferences>Removable drives and media.
Make sure "Mount removable drives when hot-plugged" is enabled. (The one above the red oval).
[URL="http://ubuntuforums.org/attachment.php?attachmentid=76157&stc=1&d=1215025428"]
[img]http://ubuntuforums.org/attachment.php?attachmentid=76157&stc=1&thumb=1&d=1215025426[/img]
[/URL]

Also click on System>Administration>Users and Groups.
Click your username. Click Properties. Click the User Privileges Tab. (See attachment).
Make sure "Access external storage devices automatically" is enabled.
[URL="http://ubuntuforums.org/attachment.php?attachmentid=76251&d=1215097261
"][img]http://ubuntuforums.org/attachment.php?attachmentid=76251&stc=1&thumb=1&d=1215097261[/img]
[/URL]

i have it set to auto detect but it wont mount ill post my error message again

---

### Post by KuroYoma on 2008-07-06
After you successfully mount the device, bring up its propeties and goto the volume tab, the expand the settings and you will see "Mount Point" "File System" "Mount Options"

WARNING:  Plz make sure you mkdir the mount point before modifying the properties and make sure your user has permission to access the mountdir

---

### Post by PatrickMoore on 2008-07-06
> **KuroYoma said:**
> After you successfully mount the device, bring up its propeties and goto the volume tab, the expand the settings and you will see "Mount Point" "File System" "Mount Options"

WARNING:  Plz make sure you mkdir the mount point before modifying the properties and make sure your user has permission to access the mountdir

still having the same issue

---

### Post by louieb on 2008-07-06
> **PatrickMoore said:**
> ```
patrick@patrick-laptop:~$ e2label /dev/sda1 newname
e2label: No such file or directory while trying to open /dev/sda1
Couldn't find valid filesystem superblock.
```i got nothing
 
Did you mean to try** /dev/sdb1** ? Did not see a /dev/sda1 in the fdisk output posted earlier.

---

### Post by unutbu on 2008-07-06
Try [http://ubuntuforums.org/showpost.php?p=2884085&postcount=17](http://ubuntuforums.org/showpost.php?p=2884085&postcount=17)

---

