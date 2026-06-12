---
title: "Ubuntu Server 14.04 fails to boot within VSphere"
date: 2016-10-26
forum: New to Ubuntu
---

### Post by brox18 on 2016-10-26
Hi,

Essentially, the issue we have is the failure of standard Ubuntu Server 14.04 installs boot due to a disk failure (all VM's have since been shifted to a new disk) on the back end causing some form of file corruption that placed all our servers into read only mode. If any of these machines are shutdown, they never reboot fully again.

We have access to the GRUB boot menu, file recovery mode and rescue mode through booting from a virtual CD. We can get root shell access and are able to view all the files on the system but make no edits (read-only mode).

We have tried to manually mount the filesystem as read/write using '*mount -o remount, rw /' *but this failed as well as use a number of other recovery options.
Here's a group of images displaying the current standard boot process, it does not get any further than shown in the last image.
[http://imgur.com/a/aY7yQ](http://imgur.com/a/aY7yQ)

If anyone can put us noobs in the right direction to solve this, it would be hugely appreciated. Happy to provide any further info if I can.


Thanks!

---

