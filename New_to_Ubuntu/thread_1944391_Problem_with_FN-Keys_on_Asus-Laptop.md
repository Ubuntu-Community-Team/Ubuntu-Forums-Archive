---
title: "Problem with FN-Keys on Asus-Laptop"
date: 2012-03-21
forum: New to Ubuntu
---

### Post by mazell on 2012-03-21
Hello,

I have a problem with my FN-Keys on my new laptop.
They don't work since I installed Ubuntu. The knock-on problems are that I can't turn on my w-Lan and that the laptop doesn't find the correct size of an external monitor. At least I think that these problems are caused by the missing FN-Keys or can be resolved having these keys. I tried to find out what the problem is and here's all information I can give you:

The laptop:
Asus p53e-SO102X
Intel Core i3 - 2330M, 2.2GHz
2GB RAM
(Delivered with Win7 Pro)

Ubuntu 10.04 LTS
(which sadly had some issues with the network-card, which is why I updated the kernel to 2.6.38-13-generic)

Here's the ouptut of uname -a:
```
marcel@aurorII:~$ uname -a
Linux auroraII 2.6.38-13-generic #56~lucid1-Ubuntu SMP Tue Feb 14 03:18:12 UTC 2012 x86_64 GNU/Linux
```The network-card and the wlan-module have the correct drivers and work fine. I can turn them on and off via ifconfig. Here's some more info about that:
```
marcel@auroraII:/etc$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Device [8086:0104] (rev 09)
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:0116] (rev 09)
    Kernel driver in use: i915
    Kernel modules: i915
00:16.0 Communication controller [0780]: Intel Corporation Cougar Point HECI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation Cougar Point High Definition Audio Controller [8086:1c20] (rev 05)
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 1 [8086:1c10] (rev b5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 2 [8086:1c12] (rev b5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.5 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 6 [8086:1c1a] (rev b5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
    Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:1c49] (rev 05)
    Kernel modules: iTCO_wdt
00:1f.2 SATA controller [0106]: Intel Corporation Cougar Point 6 port SATA AHCI Controller [8086:1c03] (rev 05)
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation Cougar Point SMBus Controller [8086:1c22] (rev 05)
    Kernel modules: i2c-i801
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Kernel driver in use: ath9k
    Kernel modules: ath9k
03:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1083] (rev c0)
    Kernel driver in use: atl1c
    Kernel modules: atl1c
marcel@auroraII:~$ ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 54:04:a6:3f:69:3d  
          inet Adresse:192.168.2.101  Bcast:192.168.2.255  Maske:255.255.255.0
          inet6-Adresse: fe80::5604:a6ff:fe3f:693d/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:103704 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78506 errors:0 dropped:0 overruns:0 carrier:1
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:128204990 (128.2 MB)  TX bytes:6313913 (6.3 MB)
          Interrupt:43 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:1236 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1236 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:36493 (36.4 KB)  TX bytes:36493 (36.4 KB)

wlan0     Link encap:Ethernet  Hardware Adresse e0:b9:a5:ce:cd:a1  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
marcel@auroraII:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
```The other Problem is, that I've got a 24"-Monitor and if I plug it to the laptop only half the screen is used, because it's shown in the size of the laptop-monitor. I hope that I can fixed these two problems with using FN+F2 to turn the wlan on and FN+F8 to resize the monitor.

I tried even some configuration-files, e.g. of xandr and wpa_supplicant but neither did solve my problems.
I hope you can help me.

Best
Marcel

---

### Post by Mark Phelps on 2012-03-22
The basic question is whether or not the kernel sees the keypresses.  IF it does not, there is nothing you can do.

Historically, "xev" has been used to see if pressing the key sends any information the kernel can see.

Some instructions on using xev:  [http://crunchbanglinux.org/wiki/xev-determine_custom_keybindings]("http://crunchbanglinux.org/wiki/xev-determine_custom_keybindings")

As to the monitor, it's generally a bad idea to lump unrelated problems into the same thread.  Just makes things confusing.

Would suggest you start a separate thread for the monitor problem.

---

### Post by mazell on 2012-03-27
Hello Mark,

thanks for your reply. I tried xev to determine if the kernel sees the pressing of fn but unfortunately it doesn't. That's really bad.
Ok, I need another way to turn on my wlan then. So I do some research again on how to solve this problem and get in touch if I can't find anything.

Best
Marcel

---

