---
title: "Network disabled?"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by TheS0urce on 2008-05-19
I installed virtualbox once I rebooted I am no longer connected to the internet it says my network device is disabled.

Your help will be appreciated.

---

### Post by joslinar on 2008-05-19
Open a terminal and run the following code

```
ifconfig
cat /etc/network/interfaces
```


post the output here so we can help you.

---

### Post by TheS0urce on 2008-05-19
mikek1969@mikek1969-desktop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:60800 (59.3 KB)  TX bytes:60800 (59.3 KB)

mikek1969@mikek1969-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by joslinar on 2008-05-20
I don't see any network adapters in the ouput you showed me. First of all, Is the problem with your virtual machine or the host? IF it is the virtual machine you'll probably only have to enable the interface. I haven't use virtual box in a long time but in vmware you can allow the virtual host to see the real, physical host devices trough the vmware menus.

If you are trying to troubleshoot the real, physical host then a good place to start is to check weather or not the OS detected with the following command 
```
lspci
```
make sure you post the output here.

---

### Post by TheS0urce on 2008-05-20
The problem is with the virtual machine.  Here is the output anyways:

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
02:05.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
02:0d.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
02:0d.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02

---

### Post by HotShotDJ on 2008-05-20
Just so I'm clear on the issue... on the HOST operating system you have connectivity... on the GUEST operating system, you do NOT have connectivity. Yes? No? Corrections?

---

### Post by joslinar on 2008-05-21
then do the lspci command on the virtual machine.

---

### Post by TheS0urce on 2008-05-22
I did that's the output.

---

