---
title: "apt (et. al.) ignoring CD-ROM"
date: 2012-12-16
forum: New to Ubuntu
---

### Post by GordThompson on 2012-12-16
*In trying to get a better idea of why so many new users have network connectivity problems here is my experience:*

I have an Inspiron 1720 notebook with a Broadcom BCM4312 wireless adapter. When I boot from my 12.04 Desktop DVD and choose "Try Ubuntu" (Live CD) I see a message that says "Additional Drivers" are needed, so I click on the corresponding status bar icon, Ubuntu "downloads" the driver (copies it from the DVD) and my wireless adapter works.

When it came time to do the actual install I chose "Install Ubuntu" and purposely left the "Install this third-party software" box unchecked (because that is the default). The install proceeds and eventually I am told to restart. After I do that, the wireless adapter doesn't work.

"Okay, fair enough, I'll just copy the driver from the DVD" I sez, so I put the DVD back into the drive, launch Ubuntu Software Centre, choose **Edit > Software Sources...** and tick the box beside

Installable from CD-ROM/DVD
[x] CD-ROM with Ubuntu 12.04 'Precise Pangolin'

I close Ubuntu Software Centre, then go to **System Settings > Hardware > Additional Drivers** and I see the familiar dialog from the Live CD session listing the "Broadcom STA wireless driver". I click the "Activate" button and after a few seconds I get an error message saying

Sorry, installation of this driver failed.
Please have a look at the log file for details: /var/log/jockey.log

So I look in the log file and after almost 350 lines (mostly DEBUG messages) I see

```
Failed to fetch cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)]/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6.1_i386.deb File not found
```The file is there...

```
gord@pingu:~$ ls -l /media/Ubuntu\ 12.04.1\ LTS\ i386/pool/restricted/b/bcmwl/
total 1175
-r--r--r-- 1 gord gord 1202416 Apr 23  2012 bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6.1_i386.deb
```...but the Additional Drivers app won't read it.

Furthermore, apt-get refuses to read the "CD-ROM" as well:

```
gord@pingu:~$ sudo apt-get update
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise InRelease
...
```I went back into the Ubuntu Software Centre to double-check and yes, the "CD-ROM..." is still selected.

So what's the magic incantation to get apt, etc., to actually *use *the "CD-ROM"?

---

### Post by GordThompson on 2012-12-17
Never mind. After more searching I found this exact issue in a bug report from over two years ago:

[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/630519](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/630519)

Status: New
Importance: Undecided
Assigned to: Unassigned

Fail.

---

