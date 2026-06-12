---
title: "Drivers OK, but Network Disabled"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by lnajt on 2008-10-04
Following the instructions at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Load%20the%20new%20driver%20module](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Load%20the%20new%20driver%20module) for setting up NDiswrapper and using it to install my wireless card drivers I have been able to get my driver, though not my wireless, to work. 

Running lswh tells me that the entry for network (that is,wlan0) is marked disabled. Allegedly, the solution to this problem varies from computer to computer, but I have been unable to find a fix for my computer (A Dell Latitude D830).

Does anyone here know of such a fix, or even a general one?

Thank you.

---

### Post by pytheas22 on 2008-10-04
Please post the output of the following commands:
```

uname -m
ndiswrapper -l
lshw -C Network
lspci -nn
dmesg | grep -e ndis -e wlan
```

---

