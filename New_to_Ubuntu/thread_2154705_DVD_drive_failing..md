---
title: "DVD drive failing."
date: 2013-06-15
forum: New to Ubuntu
---

### Post by r3bol on 2013-06-15
Hi, I've been happily watching a dvd box set on ubuntu 12.04, but suddenly my drive has failed on me. I can still hear it trying to access the DVDs, but it doesn't 'spin up' and detect the drive in my drive view. 
I've searched through various threads and it seems I've got all the things I need installed. For example: 
sudo apt-get install libdvdnav4 libdvdread4 gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
and also libdvdcss2. 

I also installed and run:
```
asdf@asdf:~$ sudo regionset
regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive.
```

Does anyone have any suggestions?

Here are my details: 

```
asdf@asdf:~$ sudo lshw -C disk
[sudo] password for asdf: 
  *-cdrom                 
       description: DVD-RAM writer
       product: DVDRAM GSA-T20N
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: WW01
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
  *-disk
       description: ATA Disk
       product: WDC WD1200BEVS-2
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 01.0
       serial: WD-WXE907844187
       size: 111GiB (120GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=7ab852fc
  *-disk
       description: SCSI Disk
       product: STORAGE DEVICE
       vendor: Generic
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/sdb
       version: 9412
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdb


asdf@asdf:~$ sudo lshw | grep cdrom
           *-cdrom
                logical name: /dev/cdrom
                   logical name: /dev/cdrom
asdf@asdf:~$ 

```

Thanks :)

---

### Post by newbie-user on 2013-06-17
Hardware issue perhaps. Have another DVD drive to test with?

---

### Post by monkeybrain2012 on 2013-06-17
Hardware failure I would guess. Since you have been watching dvd happily before you had all the required software installed and it had nothing to do with region code.

---

### Post by r3bol on 2013-06-17
Thanks, I guess I could test it by running a live distro.

---

### Post by coldraven on 2013-06-17
Try cleaning the lens. Even the tiniest speck of dust or tobacco smoke will stop it working, especially on dual-layer DVDs.

---

### Post by r3bol on 2013-06-17
> **coldraven said:**
> Try cleaning the lens. Even the tiniest speck of dust or tobacco smoke will stop it working, especially on dual-layer DVDs.
Well, what do you know! I gave the lens a clean, and it did the job. 
I kind of feel a little stupid now. Sorry folks, and thanks for the support.

---

