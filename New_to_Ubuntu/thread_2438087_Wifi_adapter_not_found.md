---
title: "Wifi adapter not found"
date: 2020-03-05
forum: New to Ubuntu
---

### Post by manjunatham2 on 2020-03-05
Few minutes back installed ubuntu and not able to connect to wifi network. please help me

as i am new here i have no much idea, if u need any additional data please give me terminal code also to retrieve that

ran the following command in terminal 
lspci -knn | grep Net -A3; rfkill list

and received:
0a:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
    Subsystem: AzureWave BCM4352 802.11ac Wireless Network Adapter [1a3b:2b23]
    Kernel driver in use: bcma-pci-bridge
    Kernel modules: bcma
0: dell-rbtn: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

---

### Post by CelticWarrior on 2020-03-05
With an alternative internet connection (Ethernet, USB tethering from a phone, etc.), try this:

```
sudo apt purge bcma-pci-bridge
sudo apt install bcmwl-kernel-source
```

Source: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by manjunatham2 on 2020-03-05
thank you. it worked.

---

### Post by CelticWarrior on 2020-03-05
Great. :)

Please use the thread tools to mark it as solved.

---

