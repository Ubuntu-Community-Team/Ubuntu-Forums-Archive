---
title: "Script to make a USB stick to Flash your BIOS with"
date: 2008-08-09
forum: Outdated Tutorials &amp; Tips
---

### Post by HunterThomson on 2008-08-09
#!/bin/bash
#
# Shell script to make a USB Tumb Drive for Flashing BIOS.

Under construction...

---

### Post by kung fu buntu on 2008-08-10
This doesn't work :-/

What I did:
cat /proc/partitions
cfdisk $MYBOOTUSB
chosend partition type 0x0E
install-mbr -v --enable A1 --partition 1 --force --timeout 0 "$MYBOOTUSB"
mkdosfs -F 16 -vc "$MYBOOTUSB"1

Then copied freedos files to it.
When I booted it printed an error...

I have googled and googled, tried lots of stuff, but so far haven't found a (good) working method.

I was able to boot a usb drive with syslinux and a img file. The drawback was being unable to work with the image file in an easy way.
This means you have to mount the image if you want to make changes, and when you boot the usb key that is read only. Another problem is that you can't have a big boot img... and I would like to have freedos fully featured (the contents on the iso version).

---

### Post by HunterThomson on 2008-08-16
who ya this scipt is not working ...... Sorry I was slacking on it.... I fine tuned up the one for the lenovo ideapad Y510. This scrip is jsut like an offshoot...

I will fix it...

---

