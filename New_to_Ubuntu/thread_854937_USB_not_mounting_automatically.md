---
title: "USB not mounting automatically"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by gtdaqua on 2008-07-10
I am continuing [this]("http://ubuntuforums.org/showthread.php?t=582045&page=8") thread because its not solved yet.

Since yesterday, Kubuntu Hardy has stopped automounting USB drives. Dmesg and lsusb are seeing them. So, manual mount is possible. Dolphin is not seeing the new drive.

---

### Post by kansasnoob on 2008-07-10
I've had good luck with the package

> usbmount

which is available in synaptic.

An alternative is

> pmount

which plays well with hal which should be installed by default.

---

### Post by gtdaqua on 2008-07-10
installing pmount does not solve. why is this happening since recently?

---

