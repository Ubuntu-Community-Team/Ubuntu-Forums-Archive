---
title: "USB Device question"
date: 2014-01-24
forum: New to Ubuntu
---

### Post by mike.lussier on 2014-01-24
I have a USB device for Radio control . Every time I boot up the computer I have to search for the USB device. it can be /dev/ttyUSB0 to /dev/ttyUSB4 on the system. 

The question is can I hard code this some place so it identfies the device and always gives it the same ttyUSB identifier. 

Its a pain in the but whn I power up to make some radio contacts and I spend 15 - 20 minutes reconfiguring my software each time.

Thank you 


Michael 

System :: 
Ubuntu 12.04 64bit on Dell Inspiron 620 R7850 video card running 3 monitors.

---

### Post by Dennis N on 2014-01-24
How about giving the device a label?

[https://wiki.archlinux.org/index.php/persistent_block_device_naming](https://wiki.archlinux.org/index.php/persistent_block_device_naming)

see the section "Persistent Naming Methods - by label"

The utility used depends on the filesystem. gparted can do this also.

[898]

---

### Post by Dennis N on 2014-01-24
How about giving the device a label?

[https://wiki.archlinux.org/index.php/persistent_block_device_naming](https://wiki.archlinux.org/index.php/persistent_block_device_naming)

see the section "Persistent Naming Methods - by label"

The utility used depends on the filesystem. gparted can do this also.

[898]

---

