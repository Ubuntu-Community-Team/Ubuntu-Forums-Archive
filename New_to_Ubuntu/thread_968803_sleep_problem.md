---
title: "sleep problem"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by ozmick on 2008-11-03
hello all
    
this is my first post so be kind

I've just upgraded to 8.10 from 8.04 and my pc goes to sleep and wakes up fine but the only way it will reconnect to the Internet is if I restart 
any help would be greatly appreciated :(

---

### Post by jbrown96 on 2008-11-03
Could you give some info on your internet connect (i.e. wired or wireless)? your hardware, in a terminal (apps-->accessories-->terminal) enter ```
lspci
``` and post the output here. When you have an internet connection post ```
ifconfig
``` and if using wireless ```
iwconfig
```. Then post the same commands after sleep when your connection does not work. Are you doing anything else besides putting it to sleep and waking it up (turing off wifi switches)?

---

### Post by ozmick on 2008-11-03
ok here goes

mick@mick-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0f.0 IDE interface: VIA Technologies, Inc. VT8251 AHCI/SATA 4-Port Controller
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8251 PCI to ISA Bridge
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 70)
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8251 Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8251 PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)
02:00.0 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port
02:00.1 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port
mick@mick-desktop:~$ 


its a wired connection 


eth0      Link encap:Ethernet  HWaddr 00:15:f2:f6:e8:8f  
          inet addr:10.1.1.2  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fef6:e88f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18787 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18057 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18351176 (18.3 MB)  TX bytes:2520017 (2.5 MB)
          Interrupt:23 Base address:0x400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:390 errors:0 dropped:0 overruns:0 frame:0
          TX packets:390 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26760 (26.7 KB)  TX bytes:26760 (26.7 KB)

---

### Post by ozmick on 2008-11-03
and after waking 

mick@mick-desktop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:15:f2:f6:e8:8f  
          inet6 addr: fe80::215:f2ff:fef6:e88f/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:18967 errors:0 dropped:589815 overruns:0 frame:589815 
          TX packets:18197 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:18568901 (18.5 MB)  TX bytes:2537677 (2.5 MB) 
          Interrupt:23 Base address:0x400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:390 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:390 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:26760 (26.7 KB)  TX bytes:26760 (26.7 KB)

---

### Post by ozmick on 2008-11-03
anyone?

---

### Post by jbrown96 on 2008-11-03
try running ```
sudo dhclient
``` after waking it up. Your interface reactivates correctly (eth0 is visible both times); however, it does not have an ip address. I'll look into how to automate this if it works.

---

### Post by adieb on 2008-11-03
if that wont help try

sudo /etc/init.d/networking restart

It does pretty much the same, but maybeyou get an error with to dhcp.clients messing up each other...

---

### Post by ozmick on 2008-11-03
bummer    neither of these options worked

---

### Post by jbrown96 on 2008-11-04
Read this bug report if you want the full story, but the relavent messages are the last couple. [https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/111282]("https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/111282") It looks like it's fixed, but you may need to do a clean install to get it working. Otherwise, you can try the irqpoll method. To try it temporarily, do the following:
1. Reboot and press Esc when GRuB is loading.
2. Select the kernel you boot (usually the first entry, probably of the form 2.6.27-)
3. Press e to edit the entry
4. Highlight the second line and press e again 
5. Go to the end of the line and append irqpoll
6. press b to boot
If this works, we can make it permanent by adding it in your grub files. Find the same entry (it will be at the end) and add irqpoll in the same manner ```
sudo gedit /boot/grub/menu.lst
```
I would recommend a clean install though.

---

### Post by ozmick on 2008-11-06
well thank you all for your efforts:)

---

