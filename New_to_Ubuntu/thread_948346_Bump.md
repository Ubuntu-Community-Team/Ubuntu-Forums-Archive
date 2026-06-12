---
title: "Bump"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by L Campbell on 2008-10-15
How do I get my Iomega DVD to work?
I have an Iomega 'Super DVD' R/RW model #31367200 which I am hoping to get operating on my PC with 8.04. After doing a couple of searches, it appears that this is NOT Iomega's latest version of this machine and I didn't find any information about his model number.

It is connected to my 'puter and functions to the point that the drawer opens and closes. Also, I can feel a minute vibration, as if the DVD inside is spinning up.

When I go to Places > Computer the Computer – File browser opens and I see the icon for my Iomega but when I click on it, all I get is this message:-

Unable to mount location.
No media in drive.

I have tried this with a Knoppix DVD and a Live Ubuntu CD, all with the same result.

If you have a suggestion as to what I should try next, I would appreciate it.

TIA.

---

### Post by philinux on 2008-10-15
With  thread titles like that you wont get far. Please use a proper title in future.
Whats wrong with using

How do I get my Iomega DVD to work?

As a title.

---

### Post by hyper_ch on 2008-10-15
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

---

### Post by L Campbell on 2008-10-15
> **philinux said:**
> With  thread titles like that you wont get far. Please use a proper title in future.
Whats wrong with using

How do I get my Iomega DVD to work?

As a title.


Your point is well taken but I have been using, "How do I get my Iomega DVD to work?" for 2 days and not had a single reply.

---

### Post by sisco311 on 2008-10-15
open a terminal and post the output of:
```
sudo lshw -C disk
```and
```
cat /etc/fstab
```

---

### Post by philinux on 2008-10-15
> **L Campbell said:**
> Your point is well taken but I have been using, "How do I get my Iomega DVD to work?" for 2 days and not had a single reply.

It sometimes happens I'm afraid. You would have been better bumping your original thread. Quite right too after say 24 hours.

What does 

[FONT=Courier New]lsusb [/FONT]

show when it's plugged in?

---

### Post by L Campbell on 2008-10-15
> **sisco311 said:**
> open a terminal and post the output of:
```
sudo lshw -C disk
```and
```
cat /etc/fstab
```

Hi, thanks for your interest.

qwer@qwer-desktop:~$ sudo lshw -C disk
  *-disk                  
       description: ATA Disk
       product: WDC WD800AB-22CB
       vendor: Western Digital
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 04.0
       serial: WD-WMAA51715622
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000b5496
  *-cdrom:0
       description: CD-R/CD-RW writer
       product: CD-RW GCE-8400B
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.06
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 status=open
  *-cdrom:1
       description: DVD reader
       product: DVD-ROM DDU1615
       vendor: SONY
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: GYS1
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=open
  *-cdrom
       description: DVD writer
       product: DVDRW SOHW-1633S
       vendor: LITE-ON
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/cdrom2
       logical name: /dev/dvd2
       logical name: /dev/scd2
       logical name: /dev/sr2
       version: BS01
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: status=open



************************************
qwer@qwer-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9037a3b5-8ef7-41dd-a427-1b257451e283 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ac576f2b-b391-424d-92e8-1e95ef845fe6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
qwer@qwer-desktop:~$

---

### Post by L Campbell on 2008-10-15
> **philinux said:**
> It sometimes happens I'm afraid. You would have been better bumping your original thread. Quite right too after say 24 hours.

What does 

[FONT=Courier New]lsusb [/FONT]

show when it's plugged in?

qwer@qwer-desktop:~$ lsusb 
Bus 004 Device 003: ID 059b:0251 Iomega Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 001 Device 001: ID 0000:0000  
qwer@qwer-desktop:~$

---

### Post by sisco311 on 2008-10-15
edit the fstab 
```
gksu gedit /etc/fstab
```and add this line:
> /dev/scd2 /media/cdrom2 udf,iso9660 user,noauto,exec,utf8 0 0

create the mount point:
```
sudo mkdir /media/cdrom2
```

---

### Post by L Campbell on 2008-10-15
> **sisco311 said:**
> edit the fstab 
```
gksu gedit /etc/fstab
```and add this line:


create the mount point:
```
sudo mkdir /media/cdrom2
```

Thanks, I did this and, as far as I can tell, it went smoothly.

Unfortunately I am still getting the same error message:-

"Unable to mount location."
"No media in drive."

I have tried this with a Knoppix DVD and a Live Ubuntu CD, all with the same result. 

Kind regards.

---

