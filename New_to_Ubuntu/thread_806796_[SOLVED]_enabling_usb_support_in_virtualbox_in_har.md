---
title: "[SOLVED] enabling usb support in virtualbox in hardy"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by gameryoshi600 on 2008-05-25
can someone help me enable usb support for virtualbox in hardy

---

### Post by shifty_powers on 2008-05-25
assuming you don't have the ose version, which doesn't support it

[http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html](http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html)

worked perfectly for me ;)

---

### Post by signseeker on 2008-05-25
> **gameryoshi600 said:**
> can someone help me enable usb support for virtualbox in hardy

Doesn't it just 'work'? What specifically are you trying to do?

What OS are you trying to install? What 'settings' have you used for the virtual machine?

---

### Post by shifty_powers on 2008-05-25
> **signseeker said:**
> Doesn't it just 'work'? What specifically are you trying to do?

What OS are you trying to install? What 'settings' have you used for the virtual machine?

unfortunately, no, neither the ose, (open source editiom), or the normal sun edition support usb out of the box...

---

### Post by briandu on 2008-05-25
As per the link given do the following:

Enable USB
In a terminal type:
[COLOR=#3333FF]sudo gedit /etc/init.d/mountdevsubfs.sh [/COLOR]

You need to look for this section:
[COLOR=#009900]#[/COLOR]
[COLOR=#009900]# Magic to make /proc/bus/usb work[/COLOR]
[COLOR=#009900]#[/COLOR]
[COLOR=#009900]#mkdir -p /dev/bus/usb/.usbfs[/COLOR]
[COLOR=#009900]#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644[/COLOR]
[COLOR=#009900]#ln -s .usbfs/devices /dev/bus/usb/devices[/COLOR]
[COLOR=#009900]#mount --rbind /dev/bus/usb /proc/bus/usb[/COLOR]

And delete all the # shown, it should look exactly like this.

[COLOR=#009900]#Magic to make /proc/bus/usb work[/COLOR]

[COLOR=#009900]mkdir -p /dev/bus/usb/.usbfs[/COLOR]
[COLOR=#009900]domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644[/COLOR]
[COLOR=#009900]ln -s .usbfs/devices /dev/bus/usb/devices[/COLOR]
[COLOR=#009900]mount --rbind /dev/bus/usb /proc/bus/usb[/COLOR]

then reboot!

---

