---
title: "[HELP] Wireless not working (LP-8617E)"
date: 2010-12-02
forum: Philippine Team
---

### Post by xxxlam on 2010-12-02
Hi guys,

I am having a problem in connecting my USB wireless device which I bought from CD-R King. I browsed the CD included in the package but theres no driver for Linux. I bought "Wireless-N USB Dongle with External Antena" with the model LP-8617E.

I successfully installed the driver in Wind0ws and it works fine.

Here's my code...
```

allan@allan-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 0bda:8171 Realtek Semiconductor Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Any idea guys. Thanks in advance. :|

---

### Post by oobermensch on 2010-12-02
Chances are, there are no drivers for that device in Linux, especially since hardware from CD-R King are just *generic*.

I could be wrong though.

---

### Post by TBABill on 2010-12-02
Does the output of ```
lsusb -vv
``` give you any additional info? Realtek Semiconductor Corp. doesn't provide much to go on other than the brand. The specific chipset may.

---

### Post by loell on 2010-12-02
try the installing the hiro driver.

[http://csiuo.com/drupal/content/installing-driver-hiro-h50193-wireless-usb-network-adapter-0bda8171-under-ubuntu-104]("http://csiuo.com/drupal/content/installing-driver-hiro-h50193-wireless-usb-network-adapter-0bda8171-under-ubuntu-104")

---

### Post by wazorie on 2011-01-09
ung version ubuntu 10.10 nakakaconnect po sa wireless N-router khit na wireless b/g lang PC/Laptop mo..

---

