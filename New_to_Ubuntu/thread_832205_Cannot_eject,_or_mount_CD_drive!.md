---
title: "Cannot eject, or mount CD drive!"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by linkmaster03 on 2008-06-17
I can't eject my CD drive, or even (un)mount it! I am on a Toshiba Satellite A135 laptop. It's a Matshita drive.

```
brad@brad-laptop-ubuntu:~$ sudo mount /media/cdrom0
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

brad@brad-laptop-ubuntu:~$
```

```
brad@brad-laptop-ubuntu:~$ dmesg | tail
[ 8050.280280] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[ 8086.738482] UDF-fs: No partition found (1)
[ 8086.740501] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[ 8459.083440] UDF-fs: No partition found (1)
[ 8459.085297] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[ 8604.053597] npviewer.bin[18070]: segfault at 00000018 eip b7a7cf42 esp bfbe0810 error 4
[ 8660.387380] UDF-fs: No partition found (1)
[ 8660.388416] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[ 8669.821780] UDF-fs: No partition found (1)
[ 8669.825066] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
brad@brad-laptop-ubuntu:~$ 

```

---

### Post by _sphinx_ on 2008-06-17
Don't you think it should be ```
sudo umount /media/cdrom0

```

---

### Post by linkmaster03 on 2008-06-17
I have no media in there. I had to use the paperclip method to take it out.

```
brad@brad-laptop-ubuntu:~$ sudo umount /media/cdrom0
umount: /media/cdrom0: not mounted
brad@brad-laptop-ubuntu:~$ 
```

I still can't insert CDs, or burn, or anything.

---

### Post by linkmaster03 on 2008-06-17
ImgBurn on Windows burns fine:

[img]http://img117.imageshack.us/img117/7729/jun17060605pmnr3.png[/img]

---

### Post by Fixman on 2008-06-17
post /etc/fstab.

---

### Post by linkmaster03 on 2008-06-17
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=d4279e97-5eea-40f4-8f91-07e4c5f89b45 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=958778d8-bb89-448a-8a2c-488d04662249 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

---

### Post by linkmaster03 on 2008-06-19
Anyone?

---

### Post by Dedoimedo on 2008-06-19
Hi,

You are trying to mount the cd-rom, but you did not specify the mount point.

Try this:

cd /mnt
sudo mkdir cd

sudo mount /dev/scd0 /mnt/cd

See if this helps. Similarly, unmount the mount point:

sudo umount /mnt/cd

If this does not work, try also:

sudo mount -t udf /dev/scd0 /mnt/cd OR
sudo mount -t iso9660 /dev/scd0 /mnt/cd

In general, your fstab does specify that cd should be mounted to /media/cdrom0, but not automatically (noauto) option.

Try my solution first, see if it works.

Then, try editing the fstab:

sudo cp /etc/fstab /etc/fstab-backup

Then, change the noauto to auto. Save file. Remount all:

sudo mount -a

Then, insert CD and see if anything changes. If nothing happens, try rebooting then see if anything changes. If not, post back again.

Dedoimedo

---

### Post by linkmaster03 on 2008-06-19
```
brad@brad-laptop-ubuntu:/mnt$ sudo mount /dev/scd0 /mnt/cd
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: you must specify the filesystem type
brad@brad-laptop-ubuntu:/mnt$ 

```

```
brad@brad-laptop-ubuntu:/mnt$ sudo mount -t udf /dev/scd0 /mnt/cd
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

brad@brad-laptop-ubuntu:/mnt$ 

```

```
brad@brad-laptop-ubuntu:/mnt$ sudo mount -t iso9660 /dev/scd0 /mnt/cd
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

brad@brad-laptop-ubuntu:/mnt$
```

```
brad@brad-laptop-ubuntu:/mnt$ dmesg | tail
[  552.211287] Buffer I/O error on device sr0, logical block 2
[  552.211293] Buffer I/O error on device sr0, logical block 3
[  552.211299] Buffer I/O error on device sr0, logical block 4
[  552.211305] Buffer I/O error on device sr0, logical block 5
[  552.211311] Buffer I/O error on device sr0, logical block 6
[  552.211317] Buffer I/O error on device sr0, logical block 7
[  552.213019] Buffer I/O error on device sr0, logical block 0
[  552.213050] Buffer I/O error on device sr0, logical block 1
[  602.888605] UDF-fs: No partition found (1)
[  623.428654] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
brad@brad-laptop-ubuntu:/mnt$ 

```

```
brad@brad-laptop-ubuntu:/mnt$ sudo mount -a
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

brad@brad-laptop-ubuntu:/mnt$ 
```

Nothing happens when I put in a CD. No detection by k3b, can't view CD in Nautilus...


No change on reboot.

---

### Post by linkmaster03 on 2008-06-20
Maybe the new kernel update will help... I'll try later.

---

### Post by Dedoimedo on 2008-06-20
Hi,

Do you know what format this CD is? Could it be corrupted?

What do you get if you run: cat /proc/interrupts ? Do you see any conflicts between the CD drive and any other hardware?

Dedoimedo

---

### Post by linkmaster03 on 2008-06-20
The CDs work fine on Windows. But Ubuntu can't even read my empty CDs or burn to them.

```
brad@brad-laptop-ubuntu:~$ cat /proc/interrupts
           CPU0       CPU1       
  0:    4516239          0   IO-APIC-edge      timer
  1:      19591          0   IO-APIC-edge      i8042
  8:          7          0   IO-APIC-edge      rtc
  9:     273334          0   IO-APIC-fasteoi   acpi
 12:     215580          0   IO-APIC-edge      i8042
 14:      85396          0   IO-APIC-edge      libata
 15:       2607          0   IO-APIC-edge      libata
 16:     906038          0   IO-APIC-fasteoi   ohci1394, wifi0
 17:    1406128          0   IO-APIC-fasteoi   uhci_hcd:usb4, yenta, i915@pci:0000:00:02.0
 18:      44434          0   IO-APIC-fasteoi   uhci_hcd:usb3, tifm_7xx1
 19:          2          0   IO-APIC-fasteoi   uhci_hcd:usb1, ehci_hcd:usb5
 20:          0          0   IO-APIC-fasteoi   uhci_hcd:usb2, sdhci:slot0
 21:     214819          0   IO-APIC-fasteoi   HDA Intel
