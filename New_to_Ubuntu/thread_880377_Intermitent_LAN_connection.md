---
title: "Intermitent LAN connection"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by LValeria on 2008-08-04
Hi, I have 2 laptops (mine and my sister's) that are almost the same (same brand, same model, but the manufacturer made some upgrades, one is 4 months newer than the other). They both have Kubuntu 8.04 installed with all the latest upgrades (stable, not testing). At home we have a ADSL modem that connects to a switch via rj45, all the computers are connected to the switch and have internet access.
My computer always has internet, but my sister's computer sometimes has and sometimes not (usually between reboots, but once lost internet without reboot). It is not a problem outside the computer, tested on several of the switch's ports, tested several cables, and the only computer with connection problems is my sister's.
I make no changes between "working" and "not working", only reboots, so I have no idea what is the problem. This is all the info I could think of getting that could be useful from my sister's computer:

> etc/network/interfaces:
auto lo eth0
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

iface eth0 inet static
address 10.0.0.36
netmask 255.255.255.0
gateway 10.0.0.2

> lspci:
00:00.0 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M G (rev a1)
05:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
06:04.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
06:04.1 SD Host controller: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller
06:04.3 FLASH memory: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller

> ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:90:f4:66:8d:7e
          inet addr:10.0.0.36  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::290:f4ff:fe68:8d5e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:2 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1050 (1.0 KB)  TX bytes:3903 (3.8 KB)
          Interrupt:21 Base address:0x2400

When it is not working I don't get an answer to ping from the Modem.

Any other info you need, just ask (with instructions on how to get it)

Thanks

---

### Post by eightmillion on 2008-08-05
Try booting with the irqpoll option enabled. You'll need to edit your **/boot/grub/menu.list**

```
sudo gedit /boot/grub/menu.list
```
You'll need to add it onto the end of the kernel line like so...
```
title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=82c05c38-8881-48ab-8fd9-3349bf7d2c83 ro quiet splash vga=792 **irqpoll**
initrd          /boot/initrd.img-2.6.24-19-generic
quiet


```

---

### Post by LValeria on 2008-08-05
Ok, i'll do that tomorrow when I can get my hands on her computer.
You think it is an irq conflict? sometimes the lan card wins and it works fine and sometimes another thing wins and the lan doesn't work?
Will irqpoll generate a log file or will it try to solve that problem? (do I have to post some particular result or is it a solve/ don't solve thing?)
Thanks

---

### Post by eightmillion on 2008-08-06
There was a bug report on the kernel open for that card, but it was closed without ever being fixed so I'm assuming it still exists. Others with the same card have reported that booting with the irqpoll option solved their problems. Chances are good that if you look through **/var/log/kern.log** you'll see messages like this:
> Dec 9 09:49:54 ofm kernel: [ 3445.048000] irq 24: nobody cared (try booting with the "irqpoll" option)
> You think it is an irq conflict? sometimes the lan card wins and it works fine and sometimes another thing wins and the lan doesn't work?
Irqpoll tells the kernel, when an interrupt is not handled, search all known interrupt handlers for it. This is intended to get systems with badly broken firmware running.
> Will irqpoll generate a log file or will it try to solve that problem? (do I have to post some particular result or is it a solve/ don't solve thing?)
Just booting with that enabled should solve your problem hopefully.

---

### Post by LValeria on 2008-08-06
Hi, I'm "the sister". It worked! Thank you very very very much! :biggrin:
I was upset and internet-less over so small a thing. Thanks again!

Ana

---

