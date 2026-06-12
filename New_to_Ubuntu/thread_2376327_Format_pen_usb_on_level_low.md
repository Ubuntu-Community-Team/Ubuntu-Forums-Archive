---
title: "Format pen usb on level low"
date: 2017-11-01
forum: New to Ubuntu
---

### Post by sed_faster on 2017-11-01
Hello my dears folks :)

I need formatted a pen usb on a low level. I don't understand very much about levels formatted, but i know which exist many different levels. I need a level where the recovery the information on the pen usb become difficult. 

To formatted pen usb on linux I konw  Gparted, Mkfs (by terminal). I intend format this pen usb on format Fat16, because I will use it on Windows.

What do yo suggest to handle this task?
I prefer a tool through terminal, because this option offer more flexibility across platforms.
Thanks

---

### Post by C.S.Cameron on 2017-11-02
[https://askubuntu.com/questions/22381/how-to-format-a-usb-flash-drive](https://askubuntu.com/questions/22381/how-to-format-a-usb-flash-drive)

---

### Post by HermanAB on 2017-11-03
Two things:
1. Ubuntu has a disk utility called Disks that can format things.
2. To securely delete data from a flash memory, you only need to erase it once.

---

### Post by sudodus on 2017-11-03
[SIZE=4]Wipe the whole device[/SIZE]

I can confirm that you only need to erase the pendrive once, (erase alias wipe alias overwrite the whole device with zeros).

You can do it with

- the built-in tool **Disks** alias gnome-disks.

- the **mkusb** tool, that you install from a PPA, and is useful for several tasks related to USB pendrives, creating USB boot drives and restoring drives to standard storage devices.

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[https://help.ubuntu.com/community/mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe) 

```
sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb mkusb-nox usb-pack-efi
```

[SIZE=4]File system[/SIZE]

Do not use FAT16 (unless you have a very small pendrive). The current basic standard file system is FAT32, but you can consider other file systems too, particularly if you want to store files bigger than 4 GB. See this link

[How do I copy a file larger than 4GB to a USB flash drive?](https://askubuntu.com/questions/952673/how-do-i-copy-a-file-larger-than-4gb-to-a-usb-flash-drive/952706#952706)

---