220:          0          0   PCI-MSI-edge      eth0
NMI:          0          0   Non-maskable interrupts
LOC:     829920    2814982   Local timer interrupts
RES:    5959851    6236970   Rescheduling interrupts
CAL:        210        295   function call interrupts
TLB:       1605       2116   TLB shootdowns
TRM:          0          0   Thermal event interrupts
SPU:          0          0   Spurious interrupts
ERR:          0
MIS:          0
brad@brad-laptop-ubuntu:~$ 
```

---

### Post by linkmaster03 on 2008-06-22
Anyone? :( :popcorn: to the one who helps me fix it.

---

### Post by linkmaster03 on 2008-06-24
Hmm. There must be a way to get this working.

---

### Post by linkmaster03 on 2008-06-28
Hello? :(

---

### Post by tipiglen on 2008-07-04
```

sudo lshw -C disk

```
you should get a listing including something like this:
> 
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

try changing the relevant line in your fstab to show the FIRST logical name in the list. Mine was showing /dev/scd0 and after I changed that to /dev/cdrom1 (as above) everything worked fine again.

Best of luck
ed

---

### Post by linkmaster03 on 2008-07-06
No help. :(

New fstab (replaced /dev/scd0 to /dev/cdrom in last line)

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=d4279e97-5eea-40f4-8f91-07e4c5f89b45 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=958778d8-bb89-448a-8a2c-488d04662249 none            swap    sw              0       0
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

```
brad@brad-laptop-ubuntu:~$ sudo lshw -C disk
  *-disk
       description: ATA Disk
       product: TOSHIBA MK1637GS
       vendor: Toshiba
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: DL03
       serial: 6738T0BST
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=155e88b5
  *-cdrom
       description: DVD-RAM writer
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=ready
brad@brad-laptop-ubuntu:~$
```

---

### Post by jimbob on 2008-07-06
Post the output of:

cd /dev
ls -al cdr*

My original installation only had cdrom2 and cdrom3 specified.  This caused my problems with some applications.

I had to change/add some links in /etc/rc.local to get things to work.

---

### Post by tipiglen on 2008-07-06
```
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

try 
```
/dev/cdrom       /media/cdrom0   udf,iso9660 -o users,noauto,exec 0       0
```

Change user to users.  It may be that only root (who mounted it) can use it.  Also it might be worth the -o which signifies options other than defaults....You might also just try defaults (all by itself in the field)

Best of luck
ed

---

### Post by mc4man on 2008-07-06
What is sorta interesting is this line from lshw
> configuration: status=ready
That's indicating media in the drive but it's not complete
These are 4 basic possibilities
# empty
> configuration: ansiversion=5 status=open
#blank cd/dvd ; audio cd 
> configuration: ansiversion=5 status=ready
 *-medium
    physical id: 0
    logical name: /dev/cdrom

# data dvd ; dvd video
>  configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom0
# data cd
>  configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom0

Did you have some media in the drive when you ran the command? Yours is same as to be expected with blank cd/dvd or audio cd, but no physical id,logical name or ansiversion
You may want to ck. in /etc/udev/rules.d/ 70-persistent-cd.rules and see if your drive is listed twice (longshot)

---

### Post by linkmaster03 on 2008-07-07
I had nothing in the drive when I ran the command. Now, since I put an empty DVD-R in the drive, this shows whether media is in or not:

```
brad@brad-laptop-ubuntu:~$ sudo lshw -C disk
  *-disk
       description: ATA Disk
       product: TOSHIBA MK1637GS
       vendor: Toshiba
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: DL03
       serial: 6738T0BST
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=155e88b5
brad@brad-laptop-ubuntu:~$ 
```

```
brad@brad-laptop-ubuntu:/dev$ cd /dev
brad@brad-laptop-ubuntu:/dev$ ls -al cdr*
ls: cannot access cdr*: No such file or directory
brad@brad-laptop-ubuntu:/dev$
```

---

### Post by jimbob on 2008-07-08
Your /dev/cdr* entries should look like this:

root@HKDE:/dev# ls -al cdr*
lrwxrwxrwx 1 root root 4 2008-07-08 07:56 cdrom -> scd1
lrwxrwxrwx 1 root root 4 2008-07-08 07:56 cdrom1 -> scd0
lrwxrwxrwx 1 root root 4 2008-07-08 07:56 cdrw -> scd1
 
You can try adding them in manually if you want making sure you know which one is associated with which hardware (scdx) device:

ln -s scd0 cdrom1   (etc ...)

---

### Post by linkmaster03 on 2008-07-10
The drive is appearing on lshw again, so it's back to "normal".

```
brad@brad-laptop-ubuntu:/dev$ ls -al cdr*
lrwxrwxrwx 1 root root 4 2008-07-10 12:30 cdrom -> scd0
lrwxrwxrwx 1 root root 4 2008-07-10 12:30 cdrw -> scd0
brad@brad-laptop-ubuntu:/dev$   
```

---

