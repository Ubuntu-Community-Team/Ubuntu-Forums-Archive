---
title: "How do I get my PCI wireless card to work?"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by arnicainthemembrane on 2008-08-12
I got a Novatech 54Mbps Unwire Notebook Adapter to speed up my internet connection, but it isn't working. The machine recognizes it but it won't work, iwconfig says "no wireless extensions". I had it working before, it is possible I somehow disconnected it. How can I troubleshoot this problem and get it working again?

---

### Post by pytheas22 on 2008-08-12
Please post the output of these commands to help us figure out what's going on:
```

lspci -nn
iwconfig
ifconfig
lshw -C Network
```

---

### Post by arnicainthemembrane on 2008-08-13
I think ifconfig fixed it. thanks.

---

### Post by arnicainthemembrane on 2008-08-14
It's not working again, damnit.

```

arnica@arnica-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82855PM Processor to I/O Controller [8086:3340] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82855PM Processor to AGP Controller [8086:3341] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] [1002:4e50]
02:00.0 CardBus bridge [0607]: Texas Instruments PCI4520 PC card Cardbus Controller [104c:ac46] (rev 01)
02:00.1 CardBus bridge [0607]: Texas Instruments PCI4520 PC card Cardbus Controller [104c:ac46] (rev 01)
02:01.0 Ethernet controller [0200]: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) [8086:101e] (rev 03)
02:02.0 Network controller [0280]: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter [8086:1043] (rev 04)
03:00.0 Network controller [0280]: RaLink RT2500 802.11g Cardbus/mini-PCI [1814:0201] (rev 01)
arnica@arnica-laptop:~$ iwconfig
lo        no wireless extensions.

eth2      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11b  ESSID:"300d"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:D1:3C:29:04   
          Bit Rate=11 Mb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0
arnica@arnica-laptop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:04:23:79:65:10  
          inet addr:192.168.254.5  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::204:23ff:fe79:6510/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50281 errors:38 dropped:0 overruns:0 frame:0
          TX packets:35016 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60210893 (57.4 MB)  TX bytes:3893886 (3.7 MB)
          Interrupt:11 Base address:0x8000 Memory:c0214000-c0214fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3933 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3933 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200128 (195.4 KB)  TX bytes:200128 (195.4 KB)


```

---

### Post by Fire_Chief on 2008-08-14
What version of Ubuntu are you running please? Also, just out of curiosity, what is the speed of your Internet connection?

---

### Post by pytheas22 on 2008-08-14
What is the output of:
```

lshw -C Network
```

---

### Post by arnicainthemembrane on 2008-08-14
Hardy Heron. Don't know the speed of the internet connection.


```

arnica@arnica-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82855PM Processor to I/O Controller [8086:3340] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82855PM Processor to AGP Controller [8086:3341] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] [1002:4e50]
02:00.0 CardBus bridge [0607]: Texas Instruments PCI4520 PC card Cardbus Controller [104c:ac46] (rev 01)
02:00.1 CardBus bridge [0607]: Texas Instruments PCI4520 PC card Cardbus Controller [104c:ac46] (rev 01)
02:01.0 Ethernet controller [0200]: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) [8086:101e] (rev 03)
02:02.0 Network controller [0280]: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter [8086:1043] (rev 04)
**03:00.0 Network controller [0280]: RaLink RT2500 802.11g Cardbus/mini-PCI [1814:0201] (rev 01)**
arnica@arnica-laptop:~$ iwconfig
lo        no wireless extensions.

eth2      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11b  ESSID:"300d"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:D1:3C:29:04   
          Bit Rate=11 Mb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0

arnica@arnica-laptop:~$ ifcong
bash: ifcong: command not found
arnica@arnica-laptop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:04:23:79:65:10  
          inet addr:192.168.254.5  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::204:23ff:fe79:6510/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50281 errors:38 dropped:0 overruns:0 frame:0
          TX packets:35016 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60210893 (57.4 MB)  TX bytes:3893886 (3.7 MB)
          Interrupt:11 Base address:0x8000 Memory:c0214000-c0214fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3933 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3933 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200128 (195.4 KB)  TX bytes:200128 (195.4 KB)


```

---

### Post by Fire_Chief on 2008-08-14
You can determine your Internet connection speed by going to [http://speedtest.net]("http://speedtest.net")

The only reason I ask is if this is your only PC and your Internet connection is less than 8 Mbps or so, then changing your wireless card will not really make a noticeable difference in speed of Internet browsing. The bottleneck is your Internet connection, not your wireless card.

Cheers!

---

### Post by arnicainthemembrane on 2008-08-14
download: 1839 kb/s
upload: 366 kb/s

---

### Post by arnicainthemembrane on 2008-08-14
BUT I use internet connections all over the place.

---

### Post by pytheas22 on 2008-08-14
Your card has a Ralink rt2500 chipset.  The drivers that ship with it for Ubuntu don't always work well, but you can compile the legacy Ralink drivers, which usually give better results.  If you want to do that, run these commands:

```
sudo -s
apt-get install rutilt build-essential
wget http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz
tar -xzvf rt*
cd rt*/Module
make
make install
echo 'blacklist rt2500usb' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2500pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt61pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2400pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00lib' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00usb' >> /etc/modprobe.d/blacklist
```

Then reboot and see if it works better.

The downside of the legacy Ralink drivers is that they don't work with Network Manager; instead, you have to use a special wireless manager built just for them.  It will be under System>Administration>Rutilt WLAN Manager.  The upside is that the legacy drivers are more stable in most cases.

---

