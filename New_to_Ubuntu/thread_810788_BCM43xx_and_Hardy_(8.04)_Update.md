---
title: "BCM43xx and Hardy (8.04) Update"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by dwhitney67 on 2008-05-28
I don't have question, but merely the desire to record the knowledge I gained this morning concerning getting my wireless chip-set to work on my Dell Inspiron E1505 laptop.

This past weekend I upgraded from 7.10 to 8.04.  Previously, with 7.10, the wireless chip-set functioned properly.  However, with 8.04, the chip-set was not enabled.  Fortunately, the solution to this problem was easily determined.  All I had to do is edit /etc/modules and add the bcm43xx driver to the list, and then perform a reboot.

If you find yourself in a similar predicament, don't muck your system with a million experimental changes until you at least try what I did.

Cheers.

------------------------------------------

Output from 'lspci':
```

$ lspci
...
0b:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
```

Listing of '/etc/modules':
```
$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
sbp2
fuse

# Added entry below for wi-fi support.
bcm43xx
```

---

