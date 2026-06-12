---
title: "Wireless network too slow and unreliable"
date: 2021-01-03
forum: New to Ubuntu
---

### Post by abinav-shankar on 2021-01-03
Hi,

I am dual-booting Windows 10 and Ubuntu 20.10 in my laptop and I have a wireless network issue in Ubuntu. The internet speed is too low compared to Windows 10. I only reach Kbps in Ubuntu while in W10 it's always Mbps. Besides the speed, the connection breaks every now and then in Ubuntu. The status bar shows I am connected to the internet but both my upload and download speed falls down to 0. I found other people were having similar issues with Ubuntu 20.04 and the fixes they suggested didn't work for me. Has anyone faced the same issue and found a fix yet?

Thanks.

---

### Post by yancek on 2021-01-03
I doubt if you will get any help without posting some details.  Run the commands below and post the output here.

```
lspci | grep -i wireless
``` 

Have you gone through the wireless troubleshooting documentation at the link below? 

[https://help.ubuntu.com/stable/ubuntu-help/net-wireless-troubleshooting-hardware-check.html.en](https://help.ubuntu.com/stable/ubuntu-help/net-wireless-troubleshooting-hardware-check.html.en)

If you have inxi installed, running the command:  inxi -N will give the network card and driver info.

---

### Post by abinav-shankar on 2021-01-04
Hi,

The command lspci | grep -i wireless doesn't return anything. However,  I ran lshw -C network and got the following details

  *-network                 
       description: Wireless interface
       product: RTL8822BE 802.11a/b/g/n/ac WiFi adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlo1
       version: 00
       serial: 74:40:bb:49:e4:bd
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtw_8822be driverversion=5.8.0-33-generic firmware=N/A ip=192.168.0.103 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:142 ioport:3000(size=256) memory:a4000000-a400ffff


The troubleshooter is basic and doesn't list my problem.

---

