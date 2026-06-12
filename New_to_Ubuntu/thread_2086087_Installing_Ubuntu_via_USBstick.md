---
title: "Installing Ubuntu via USBstick"
date: 2012-11-19
forum: New to Ubuntu
---

### Post by PCNT on 2012-11-19
> **LarsVinter said:**
> I have the same issue. I was able to solve it the following way:

1) Copy the server-iso file to another usb stick
2) Insert that usb stick into the new box
3) ALT+F2 to another console and:
4) Mount the usb-stick to /mnt/usb:
     a) mkdir /mnt/usb
     b) mount -t vfat /dev/<your_usb_device> /mnt/usb
5) Mount the server-image file to /cdrom
     a) mount -t iso9660 -o loop /mnt/usb/ubuntu-11.04-server-amd64.iso /cdrom
6) exit from the terminal and ALT+F1 back to main installer screen
7) Press ESC to avoid trying to mount cd-rom
8) In main installer menu chose "Detect and mount CD-rom"

This time it will actually detect your USB stick as the CD-rom.

It works for me now and I was able to install the server fully.

Lars
5


When I enter those commands it says: mount: mounting /dev/sdb1 on /mnt/usb failed: invalid argument

Any suggestions?

---

### Post by oldos2er on 2012-11-19
Post moved to its own thread.

---

