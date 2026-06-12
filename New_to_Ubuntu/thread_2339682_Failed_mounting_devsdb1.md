---
title: "Failed mounting /dev/sdb1"
date: 2016-10-11
forum: New to Ubuntu
---

### Post by random.developer on 2016-10-11
I will be fast cause it's the 3rd time I'm writing this.
My PC = 1 SSD and 1 HDD
on SSD there's Windows 10 and Ubuntu 16.04
on HDD my files
HDD is 500GB
On Windows HDD=E:\
On Ubuntu HDD=/dev/sdb
On Ubuntu it says it is 272GB and cannot be mounted:

```
Error mounting system-managed device /dev/sdb2: Command-line `mount "/mnt/D2A0AEA1A0AE8B93"' exited with non-zero exit status 12: Failed to read last sector (976761538): Invalid argumentHINTS: Either the volume is a RAID/LDM but it wasn't setup yet,   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdb2': Invalid argument
The device '/dev/sdb2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```

If I fix it with sudo ntfs-fix /dev/sdb2 ---> On Windows it says E:\ is 253GB and full, I cannot run any file.

Images are after fixing sdb on Ubuntu

[IMG]http://i63.tinypic.com/4ptt2d.png[/IMG]

[IMG]http://i63.tinypic.com/2lcmr0l.png[/IMG]

If I fix the drive with chkdsk on Windows, the previous issue on Ubuntu appears.

HOW CAN I SOLVE IT????

---

### Post by Habitual on 2016-10-12
n/m. no coffee, yet.

---

### Post by random.developer on 2016-10-12
what?

---

### Post by SeijiSensei on 2016-10-12
You need to use Windows to completely repair an NTFS filesystem.  ntfsfix has only limited abilities.  From the manual page for ntfsfix ("man ntfsfix"):

> ntfsfix is a utility that fixes some common NTFS problems.  ntfsfix is NOT a Linux version of chkdsk.  It only repairs some fundamental NTFS inconsistencies, resets the NTFS journal file and schedules an NTFS  consistency check for the first boot into Windows.

---

### Post by oldfred on 2016-10-12
Windows mounts and keeps all NTFS partitions mounted when hibernated. You need to turn fast start up off as Linux NTFS driver will not normally mount hibernated partitions to prevent damage.

 Fast Startup off/hibernation - Windows 8 or 10 UEFI or BIOS boot.
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by random.developer on 2016-10-12
Thanks! I've recently formatted the partition and I'll try to reinstall Ubuntu, hoping it will work.

---

