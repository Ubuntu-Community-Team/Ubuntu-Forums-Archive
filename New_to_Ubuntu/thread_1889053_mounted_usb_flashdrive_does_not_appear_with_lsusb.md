---
title: "mounted usb flashdrive does not appear with lsusb"
date: 2011-11-30
forum: New to Ubuntu
---

### Post by thane1 on 2011-11-30
Have purchased a Centon Datastick Pro 32GB flashdrive.  Although it mounts in ubuntu 10.10, when inserted and appears at /media/CENTON USB , it doesn't appear in the usb devices list in Terminal, if I enter ```
lsusb
```
Output from my lsusb is:
```
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 1267:0210 Logic3 / SpectraVideo plc 
Bus 004 Device 002: ID 04f9:01ea Brother Industries, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 008: ID 111d:0000  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 045e:075d Microsoft Corp. LifeCam Cinema
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
I want to find the manufacturers id and product id, to enable this flashdrive for windows use under virtualbox.  The manufacturer's website doesn't offer the information and google searches seem a dead end.  Is there another means to find the id numbers?  Thanks

---

### Post by insomniaccanuck on 2011-11-30
Possible easy answer is to go to the /media/ directory.
Unless you renamed the device it will be listed as pair of vendor/product ids in hex code.

[http://wiki.sakis3g.org/wiki/index.php?title=USB_IDS](http://wiki.sakis3g.org/wiki/index.php?title=USB_IDS)

---

### Post by thane1 on 2011-11-30
I would like to change my question.  Why does lsusb not recognize, that a usb device has been unmounted.  The reason is this:
Prior to my original post, I couldn't identify my flashdrive with lsusb.  So I safely removed/unmounted the drive and removed it from the socket.  Then I re-entered lsusb in Terminal and got exactly the same output.  So I concluded the only possible device in the list ```
Bus 002 Device 008: ID 111d:0000 
```couldn't have been the new flashdrive.  After my first post though, I decided to restart the box and do another lsusb without the flashdrive having been installed.  No 111d:0000 appeared.  So I guess thats my drive.  But why does lsusb not reflect the new, present state of the system after unmounting/removing a device?  I checked the man page for lsusb and didn't see anything of relevance to this point there.  Thanks

---

### Post by thane1 on 2011-11-30
Thanks for the reply insomniaccanuck.  I don't see any kind of directory on my system or hex codes though under /media.

---

