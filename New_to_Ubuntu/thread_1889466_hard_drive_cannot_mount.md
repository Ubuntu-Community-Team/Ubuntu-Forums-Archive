---
title: "hard drive cannot mount"
date: 2011-12-01
forum: New to Ubuntu
---

### Post by jokkenmaster on 2011-12-01
hi there, I'm kinda new to ubuntu and have decided to wait with it and change back to windows 7 for the moment, only thing I want to do before that is transfer some files from the computer onto an external hard drive, but whenever it tries to mount it this error message comes up:
Error mounting: mount exited with exit code 12: Failed to read last sector (3907027119): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

What does this mean ? or put another way: how do I fix it?

---

### Post by deonis on 2011-12-01
You have a problem with your HDD. Try to go under windows and scan the file system. It should solve the problem.

---

### Post by BC59 on 2011-12-01
The external drive looks like having problems. From a Windows computer and from Windows Help & Support, type 'chkdisk' and run it.

---

### Post by jokkenmaster on 2011-12-01
Still doesnt work, so I'm going back to windows 7, and just download the files I couldn't transfer

---

### Post by BC59 on 2011-12-01
The problem with your external HDD has nothing to do with your decision. The problem is that to check a NTFS HDD for errors, you need Windows, because NTFS is the Windows file system.

---

### Post by deonis on 2011-12-01
Alternatively to avoid this problems in future you can format your HDD to ext* file system  and then everything will be fine except you will not be able to use Windows with it :). Do not listen to me listen to the Guys above :)

---

