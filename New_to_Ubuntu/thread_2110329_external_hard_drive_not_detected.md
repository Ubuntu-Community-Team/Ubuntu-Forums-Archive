---
title: "external hard drive not detected"
date: 2013-01-29
forum: New to Ubuntu
---

### Post by greyoracle on 2013-01-29
My external hard drive is not detected when I plug it into the USB port in Ubuntu.  When I dual boot windows 7 it says the drive is "corrupted and unreadable."  When I looked at solutions in windows I did find one program that retrieved files but wiped out the file names.  This was the best that I could find using google.  I was really hoping that there was something I could do in Ubuntu to access the hard drive before I'm forced to reformat it and wipe all the data.

thanks.

---

### Post by Bashing-om on 2013-01-30
greyoracle; Hi ! Welcome to the forum.

In ubuntu is  "disk utility", what is it's assessment of the disk's health ?
What is the problem disk's file system format ? If it is windows fat or ntfs, there is not a lot the ubuntu operating system can help with directly.

ext3/4 = ubuntu
ntfs = windows

[INDENT][INDENT]what are we working with 
[/INDENT][/INDENT]

---

### Post by papibe on 2013-01-30
Hi greyoracle. Welcome to the forums ):P

Most people refer to 'not detected' when it is not mounted automatically.

There may be recognized and not mounted because of the corruption problems. One way of checking for error would be to check the syslog a few seconds after you plug the disk:
```
tail /var/log/syslog
```
Alternatively, you could list the current USB devices by doing:
```
lsusb
```
Also you may check the list of disk devices before and after you plug the disk so you can see if it gets assigned a device name:
```
ls /dev/sd*
```

What kind of file system does the disk have?

You may run some repairs, but if it is a Windows format like NTFS or some kind of FAT, I would go with Windows tools to repair it.

Just a few thoughts. Let us know how it goes.
Regards.

---

### Post by Mark Phelps on 2013-01-30
Linux won't let you mount a filesystem that is corrupted -- to protect the file system against further damage.  So, if it a Windows filesystem, you will not be able to repair it from Linux.

The best file recovery app I've seen in Windows is RecoverMyFiles -- it's free to download and try, but you have to buy it to recover the files.  It's one of the few that actually retains the directory structure and filenames intact.

---

### Post by greyoracle on 2013-01-31
Disk utility recognizes the external hard drive but entries like location, write cache, and rotation rate are all dashed (blank).

It says the partition type is HPFS/NTFS (0x07)

under drive the device name is /dev/sdb
under volumes the device name is /dev/sdb1

Nothing is listed under lsusb for any kind of external hard drive.

If no one has any ideas I think I'm just going to format it since I have most of my data backed up anyway.

---

### Post by papibe on 2013-01-31
> **greyoracle said:**
> Disk utility recognizes the external hard drive but ...
There you go, detected but not enough information to display details or mount it.

As said before, using native Windows tools would give you better chances of repair/recover data from it.

Regards.

---

