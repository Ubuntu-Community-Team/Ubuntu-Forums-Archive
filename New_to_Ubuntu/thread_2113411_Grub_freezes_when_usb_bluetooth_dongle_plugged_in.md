---
title: "Grub freezes when usb bluetooth dongle plugged in"
date: 2013-02-07
forum: New to Ubuntu
---

### Post by benzodiaz on 2013-02-07
Hi all,

I am wondering if anyone knows the fix for this.  I did some searching and didn't find much...

I have my grub options set to quiet nosplash nolapic.

nolapic stops grub2 from freezing due to my integrated graphics.

Otherwise, with the dongle plugged in on boot, I get a black screen for a few minutes, then it'll boot to the grub screen.  If I unplug the usb bluetooth dongle at the black screen, it immediately goes to the grub.

I checked in the bios settings and usb is not set as a boot option at all.

Any idears?

If there is some other info that might help, please let me know.

Lubuntu 12.04

Thanks

---

### Post by Sealbhach on 2013-02-07
Strange. It does sound like your computer is trying to boot from the USB dongle, so it might not be a Linux or Grub issue but something prior to that.  You could look at the output of dmesg, it's sort of a running commentary of the startup process.

```
dmesg | grep usb
```

will look for mentions of "usb". To look at the whole thing from the start do

```
dmesg | less 
```

.

---

