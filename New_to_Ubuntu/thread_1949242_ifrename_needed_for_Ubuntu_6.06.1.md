---
title: "ifrename needed for Ubuntu 6.06.1"
date: 2012-03-29
forum: New to Ubuntu
---

### Post by GeorgePaul on 2012-03-29
I am trying to repair a Ubuntu 6.06.1 system. The root file system was corrupted and a number of files were deleted. One of the files that was deleted was /sbin/ifrename. /etc/rcS.d/S40ifrename refers to /sbin/ifrename and I'd like to get it. I tried aptitude install ifrename after editing /etc/apt/sources.lst to refer to old-releases.ubuntu.com instead of us.archive.ubuntu.com and security.ubuntu.com and got "No candidate version found for ifrename". How can I get the file /sbin/ifrename?

---

### Post by klytu on 2012-03-29
> **GeorgePaul said:**
> I am trying to repair a Ubuntu 6.06.1 system. The root file system was corrupted and a number of files were deleted. One of the files that was deleted was /sbin/ifrename. /etc/rcS.d/S40ifrename refers to /sbin/ifrename and I'd like to get it. I tried aptitude install ifrename after editing /etc/apt/sources.lst to refer to old-releases.ubuntu.com instead of us.archive.ubuntu.com and security.ubuntu.com and got "No candidate version found for ifrename". How can I get the file /sbin/ifrename?

According to the following link ifrename was made obsolete by the udev package in Ubuntu 6.06.1:

[https://lists.ubuntu.com/archives/kubuntu-users/2006-August/007841.html](https://lists.ubuntu.com/archives/kubuntu-users/2006-August/007841.html)

A description of the udev package indicates ifrename conflicts with it, so if you set up Ubuntu 6.06.1 and try to force installation of ifrename, part of your installation may break.

> Package: udev
Priority: important
Section: admin
Installed-Size: 804
Maintainer: Scott James Remnant <scott@ubuntu.com>
Architecture: i386
Version: 079-0ubuntu34
Replaces: hotplug, initramfs-tools (<< 0.040ubuntu1), ifrename
Depends: libc6 (>= 2.3.4-1), libselinux1 (>= 1.28), libsepol1 (>= 1.10), module-init-tools (>= 3.2.1-0ubuntu3), initramfs-tools (>= 0.40ubuntu30), grepmap (>= 1.1.0-1)
Conflicts: hotplug, ifrename
Filename: pool/main/u/udev/udev_079-0ubuntu34_i386.deb
Size: 238892
MD5sum: a86222d6450fa1faa995150a3358e060
Description: rule-based device node and kernel event manager
 udev is a collection of tools and a daemon to manage events received from
 the kernel and deal with them in user-space.  Primarily this involves
 creating and removing device nodes in /dev when hardware is discovered or
 removed from the system.
 .
 Events are received via kernel netlink messaged and processed according to
 rules in /etc/udev/rules.d, altering the name of the device node, creating
 additional symlinks or calling other tools and programs including those to
 load kernel modules and initialise the device.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

If think you really must have it, you should be able to find it in the archived Breezy main repository: 

[http://old-releases.ubuntu.com/ubuntu/dists/breezy/main/](http://old-releases.ubuntu.com/ubuntu/dists/breezy/main/)

---

