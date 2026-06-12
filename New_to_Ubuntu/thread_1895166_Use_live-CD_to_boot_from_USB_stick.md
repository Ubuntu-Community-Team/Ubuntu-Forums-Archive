---
title: "Use live-CD to boot from USB stick?"
date: 2011-12-14
forum: New to Ubuntu
---

### Post by KIAaze on 2011-12-14
Hi,

In case a computer does not support booting from a USB key, is it possible to somehow boot using a Live-CD, but then use the apps and data on the USB key? i.e. somehow use the Live-CD to boot from the USB key?

Maybe something like specifying the /usr, /etc and /home,... directories to be on the USB key before booting, or changing them after boot.

Any ideas?

I want to create a USB key I can use as OS when travelling (i.e. as some form of laptop replacement), but want to make sure I can also boot from it on systems not supporting USB boots.
I basically don't want to have to reinstall and reconfigure any apps at every boot and use the USB key as /home.

edit:
Ah, I think I found what I was looking for:
[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://reconstructor.apphosted.com/](https://reconstructor.apphosted.com/)
Will do some testing as soon as possible. :)

---

### Post by seawolf167 on 2011-12-14
You can use use [UNetBootin ]("http://unetbootin.sourceforge.net/")to create your Live USBs with optional persistence. As for booting off a cd then specifying the USB drive as the system, perhaps you want to use

```
man chroot
```

to change the root system to the USB drive?

---

### Post by mastablasta on 2011-12-14
you can use PLOP boot manager to boot from CD, another disk or even floppy disk to USB. when you boot with plop it will load a small menu askign which device oyu want to boot form and then it will boot from it. 
 
i used it to test new distributions on old machine that can't boot from USB, while burning a new LiveCD just for one live session is expencive.
 
you can stick linux on USB with unebootin or linuxliveusb.

---

