---
title: "running windows in ubuntu thru virtualbox"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by luckydeveloper on 2008-11-13
hi,

i actually want to run windows in ubuntu using virtual box solely bcos of MS office. 

when i run windows thru virtual box, will i be able to edit ms office docs and save it to my thumb drive .. will i be able to transfer files to/from cds/pen-drives to/from windows just as i would do in real machine

please help.
thanks

---

### Post by wizard10000 on 2008-11-13
Yup.  I've run both XP and Vista under virtualbox - you can transfer files to and from external media just like if Windows was the native OS.

Note that Vista under virtualbox is painfully slow unless you've got a relatively modern PC with a fair bit of RAM - it was almost unusable on my 2.8GHz test box with 1GB.  XP ran pretty well on the same machine.

I've never tried writing to optical disks from within virtualbox but don't see any reason why it wouldn't work  ;)

Good luck -

---

### Post by binbash on 2008-11-13
If you want usb support you have to go do virtualbox site and download the software from there.At repos there is OSE (open source edition) which does not support USB(But you can create windows share between linux and transfer files to ubuntu and use usb there).

---

### Post by wizard10000 on 2008-11-13
> **binbash said:**
> If you want usb support you have to go do virtualbox site and download the software from there.At repos there is OSE (open source edition) which does not support USB(But you can create windows share between linux and transfer files to ubuntu and use usb there).

I forgot about this - thanks for reminding me  :)

From virtualbox.org - [http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ)

> **USB on Ubuntu/Gutsy:** Ubuntu removed support for /proc/bus/usb/*. We will address this issue in the future. Until this, edit the script `/etc/init.d/mountdevsubfs.sh and activate the four lines around line 40 (Magic to make /proc/bus/usb work). Then execute

/etc/init.d/mountdevsubfs.sh start

    * **USB on Ubuntu/Intrepid:** Finally, the Ubuntu guys completely removed these lines. So you have to manually add them again:

      mkdir -p /dev/bus/usb/.usbfs
      domount usbfs "" /dev/bus/usb/.usbfs usbfs -obusmode=0700,devmode=0600,listmode=0644
      ln -s .usbfs/devices /dev/bus/usb/devices
      mount --rbind /dev/bus/usb /proc/bus/usb

      Add these lines to at the end of the start() function of /etc/init.d/mountdevsubfs.sh.
      Note that the udev permissions for the USB devices are still used. For instance, to access a USB disk you have to be member of the group disk. Execute

      /bin/ls -l /proc/bus/usb/*/*

      and check if you have write access to all desired USB devices.

      If you want to make all USB devices available for users member of the vboxusers group, apply the proposed change for USB on openSUSE. 

    * **USB on openSUSE:** Add the following entry to /etc/fstab:

      none  /proc/bus/usb  usbfs  auto,busgid=XXX,busmode=0775,devgid=XXX,devmode=0664  0  0

      Replace XXX by the group ID of the group vboxusers. You can determine this value by executing

      grep vboxusers /etc/group

      Of course, the current user should be member of that group. After the next reboot, there should be a directory /proc/bus/usb/ and the device entries below should be accessible by any user of the vboxusers group. 

    * If USB doesn't work, check your usbfs permissions. See "Troubleshooting" -> "Linux hosts" in the User Manual for a solution. 

---

