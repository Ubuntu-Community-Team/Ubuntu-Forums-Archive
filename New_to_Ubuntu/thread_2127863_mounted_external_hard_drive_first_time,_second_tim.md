---
title: "mounted external hard drive first time, second time, unable to mount"
date: 2013-03-21
forum: New to Ubuntu
---

### Post by baleeghr on 2013-03-21
Hi,
i mounted the hdd the first time, second time this error was shown

Error mounting /dev/sdb1 at /media/baleeghr/FreeAgent Drive: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sdb1" "/media/baleeghr/FreeAgent Drive"' exited with non-zero exit status 13: ntfs_mst_post_read_fixup_warn: magic: 0x43425355  size: 4096   usa_ofs: 1393  usa_count: 65535: Invalid argument
Actual VCN (0x100000efa1cf0500) of index buffer is different from expected VCN (0x3).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.


I need help urgently as i had backed up my whole hard drive

Regards,
baleegh

---

### Post by coffeecat on 2013-03-21
The error message tells you what might be wrong and what to do about it:

> **baleeghr said:**
> 
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows

An inconsistency in the NTFS filesystem is most likely. Plug the drive into a Windows system and run chkdsk.

---

### Post by baleeghr on 2013-03-21
thank you, i ahd not mentioned the hard disk was working fine on windows, until i ran it on ubuntu.

C:\Windows\system32>g:
The file or directory is corrupted and unreadable.

---

### Post by coffeecat on 2013-03-21
> **baleeghr said:**
> thank you, i ahd not mentioned the hard disk was working fine on windows, until i ran it on ubuntu.

As a point of information, accessing NTFS filesystems in Ubuntu is safe. I have been doing it for years. Did you "eject" or "safely remove" the drive before pulling out the USB cable? Just as in Windows, you can severely damage a filesystem by removing the drive while the system is still writing to it.

> C:\Windows\system32>g:
The file or directory is corrupted and unreadable.

That looks as though you simply tried to "cd" into your damaged hard drive. You need to run chkdsk from the command line. Or there is a GUI way. I'm going from memory here, because I don't use Windows very often, but if you right-click on your G: drive in Explorer (My Computer) there should be an option in the context menu to check and repair the filesystem.

---

### Post by baleeghr on 2013-03-21
yeeessss!!!!!! worked like a charm! and just for the record, i didnot safely eject in ubuntu. Did not know that was that much of a deal. Thank you again!

---

