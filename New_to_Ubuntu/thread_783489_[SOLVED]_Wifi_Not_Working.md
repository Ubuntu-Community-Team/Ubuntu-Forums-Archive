---
title: "[SOLVED] Wifi Not Working????"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Promaster91 on 2008-05-05
I installed Hardy Heron about one and a half months ago and I got the wifi working just fine using the madwifi drivers. For some reason, when I rebooted today I noticed that I had no wireless. I reinstalled the drivers but when I try to run them i get this error.
```

stefan@stefan-laptop:~/madwifi-ng-r2756+ar5007$ sudo modprobe wlan_scan_sta
stefan@stefan-laptop:~/madwifi-ng-r2756+ar5007$ sudo modprobe ath_pci
FATAL: Error inserting ath_pci (/lib/modules/2.6.24-16-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```
This is really weird and bad. If I don't have wifi I will have to boot into Vista (came with the computer)!:( Can anybody help. Thanks in advance.

---

### Post by Promaster91 on 2008-05-27
Fixed it myself. Recompiled the drivers.

---

