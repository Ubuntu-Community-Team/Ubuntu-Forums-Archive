---
title: "Can't use external HDD anymore"
date: 2012-11-13
forum: New to Ubuntu
---

### Post by Green Zubat on 2012-11-13
Used to be able to use my WD MyPassport on Ubuntu perfectly, now it's gone weird all of a sudden. I tried to use it today, and I just got this weird error message pop up:

> Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

I took it out, and tried to use it again. The error didn't pop up this time, but I couldn't see the drive on my sidebar, either. I looked in the Home folder, and on the navigation sidebar where the other folders are listed was My Passport. Right-clicked on it and tried to Open, and an error popped up saying I didn't have permission to open it. I double clicked on the MyPassport tab in the navigation pane I just mentioned, and the following error popped up:

> Unable to mount My Passport

DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

When I right-clicked and tried the Safely Remove option, this error popped up:

> Unable to stop 1.0 TB Hard Disk

One or more partitions are busy on /dev/sdb


I'm using a 32-bit Dell Inspiron 1501 with Oneiric Ocelot/11.0, and have no idea what I'm doing [newbie], if that helps. Would really appreciate any help you can give.

---

### Post by Bashing-om on 2012-11-13
Green Zubat; Hi !

As the device is formated "ntfs" and native to windows, use the windows disk utilities to check the disk -as the original error advised-. 

Do you still have the lock -inuse- situation ?
A "lazy" un mount might release it:
```
umount -l /mnt/dev/sdb
```[INDENT]just try'n to help
[/INDENT]

---

### Post by Green Zubat on 2012-11-13
> **Bashing-om said:**
> Green Zubat; Hi !

As the device is formated "ntfs" and native to windows, use the windows disk utilities to check the disk -as the original error advised-. 

Do you still have the lock -inuse- situation ?
A "lazy" un mount might release it:
```
umount -l /mnt/dev/sdb
```[INDENT]just try'n to help
[/INDENT]

All I got when I tried the command you gave was:

> No command 'unmount' found, did you mean:
 Command 'umount' from package 'mount' (main)
 Command 'umount' from package 'loop-aes-utils' (universe)
unmount: command not found

Also, what windows disk utilities? I can't find any ... I tried the chkdsk /f thing the error advised like you said, but it didn't work :/

---

### Post by Bashing-om on 2012-11-13
Can't help ya much with windows ---been toooo many years ago// hopefully others will see and assist, who are current with windows.

But is important to get the drive un mounted !

on the device busy, roll sleeves up and go to work at lower level.
with the usb device connected, lets see what ubuntu sees:
```
sudo fdisk -l
```is /dev/sdb multi partitioned ? (easier to find if 1 partition on device)
```
sudo umount /dev/sdb1
``` (assuming 1 partition as sdb1)
looking for response "device is busy" then ->
```
sudo fuser -m /dev/sdb1
``` -> output is a process ID number
to see what the process is:
```
ps aux | grep 3322
``` (PID as example only substitute your PID)
```
kill -9 3322
``` (substitute your PID)
now the device should un mount, try and see:
```
sudo umount /dev/sdb1
```[INDENT]still try'n to help < == BDQ
[/INDENT]

---

### Post by newb85 on 2012-11-13
Um, actually I think the reason the drive didn't unmount is because the OP didn't copy the command correctly.  The command is "umount", not "unmount".  Thus, the error message:

```
No command 'unmount' found, did you mean:
Command 'umount' from package 'mount' (main)
Command 'umount' from package 'loop-aes-utils' (universe)
unmount: command not found
```

---

### Post by Mark Phelps on 2012-11-14
You typically get these messages when you simply unplug an external drive without "safely removing" it first.

Since you apparently have MS Windows (else, how would you have tried chkdsk?), plug it back in with Windows running, confirm you can access it, and this time, safely remove it.

Then, when you reconnect it in Ubuntu, it should be able to mount it OK.

---

