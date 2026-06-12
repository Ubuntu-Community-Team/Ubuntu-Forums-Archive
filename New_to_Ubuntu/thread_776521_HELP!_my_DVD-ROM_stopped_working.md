---
title: "HELP! my DVD-ROM stopped working"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by spectrevk on 2008-04-30
Powertop has left me with a rather odd problem. After making a change involving my DVD-ROM drive's power useage, my drive no longer works in Ubuntu. I think it's no longer loading the driver correctly. The error message says "Cannot mount volume." Details say:

mount: block device /dev/scd0 is write-protected, mounting read-only mount: wrong fs type, bad option, bad superblock on /dev/scd0, missing codepage or helper program, or other error In some cases useful info is found in syslog - try dmesg|tail or so

So I tried that, but dmesg|tail gives me this:

```
[ 3272.820421] psmouse.c: Failed to reset mouse on isa0060/serio1
[ 3272.834021] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3272.841706] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3272.844075] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3272.846269] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3272.856010] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 3272.856020] psmouse.c: issuing reconnect request
[ 3272.965843] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input10
[ 3272.997724] psmouse.c: Failed to enable mouse on isa0060/serio1
[ 3276.074717] UDF-fs: No fileset found

```

---

### Post by spectrevk on 2008-04-30
Really? Nobody knows how to fix this? I was hoping it was something simple, but I've been trying to get this thing fixed for days.

---

### Post by spectrevk on 2008-05-02
If anyone can just point me in the right direction for DVD-ROM configuration under Linux, that would be great.

---

### Post by Michael.Godawski on 2008-05-02
ok let's start somewhere.

Can you please post the output of these commands:

```
sudo lshw -C disk
cat /etc/fstab
```

---

### Post by spectrevk on 2008-05-02
> **Michael.Godawski said:**
> ok let's start somewhere.

Can you please post the output of these commands:

```
sudo lshw -C disk
cat /etc/fstab
```

Sure thing, and thanks for responding. 

sudo lshw -C disk gives me:
```
  *-disk                  
       description: ATA Disk
       product: FUJITSU MHV2080A
       vendor: Fujitsu
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 0083
       serial: NS90T632C59S
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000093f5
  *-cdrom
       description: DVD reader
       product: CDRW/DVD SCB5265
       vendor: PHILIPS
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: TH16
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1

```

cat /etc/fstab gives me:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=b7b1ad0f-15fd-46c4-a0d8-ed116b6e6df4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=2a17f341-2418-4639-8841-eb6e10e5d712 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

---

### Post by pcmantinker on 2008-05-03
Check out my reply to this post: [http://ubuntuforums.org/showthread.php?t=777805&highlight=fstab+cd+dvd&page=2](http://ubuntuforums.org/showthread.php?t=777805&highlight=fstab+cd+dvd&page=2)
It may help solve your problem.

---

### Post by spectrevk on 2008-05-05
Thanks for the tip, I'll give it a try. It's been really, really hard to get anyone to help me with this, and I've tried in multiple places. My previous ubuntu/linux issues have been resolved in like record time, I guess I got spoiled. :)

---

### Post by SunnyRabbiera on 2008-05-05
I just hope it didnt go sour, I had a DVD ROM drive that just decided to die without reason.

---

### Post by spectrevk on 2008-05-05
I don't think it died, but the current settings in my fstab don't match what's referred to in that thread at all. Here's what I've got:

```
UUID=2a17f341-2418-4639-8841-eb6e10e5d712 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

Is there a different way I should approach this?

---

