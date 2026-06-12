---
title: "drive mount trouble"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by melrokz on 2008-08-15
I'm Melvin from cochin, India.
I've recently formatted 2 of my partitions as NTFS, but they are not mounted on startup on my Ubuntu 7.10. on taking Computer and then clicking the drive, i get a message 'Access to this disk is restricted to system admin due to security reasons. Enter your password to continue.' Any way to mount the partitions automatically on startup as they previously used to mount?

---

### Post by dca on 2008-08-15
This may help:
 
[http://ubuntuguide.org/wiki/Ubuntu:Hardy#automountntfs](http://ubuntuguide.org/wiki/Ubuntu:Hardy#automountntfs)
 
...nevermind, I can't find it there anymore...
 
try:
 
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)
 
...then add to /etc/fstab

---

### Post by dca on 2008-08-15
If they used to automount prior w/o any other interaction it could've been they were formatted as FAT32.  NTFS takes a little patience and work...

---

### Post by dca on 2008-08-15
This how-to looks pretty good...
 
[http://thetechnut.wordpress.com/2008/06/18/automounting-ntfs-drives-in-ubuntu-804/](http://thetechnut.wordpress.com/2008/06/18/automounting-ntfs-drives-in-ubuntu-804/)

---

