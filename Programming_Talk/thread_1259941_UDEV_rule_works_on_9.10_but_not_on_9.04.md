---
title: "UDEV rule works on 9.10 but not on 9.04"
date: 2009-09-07
forum: Programming Talk
---

### Post by sparker256 on 2009-09-07
Using the following rule I get the correct permisions on 9.10 but not on 9.04  Not sure why that should matter. Any thoughts

********************************************************************
From Ubuntu 9.04 with this rule 99-hidraw.rules

KERNEL=="hidraw*", SUBSYSTEM=="hidraw", SYSFS{idProduct}=="0d05", SYSFS{idVendor}=="06a3", MODE="0666"
KERNEL=="hidraw*", SUBSYSTEM=="hidraw", SYSFS{idProduct}=="0d67", SYSFS{idVendor}=="06a3", MODE="0666"
KERNEL=="hidraw*", SUBSYSTEM=="hidraw", SYSFS{idProduct}=="0bac", SYSFS{idVendor}=="06a3", MODE="0666"


bill@bill-desktop:/dev$ ls -l hidraw0
crw-rw---- 1 root root 251, 0 2009-09-06 21:32 hidraw0
bill@bill-desktop:/dev$ ls -l hidraw1
crw-rw---- 1 root root 251, 1 2009-09-06 21:32 hidraw1
bill@bill-desktop:/dev$ ls -l hidraw2
crw-rw---- 1 root root 251, 2 2009-09-06 21:32 hidraw2
bill@bill-desktop:/dev$ 

********************************************************************
From Ubuntu 9.10 with this rule 99-hidraw.rules

KERNEL=="hidraw*", SUBSYSTEM=="hidraw", SYSFS{idProduct}=="0d05", SYSFS{idVendor}=="06a3", MODE="0666"
KERNEL=="hidraw*", SUBSYSTEM=="hidraw", SYSFS{idProduct}=="0d67", SYSFS{idVendor}=="06a3", MODE="0666"
KERNEL=="hidraw*", SUBSYSTEM=="hidraw", SYSFS{idProduct}=="0bac", SYSFS{idVendor}=="06a3", MODE="0666"


bill@bill-910:/dev$ ls -l hidraw0
crw-rw---- 1 root root 252, 0 2009-09-06 18:25 hidraw0
bill@bill-910:/dev$ ls -l hidraw1
crw-rw-rw- 1 root root 252, 1 2009-09-06 18:25 hidraw1
bill@bill-910:/dev$ ls -l hidraw2
crw-rw-rw- 1 root root 252, 2 2009-09-06 18:25 hidraw2
bill@bill-910:/dev$ ls -l hidraw3
crw-rw-rw- 1 root root 252, 3 2009-09-06 18:25 hidraw3
bill@bill-910:/dev$ 

**********************************************************************

Bill

---

### Post by dwhitney67 on 2009-09-07
This seems more like a systems/OS related question, and further more, one that is related to an OS that technically has not even been officially released.

I may be wrong, but the permissions for UDEV rule files should be 644, not the values you have shown.  So IMO, both of your OSes have the wrong settings.

P.S.  Mode 644 = "-rw-r--r--"

P.S. #2   Use chmod from the command line to fix the file permission problems.

P.S. #3   In case you wanted to write a program to make the permissions change, save the following to an executable file, and then as root or sudo, run it:
```

#!/bin/sh

chmod 644 /etc/udev/rules.d/hidraw*

```

---

