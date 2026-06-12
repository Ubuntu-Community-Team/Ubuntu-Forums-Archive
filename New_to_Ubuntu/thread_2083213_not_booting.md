---
title: "not booting"
date: 2012-11-11
forum: New to Ubuntu
---

### Post by Hasan55 on 2012-11-11
Hey there, please help me........i have recently downloaded salix-mate-13.37-source-dvd iso . and burn it in a usb installer but  it can not boot ........there is a problem showing...................

SYSLINUX 4.06 EDD 4.06 -PRE7 COPYRIGHT (C) 1994-2012 H. Peter Anvin et al

ERROR: NO Configuration file found 
No DEFAULT or UI configuration directive found

boot:_

---

### Post by Bashing-om on 2012-11-11
Hasan55; Hi !

All that pops into my mind is a "bad" copy ( you do have the cd drive set as 1st boot priority in bios, right?)
I would verify the checksum of the .iso file and then re-burn the .iso --make sure to burn as an "image" and NOT "data". Burn at the slowest speed possible.
[https://help.ubuntu.com/community/MakeALiveCD/DVD/](https://help.ubuntu.com/community/MakeALiveCD/DVD/)

[INDENT]hope this helps <== BDQ

[/INDENT]

---

### Post by oldfred on 2012-11-12
What version of USB creator did you use. Some old versions had bugs in syslinux.

Sometimes workaround work or just use one of the other USB creators like pendrive or unetbootin.

syslinux errors help/enter works:
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779)
Delete ui in syslinux.cfg
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382)
in the directory from "isolinux.cfg" to "syslinux.cfg"
Try replacing the file vesamenu.c32 on the USB disk drive with that one "/usr/lib/syslinux/vesamenu.c32" of Ubuntu Maverick system or use UNetbootin than works fine.
[http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/](http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/)

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

