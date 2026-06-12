---
title: "External hdd (vfat): set read/write permissions and visibility on Windows network?"
date: 2012-09-16
forum: New to Ubuntu
---

### Post by dvrs on 2012-09-16
Hi,

1. Is it possible to ensure that an external (usb) HDD formatted as VFAT is mounted with read & write permissions? If yes how do I ensure that the permissions are permanent (i.e. remains upon restart of the system)?

2. I also want to share the HDD on my home Windows network via Samba (with read/write permissions) - I am the only one accessing my home network so 777 permissions is not a problem ;-). I assume as long as the permissions have been set correctly for the device I can just share it via an appropriate line in smb.conf - or is there anything else I need to think about?

Thanks,
M

---

### Post by marinara on 2012-09-16
it's not VFAT 
[http://en.wikipedia.org/wiki/File_Allocation_Table#Nomenclature](http://en.wikipedia.org/wiki/File_Allocation_Table#Nomenclature)

the normal way to mount a disk installed in your system, is using your /etc/fstab file

if you don't have the disk installed, and you want to avoid errors, you might mount it with a script when you boot.

also, a question, are you ever mounting the drive as read-only?  Lubuntu?

sorry can't help w/ the Samba

---

### Post by dvrs on 2012-09-17
Ok thanks for the clarification. I guess I'm asking as the system is mounting the USB HDD automatically. I can write to the disk, but have not been able to share it via Samba (so I can access it from my Win7 machine).

Trying to mount via fstab seems to lead to problems (system generates some errors and doesn't boot - tells me /dev/sdda1 is not ready or something similar).

Any tips from anyone?

Thanks,
M

---

