---
title: "Can't create new folder or file on USB drive"
date: 2018-02-15
forum: New to Ubuntu
---

### Post by neovich on 2018-02-15
I tried to create on usb drive new folder and couldn't have done it, had got error:
[COLOR=#ff0000]Error creating directory: Read-only file system

[/COLOR][ATTACH=CONFIG]278533[/ATTACH]

---

### Post by TheFu on 2018-02-15
If the file system is mounted read-only, that will stop all writes. Fix that mount.

Try, in a terminal, 
```
sudo mount {/device/path/to/flash-drive} /mnt
```
The device/path will be shown at the bottom of the output from 'dmesg' command, a few seconds after the USB drive is plugged in. Something like /dev/sdg1 is likely, but not that.

You might want to add some options if the file system isn't a Linux one, so that your userid can write to the mounted storage.  For NTFS and FAT32 (vfat) file systems, the user and group permissions can only be set at *mount* time (well, not exactly true, but setting up the mapping is something nobody does - and I mean NOBODY).

You can check whether a mount is read-only or read-write using the 'mount' command. Look for 'ro' or 'rw' in the list next to the specific mount.

---

### Post by neovich on 2018-02-17
Problem was broken flash drive. there was fat32 file system and when I did in windows ```
chdisk \f :e
``` this helped and I could have reached my disk and write there something but big folders with many files couldn't have copied anyway. Then  I wholly formatted flash in windows and set up file system NTFS and this is helped. Now can copy big and small folders and very fast.

---

### Post by neovich on 2018-02-18
And this is didn't help, Flash drive is broken.

---

