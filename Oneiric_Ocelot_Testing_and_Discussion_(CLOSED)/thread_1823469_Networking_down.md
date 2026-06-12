---
title: "Networking down"
date: 2011-08-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by TDK800 on 2011-08-12
Yesterday's updates killed networking. Anyone else?

---

### Post by dino99 on 2011-08-12
nope, what did you get with ifconfig ?

---

### Post by TDK800 on 2011-08-13
The USB clip based mobile internet is not connecting (ppp0), it detects the 3G connection (light blinking), but is not connecting (light on). On the broken system ifconfig only shows eth0 and lo (no pp0). On a working system it shows eth0, lo, pp0:

(I have obfuscated some information out with *'s)

eth0      Link encap:Ethernet  HWaddr 00:*:*:*:*:*  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:596 errors:0 dropped:0 overruns:0 frame:0
          TX packets:596 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19250 (19.2 KB)  TX bytes:19250 (19.2 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:*.*.*.*  P-t-P:*.*.*.*  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:267048 errors:0 dropped:0 overruns:0 frame:0
          TX packets:250582 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:288954883 (288.9 MB)  TX bytes:34280155 (34.2 MB)


Any ideas how to get ppp0 back?

---

### Post by Harry33 on 2011-08-13
Well can you specify which update could have caused this?
There was an update of linux-firmware, which might have caused something like that.
So download the previous version from Launchpad and install it with dpkg.
See what happens.

Here:
[https://launchpad.net/ubuntu/+source/linux-firmware/1.57/+build/2674576](https://launchpad.net/ubuntu/+source/linux-firmware/1.57/+build/2674576)

---

### Post by VinDSL on 2011-08-13
> **TDK800 said:**
> Yesterday's updates killed networking. Anyone else?
"Wired connection 1" is working normally for me.

"DSL connection 1" quit working a week or two ago - although I have a *feeling* that my ISP changed something at their CO.

I don't run wireless at home - trying to lessen the EMF (electromagnetic field) surrounding me.  ;)

---

### Post by fjgaude on 2011-08-13
There has been massive updates the last 36 hours or so. At this point my wired and wireless connections are all working.

It's 18 days until Beta1. <smile>

---

### Post by TDK800 on 2011-08-14
linux-firmware was 1.57, tried versions 1.59 and 1.52.1 also.

modemmanager and usb-modeswitch are also the newest versions.

---

### Post by cariboo on 2011-08-14
What is the output of dmesg, just after you've plugged the device in?

---

### Post by TDK800 on 2011-08-15
Below are dmesg for both not working OS and a working OS, after plugging in the device:

Not working dmesg:
[   38.040146] usb 2-4: new high speed USB device number 2 using ehci_hcd
[   38.569406] usbcore: registered new interface driver uas
[   38.572784] Initializing USB Mass Storage driver...
[   38.573936] scsi5 : usb-storage 2-4:1.0
[   38.575549] show_signal_msg: 34 callbacks suppressed
[   38.575554] usb_modeswitch_[1699]: segfault at 8 ip 00007f87c9c95681 sp 00007fff8ae9f4b8 error 4 in libc-2.13.so[7f87c9c13000+195000]
[   38.576271] scsi6 : usb-storage 2-4:1.1
[   38.576380] usbcore: registered new interface driver usb-storage
[   38.576382] USB Mass Storage support registered.
[   39.572286] scsi 5:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[   39.572496] scsi 6:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[   39.822510] sr1: scsi-1 drive
[   39.822704] sr 5:0:0:0: Attached scsi CD-ROM sr1
[   39.822787] sr 5:0:0:0: Attached scsi generic sg2 type 5
[   39.830366] sd 6:0:0:0: Attached scsi generic sg3 type 0
[   39.832824] sd 6:0:0:0: [sdb] Attached SCSI removable disk


Working dmesg:
[   69.904172] usb 2-4: new high speed USB device using ehci_hcd and address 2
[   70.066776] usbcore: registered new interface driver uas
[   70.119034] Initializing USB Mass Storage driver...
[   70.119162] scsi5 : usb-storage 2-4:1.0
[   70.119328] scsi6 : usb-storage 2-4:1.1
[   70.119805] usbcore: registered new interface driver usb-storage
[   70.119808] USB Mass Storage support registered.
[   70.940603] usb 2-4: USB disconnect, address 2
[   75.892058] usb 2-4: new high speed USB device using ehci_hcd and address 3
[   76.035358] scsi10 : usb-storage 2-4:1.3
[   76.038953] scsi11 : usb-storage 2-4:1.4
[   76.042648] usbcore: registered new interface driver usbserial
[   76.042666] USB Serial support registered for generic
[   76.043444] usbcore: registered new interface driver usbserial_generic
[   76.043447] usbserial: USB Serial Driver core
[   76.050227] USB Serial support registered for GSM modem (1-port)
[   76.050295] option 2-4:1.0: GSM modem (1-port) converter detected
[   76.050497] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB0
[   76.050509] option 2-4:1.1: GSM modem (1-port) converter detected
[   76.051596] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB1
[   76.051610] option 2-4:1.2: GSM modem (1-port) converter detected
[   76.052208] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB2
[   76.052273] usbcore: registered new interface driver option
[   76.052275] option: v0.7.2:USB Driver for GSM modems
[   77.037747] scsi 10:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[   77.046459] sr1: scsi-1 drive
[   77.046498] scsi 11:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[   77.046614] sr 10:0:0:0: Attached scsi CD-ROM sr1
[   77.049018] sr 10:0:0:0: Attached scsi generic sg2 type 5
[   77.051115] sd 11:0:0:0: Attached scsi generic sg3 type 0
[   77.054309] sd 11:0:0:0: [sdb] Attached SCSI removable disk
[   86.821785] PPP BSD Compression module registered
[   86.824766] PPP Deflate Compression module registered

---

### Post by dino99 on 2011-08-15
try: sudo dpkg-reconfigure pppoeconf

---

### Post by TDK800 on 2011-08-15
> **dino99 said:**
> try: sudo dpkg-reconfigure pppoeconf

didn't do anything.


I think the problem might be in these lines:

[ 38.575549] show_signal_msg: 34 callbacks suppressed
[ 38.575554] usb_modeswitch_[1699]: segfault at 8 ip 00007f87c9c95681 sp 00007fff8ae9f4b8 error 4 in libc-2.13.so[7f87c9c13000+195000]

---

### Post by Vishal Agarwal on 2011-08-15
The same problem I have faced a couple of days ago and fortunately i was able to resolve the problem yesterday. what all i did is

1. ifconfig wlan0 down
2 ifup wlan0
3. apt-get install network-manager

reboot the system

May be any of these can help you.

---

### Post by TDK800 on 2011-08-16
system said it couldn't find wlan0, tried with ppp0 also.

Do you have the latest version of network-manager (0.8.9997+git.20110721t045648.36db194-0ubuntu2) or the previous version (0.8.9997+git.20110614t173923.b4a72d1-0ubuntu1)

Going to connect it through ethernet cable in a few hours and run the week worth of latest updates, will post an update if that fixes anything.

---

### Post by TDK800 on 2011-08-20
Connected through eth0, ran all the latest updates yesterday. Didn't work.

Today diconnected usb device, edited /etc/usb_modeswitch.conf and enabled logging, reconnected device, after that it immediately connected to internet.

---

