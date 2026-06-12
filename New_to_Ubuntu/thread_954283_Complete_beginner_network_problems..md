---
title: "Complete beginner network problems."
date: 2008-10-21
forum: New to Ubuntu
---

### Post by pluekiller on 2008-10-21
I seem unable to connect to the internet at all..

I am running Wubi just to try it out..

My laptop is a zepto nox.

It seems to me that my ubuntu is unable to detect both my ethernet and wireless cards..

From the windows device manager.. here are my cards..
Realtek RT8168(c)p/8111C(P) Family PCI-E Gigabit Ethernet NIC (NDIS 6.0)
and a generic 802.11n Wireless LAN card.

If it is any issue.. I am currently connected with an ethernet cable to my university's network, which requires a login.

Thanks in advance for the help.. I really want to try ubuntu, and sorry if this problem is in other threads, i am completely lost about what to do.

---

### Post by sazan on 2008-10-21
i dont knw if this will help.. but is ur DHCP enabled...

goto Systems->Administration->Network->select eth0 and then select DHCP from drop down menu .. and then try connecting.. lemme knw if it works..

---

### Post by Nepherte on 2008-10-21
Give the output of these commands:
```
lspci
```
```
ifconfig
```

---

### Post by pluekiller on 2008-10-21
Couldn't find DCHP in the network settings..

Interestingly, I tried a reinstall of Wubi, and now my windows can't detect my eternet driver too. Two networking problems to fix. Lucky i still have wireless. haha.

anyway heres what i got

lspci

00:00.0 Host bridge: Intel Corporation Cantiga Memory Controller Hub (rev 07) 
00:01.0 PCI bridge: Intel Corporation Cantiga PCI Express Graphics Port (rev 07) 
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) 
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) 
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03) 
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) 
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03) 
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03) 
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03) 
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) 
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03) 
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) 
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03) 
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03) 
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0649 (rev a1) 
04:00.0 Network controller: RaLink Unknown device 0781 

ifconfig

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:2076 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2076 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:103800 (101.3 KB)  TX bytes:103800 (101.3 KB)

---

### Post by pluekiller on 2008-10-21
just a quick note if it matters.. a reinstall of the network driver in windows fixed my windows connectivity..

I also noticed that the website provides a driver for linux.. do i need to install that?

---

