---
title: "Grsync can't see network drive?"
date: 2013-01-12
forum: New to Ubuntu
---

### Post by mapes12 on 2013-01-12
- Ubu 12.04LTS and installed Grsync
- Ubu machine is connected to BTHomeHub router via ethernet
- Win7 machine connected to the same router via ethernet
- NTFS data partition set up on Win7 machine with sharing enabled
- Ubu machine can see it fine in Network Places
- But when I try to locate the same folder when configuring Grsync via the destinations setting it does not show any network drives?

I've Googled this for ages and got no where.

---

### Post by gordintoronto on 2013-01-12
You just need to do this once: make sure your file manager is set to display hidden files. In your Home folder, scroll down to .gvfs and right-click on it. Select "Make Link." The Link will not be hidden, drag it onto your desktop.

After making sure the drive is mounted, from your application's save dialogue navigate to Desktop, select "Link to .gvfs" and the network drive will appear in it. One more double-click and you can save.

---

### Post by Paqman on 2013-01-12
You can also mount the network share to any folder you want by creating an entry in /etc/fstab that mounts it automatically at boot. I find the way Gnome mounts things to a weird location in .gvfs to be a bit of a pain, and prefer to mount my shares somewhere a bit more accessible.

[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

### Post by mapes12 on 2013-01-13
Thanks guys. With your help I've got it working. Once my first backup has completed I'm going to take a look a [Gigolo]("http://www.uvena.de/gigolo/") for future mounting configs.

---

