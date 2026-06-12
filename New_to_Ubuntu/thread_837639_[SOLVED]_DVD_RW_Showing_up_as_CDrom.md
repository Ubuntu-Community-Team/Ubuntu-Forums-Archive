---
title: "[SOLVED] DVD RW Showing up as CDrom?"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by kayfes on 2008-06-22
My DVD Rw is showing up as and functioning as a cdrom only drive.  How would I fix this?

---

### Post by niyonk on 2008-06-22
Don't be alarmed. It's the same on mine. ;)
The DvDs themselves will burn just fine. therz nothin to fix here 
Correct me if i misunderstood your Q :biggrin:

---

### Post by scxtt on 2008-06-22
what's the output of:

**sudo lshw -class disk**

specifically the "*-cdrom" section . . .

---

### Post by kayfes on 2008-06-22
Hey thanks guys sorry for the delay in my response.  My problem right now is I can't get it to play DVDs no matter what I do.  

Here is the output of sudo lshw -class disk 

  *-cdrom:0               
       description: DVD writer
       product: DVD RW DW-D22A
       vendor: SONY
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: BFS1
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
          logical name: /media/cdrom0
          configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted
  *-cdrom:1
       description: SCSI CD-ROM
       product: CD-ROM SC-148A
       vendor: SAMSUNG
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: B400
       capabilities: removable audio
       configuration: ansiversion=5 status=open
  *-disk:0
       description: ATA Disk
       product: Maxtor 6Y160M0
       vendor: Maxtor
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: YAR5
       serial: Y46FLY5E
       size: 152GiB (163GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=3a3454d5
  *-disk:1
       description: ATA Disk
       product: WDC WD5000AACS-0
       vendor: Western Digital
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/sdb
       version: 01.0
       serial: WD-WCASU2014098
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00000001


The drive in question is of course crdrom0.  However in my home/media folder I have cdrom0, cdrom1 and cdrom2 and I only have 2 Optical drives.  Don't know if that helps or not.

---

### Post by kayfes on 2008-06-22
After some research it appears that DVD RW DW-D22A made by sony is a pile of junk.  I don't know if this is why it is showing up as a cdrom but apparently lots of people have had problems with it.  If I were to replace it does anyone have a recommendation for a cheap yet worthy device that will run in Ubuntu?

---

### Post by cariboo on 2008-06-22
I've always had good luck with LG at the wholesale level there are a couple of dollars more than a Sony drive. You should be able to pick one up for less than $40.00 US/CDN

Jim

---

### Post by scxtt on 2008-06-22
my LG DVDRW has performed great :)

```
*-cdrom
       description: DVD-RAM writer
       product: HL-DT-STDVDRRW GSA-4166B
       physical id: 1
       bus info: ide@0.1
       logical name: /dev/hdb
       version: 1.00
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=nodisc
```

---

### Post by kayfes on 2008-06-22
Went out and got an HP 1080i and it works great now.  Figured that was the reason it wasn't playing Dvds.  Could anyone tell me if that could be the reason wine freezes when I am trying to install games from the old sony dvd drive?

---

### Post by tipiglen on 2008-07-04
> *-cdrom:0
description: DVD writer
product: DVD RW DW-D22A
vendor: SONY
physical id: 0.0.0
bus info: scsi@0:0.0.0
logical name: /dev/cdrom1
logical name: /dev/dvd1
logical name: /dev/scd0
logical name: /dev/sr0
logical name: /media/cdrom0
version: BFS1
capabilities: removable audio cd-r cd-rw dvd dvd-r
configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted status=ready


try changing the relevant line in your fstab to show the FIRST logical name in the list.  Mine was showing /dev/scd0 and after I changed that to /dev/cdrom1 (as above) everything worked fine again.

Best of luck
ed

---

### Post by tipiglen on 2008-07-04
I neglected to say how to get the listing in the previous post


```

sudo lshw -C disk

```

Hope that helps

---

