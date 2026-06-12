---
title: "Mounting Windows NTFS Network Drives in Ubuntu"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by vnet81 on 2008-11-10
I need help in getting pointed in the right direction on how to mount a few NTFS network drives to my linux box here at work.  Samba has been installed, I just need to know what to do at this point.  Any and all help will be much appreciated!!

Also:  I am using Mint as my linux distribution, which is based off Ubuntu.

---

### Post by betes on 2008-11-10
Does this help?

[http://www.arsgeek.com/2006/09/25/ubuntu-tricks-how-to-mount-your-windows-partition-and-make-it-readwritable/](http://www.arsgeek.com/2006/09/25/ubuntu-tricks-how-to-mount-your-windows-partition-and-make-it-readwritable/)

---

### Post by prshah on 2008-11-10
> **vnet81 said:**
> I need help in getting pointed in the right direction on how to mount a few NTFS network drives to my linux box here at work.  Samba has been installed, I just need to know what to do at this point.  Any and all help will be much appreciated!!


> **betes said:**
> Does this help?
[http://www.arsgeek.com/2006/09/25/ubuntu-tricks-how-to-mount-your-windows-partition-and-make-it-readwritable/](http://www.arsgeek.com/2006/09/25/ubuntu-tricks-how-to-mount-your-windows-partition-and-make-it-readwritable/)

With reference to the above article: First off, he wants to mount a _network_ drive not a local drive, which is what the article talks about . Secondly, that article is a bit dated; fuse is now available by default and does not need to be apt-"got" as is ntfsprogs.

For mounting a network drive, irrespective of the underlying file system (FAT, FAT32, NTFS) you have to use CIFS.

A typical command will be ```
sudo mount -t cifs //192.168.1.7/shared /mnt -o defaults,rw,gid=46
``` Ensure that the user is a member of group plugdev (Each user is so by default on Ubuntu).

---

### Post by Nepherte on 2008-11-10
You don't need samba to mount network shares by the way. You do need samba if you want to share your own maps to a windows network.

---

### Post by prshah on 2008-11-10
> **Nepherte said:**
> You don't need samba to mount network shares by the way.

Unfortunately, you do. the mount.cifs command is part of the samba suite, and cannot be accessed independently.

Prior to 8.04, one can use smbfs, which was independent of the samba suite, but this is now deprecated and replaced with cifs.

---

### Post by Nepherte on 2008-11-11
> **prshah said:**
> Unfortunately, you do. the mount.cifs command is part of the samba suite, and cannot be accessed independently.

Prior to 8.04, one can use smbfs, which was independent of the samba suite, but this is now deprecated and replaced with cifs.
Ah, didn't know about cifs being dependent of samba.

---

