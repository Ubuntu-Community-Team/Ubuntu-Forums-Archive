---
title: "D-Link DWA-140 connection problems"
date: 2011-11-24
forum: New to Ubuntu
---

### Post by kmisad on 2011-11-24
Hi there,

 Today i received my USB D-Link DWA-140, that i read it would solve easily solve my Wi-Fi problem with Ubuntu 11.10.
 Instead....here I am still without any connection, to notice that i am a newbie....:confused::mad:

---

### Post by gandaran on 2011-11-24
is it the simple D-Link DWA-140 or B2 model?
according to this guide the DWA-140 works out of the box but the B2 doesn't
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)
anyway post the output of these commands just to check model and if the driver rt2870sta is loaded
```
lsusb
```
and
```
lsmod
```

---

