---
title: "Persistent Ubuntu settings not being saved"
date: 2012-07-23
forum: New to Ubuntu
---

### Post by harshilsharma63 on 2012-07-23
Hi, I've used Universal USB Installer to create a live Ubuntu 12.04 drive on a 7 GB partition of my 500 GB Seagate external hard drive. I set a 3.26 GB persistent file size in Universal Usb Installer and the 'casper-rw' file was created. However, none of the settings which I change in Ubuntu are being saved- these settings include wallpaper, mouse sensitivity, mobile broadband connection etc.. Why is it that even after creating a Persistent file, the settings are not being saved and what is it's solution?

---

### Post by bobsan on 2012-07-23
> **harshilsharma63 said:**
> Hi, I've used Universal USB Installer to create a live Ubuntu 12.04 drive on a 7 GB partition of my 500 GB Seagate external hard drive. I set a 3.26 GB persistent file size in Universal Usb Installer and the 'casper-rw' file was created. However, none of the settings which I change in Ubuntu are being saved- these settings include wallpaper, mouse sensitivity, mobile broadband connection etc.. Why is it that even after creating a Persistent file, the settings are not being saved and what is it's solution?

FAT only supports up to 4 G. Maybe your value is too high. Since you are using the Universal Usb Installer you are on Windows. If you have a big usb drive you may try LILI which allows you to multiboot.[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

---

### Post by C.S.Cameron on 2012-07-23
Confirm that your text.cfg, (or txt.cfg depending on version), has the word 
persistence in it.
If not you can add it after the first --.
```
-- persistence
```

You might also try usb-creator, (aka Startup Disk Creator from the Live CD), or UNetbootin.


Edit:
If 4GB persistence is not enough you can create ext2 partitions named casper-rw and home-rw of any size. You can reuse home-rw after installing a new version but not casper-rw.

---

