---
title: "howto change ntfs-3g file permissions"
date: 2007-08-24
forum: Outdated Tutorials &amp; Tips
---

### Post by xiota on 2007-08-24
When the packages ntfs-3g and gnome-mount are installed from the official repositories, ntfs partitions, listed under "computer:///" in nautilus, may be mounted by double-clicking them.  However, all directories and files have permissions set to 777.  I want files to have permissions set to 666 (no execute).

For most partition types, gnome-mount will honor options set at /system/storage/default_options/ in gconf.  I added noatime and noexec to most non-ntfs partition types, such as vfat, but noexec has no effect when used with ntfs-3g.

The ntfs-3g man page indicates that the mount option fmask=0111 will change the file permissions to 666 while leaving the directory permissions alone.  The fmask option is not recognized by gnome-mount, and adding it in the gconf will result in error messages from gnome-mount.  The related option umask is supported by gnome-mount, but will make navigating directories impossible.

gnome-mount uses the symbolic link, /sbin/mount.ntfs-3g, to mount partitions ntfs-3g partitions.  Replacing the symbolic link with a script that uses appropriate mount options should give the desired effects.

[INDENT]sudo unlink /sbin/mount.ntfs-3g
sudo nano /sbin/mount.ntfs-3g[/INDENT]

in nano, type:

[INDENT]#!/bin/bash
/usr/bin/ntfs-3g -o fmask=0111,noatime "$@"[/INDENT]

Files in ntfs partitions mounted through nautilus should now have permissions set to 666.  Don't forget to unmount partitions before removing external drives.

---

### Post by WSmart on 2008-04-15
I did this and now I can't mount.

---

