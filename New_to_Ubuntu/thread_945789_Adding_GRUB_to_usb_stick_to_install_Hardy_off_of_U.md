---
title: "Adding GRUB to usb stick to install Hardy off of USB"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by gilforsyth on 2008-10-12
My laptop has no functioning cdrom, so I install ubuntu off of a usb stick.  I was trying to reinstall hardy from a usb stick, with my grub file edited to allow booting from usb, a la

```
title   usb
root    (hd1,0)
makeactive
chainloader +1
```
which worked fine, except for whatever reason, the install had an I/O error and failed and restarted.  I used unetbootin to setup the usb stick as I have in the past without error.  

So, my question.  The install from usbstick got far enough to format / partition and, consequently, my grub config.  Can anyone tell me how to install grub onto the stick so that I can boot back into the installer from USB?

Thanks

---

