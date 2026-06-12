---
title: "No wired connection after update to Xubuntu 12.04"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by Redknecht on 2012-04-29
Hi, I searched forums for answer and it seems that there are more similar problems, but I did not find anything I could use.

I have an old machine running Xubuntu without problems so far. Recently I made an update to new version. Everything is ok, just the net won't connect. 

Please give me an advice, what should I check to find the rootcause? (i have no or little experience with linux).

My computer uses RTL-8029(AS).

Thanks!

---

### Post by bluess5700 on 2012-04-30
Have same problem. Just upgraded to 12.04 (from 11.10)  and ethernet card RTL-8029(AS) no longer works :-(

lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:04.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:04.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:04.2 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:04.3 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:04.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:09.0 Network controller: Ralink corp. RT2561/RT61 rev B 802.11g
00:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
00:0a.1 Input device controller: Creative Labs SB Live! Game Port (rev 08)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
00:0d.0 SATA controller: Initio Corporation INI-1623 PCI SATA-II Controller (rev 02)
00:11.0 Mass storage controller: Promise Technology, Inc. PDC20265 (FastTrak100 Lite/Ultra100) (rev 02)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI R350 AH [Radeon 9800]
01:00.1 Display controller: Advanced Micro Devices [AMD] nee ATI R350 [Radeon 9800] (Secondary)


relevant ouput from command lshw
*-network:1
             description: Ethernet interface
             product: RTL-8029(AS)
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: b
             bus info: pci@0000:00:0b.0
             logical name: eth0
             version: 00
             serial: 00:00:e8:5c:92:35
             width: 32 bits
             clock: 33MHz
             capabilities: ethernet physical
             configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 latency=0 multicast=yes
             resources: irq:10 ioport:8800(size=32)


dmesg | grep ne2k-pci
[    3.047151] ne2k-pci.c:v1.03 9/22/2003 D. Becker/P. Gortmaker
[    3.076525] ne2k-pci 0000:00:0b.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10

---

### Post by pqwoerituytrueiwoq on 2012-04-30
found this:
[http://www.linuxquestions.org/questions/linux-networking-3/failed-to-bring-up-eth0-rtl8029-362578/#post1850526](http://www.linuxquestions.org/questions/linux-networking-3/failed-to-bring-up-eth0-rtl8029-362578/#post1850526)
just don't type the "/sbin/" part of commands and you will need to use sudo on modprobe

---

### Post by bluess5700 on 2012-04-30
Further commands...

lsmod | grep ne2k
ne2k_pci               13389  0 
8390                   18400  1 ne2k_pci

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:e8:5c:92:35  
          inet6 addr: fe80::200:e8ff:fe5c:9235/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10353 (10.3 KB)  TX bytes:4906 (4.9 KB)
          Interrupt:10 Base address:0x8800

lsmod | grep ne2k
ne2k_pci               13389  0 
8390                   18400  1 ne2k_pci

dmesg | grep eth0
[    5.261670] eth0: RealTek RTL-8029 found at 0x8800, IRQ 10, 00:00:e8:5c:92:35.
[   29.508423] ADDRCONF(NETDEV_UP): eth0: link is not ready

cat /proc/pci
cat: /proc/pci: No such file or directory

---

### Post by bluess5700 on 2012-04-30
Found this thread:-
[http://ubuntuforums.org/showthread.php?t=1914185&highlight=rtl-8029](http://ubuntuforums.org/showthread.php?t=1914185&highlight=rtl-8029)
see post #4

Added into file /etc/network/interfaces eth0 settings
     Code:
     ```
auto eth0
iface eth0 inet dhcp 
```Then restart the network:
     Code:
     ```
sudo service networking restart
```Fixed for me

---

### Post by AGFApan on 2012-04-30
I fond this why trying to a fix a simmilar problem with arch. 

I don't know if it will be of help, but when I ran, "lspci -v" on the system I saw that under my, "Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller" there was no Kernel driver in use listed. 

So I ran "modprobe r8168" and after a few second it began to work.However, this is not persistent.

---

### Post by jat421 on 2012-04-30
I had to assign a manual IP for it to work. Try that if nothing else works.

---

### Post by bdalzell on 2012-06-29
This seems to happen to me fairly regularly when I do an upgrade in Ubuntu/Xubuntu.

From 11.10 to 12.04 I lost the ability to connect the wired ethernet to the dsl modem.

This time I found the problem was because the file

/etc/network/interfaces 

was not retained in its original form from my previous Xubuntu install

This works:
<begin file content>

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
<end file content>

The new install had this line commented out:

#iface eth0 inet dhcp


once i removed the hash mark and resaved the file (you have to use sudo gedit or sudo nano, etc to edit the file) and restarted the computer I was online.

---

