---
title: "external hdd not showing up when plugged in"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by shortridge11 on 2008-10-10
I am running 8.04, and I have a 700gig external hdd.  When i plug it in to my box, nothing happens.  Whenever this usually happens, i go to partition editor (gparted) and see what sdx it is.  Then i use mount -t xxx /dev/sdx /media/temp and drag things in to that folder.  This worked in the past, but now it doesn't seem to be working.  Also, when it worked in the past it would only take a few gigs of files and then claim it was full when it had about 690gigs still free.  Any ideas why my box can't handle external hdds very well?

---

### Post by ashmew2 on 2008-10-11
Please post output of
```
cat /etc/fstab
```

---

### Post by amac777 on 2008-10-11
Also check your syslog for error messages after you plug it in.

```
tail /var/log/syslog
```

Also, that command for the syslog will tell you what SDX it is as well so you don't need to use gparted.

Also, I am not sure if your external HDD is USB, but I had a problem with a USB drive not being recognized about 50% of the time when plugging it in. On my USB drive, there are two USB connectors  - one is the main connector and the drive works when it is plugged in, the second connector is a smaller connector that is just for auxilary power. I found that I get better results from plugging in the auxilary power USB plug first and waiting a few seconds for the LED on the drive to come on before plugging in the main USB plug. Doing it this way, it seems to give the drive time to power up first and be ready to do the handshake when I plug in the main connector. Not sure if that would help in your case.

---

### Post by vanadium on 2008-10-11
I expect that your hard disk is formatted with the fat32 file system. Your file system needs to be checked and repaired.

Make sure your HD is connected and powered on

* Determine the device name of your external disk partition using the command ```
sudo blkid
```. One of the drives listed will be your external hdd. The first item on each line is a device name. Suppose your external disk is /dev/sdb1
* Check the file system. For this, the drive needs to be unmounted. Yours will be, but to be sure, issue the unmount command first, then chekc the disk
```

sudo umount /dev/sdb1
sudo fsck /dev/sdb1

```

Post the output here: it will tell what the file system is, and this information is needed to determine the command line options you need to provide to not only check, but also repair the disk.

A clean, healthy file system will be mounted automatically.

---

