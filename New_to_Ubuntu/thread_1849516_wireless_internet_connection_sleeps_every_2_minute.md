---
title: "wireless internet connection sleeps every 2 minutes"
date: 2011-09-24
forum: New to Ubuntu
---

### Post by shevin on 2011-09-24
guys , I have sprint's mobile hotspot 4g internet 
(it is a wireless hotspot) I can connect to it in windows fine and I connect to it in ubuntu 11.04 too
but every 2-3 minutes , the interent goes to sleep and I have to disconnect it and connect again .

(it doesnt say it is discconnected but it wont load any site in firefox and it says server not found , so I have to re-connect every 2-3 minutes)

any idea?

---

### Post by gandaran on 2011-09-24
> **shevin said:**
> guys , I have sprint's mobile hotspot 4g internet 
(it is a wireless hotspot) I can connect to it in windows fine and I connect to it in ubuntu 11.04 too
but every 2-3 minutes , the interent goes to sleep and I have to disconnect it and connect again .

(it doesnt say it is discconnected but it wont load any site in firefox and it says server not found , so I have to re-connect every 2-3 minutes)

any idea?
could be wireless driver or wireless security issue with the driver, try changing the wep, wpa or wpa2.
and post the output of 
```
lspci
``` 
to check the wireless chipset brand.

---

### Post by shevin on 2011-09-24
> **gandaran said:**
> could be wireless driver or wireless security issue with the driver, try changing the wep, wpa or wpa2.
and post the output of 
```
lspci
```to check the wireless chipset brand.
I dont think I should change the security mode
because in my device control panel (192.168.0.1) the security mode is wpa2-personal
and I chose the same thing on my ubuntu
and here is my lspci

```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.5 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 6 (rev b4)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
03:00.0 Network controller: Intel Corporation Centrino Wireless-N + WiMAX 6150 (rev 67)
05:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 30)
05:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 30)
05:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 30)
05:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 30)
06:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
```

---

### Post by gandaran on 2011-09-24
> 03:00.0 Network controller: Intel Corporation Centrino Wireless-N + WiMAX 6150 (rev 67)
I think you should try changing the security mode in the router just to check if it'll work, some Intel wireless cards/drivers are known to have this problem.

---

### Post by shevin on 2011-09-24
> **gandaran said:**
> I think you should try changing the security mode in the router just to check if it'll work, some Intel wireless cards/drivers are known to have this problem.

I have two modes in my hotspot device , WPA2-Personal AES    ,WPA/WPA2 Personal 
I tried both of them , still the same problem I dont have this problem in windows just in ubuntu

---

### Post by shevin on 2011-09-24
btw my ubuntu is 11.04 , 64 bit , fresh installed, I  have to re-connect my internet even when I am typing this post short post here, someone help me please, 

is there any driver that I should isntall ?

---

### Post by shevin on 2011-09-24
:(

---

### Post by wildmanne39 on 2011-09-24
Hi, Try this please:
To disable 802.11n on this card create /edit your /etc/modprobe.d/options.conf file like this.
Code:
```
gksu gedit /etc/modprobe.d/options.conf
```
And add the following to it.
```
options iwlagn 11n_disable=1
```
then save and exit.
Thank you

---

### Post by shevin on 2011-09-25
thanks that worked :)

---

### Post by klein de usa on 2011-09-25
hi
i have a sprint's usb virgin Mobil and i have it running on 11.04, make sure it is plugged into a 2.0 usb port , sometimes i have trouble staying connected just like you, it is a server thing the way i get around it is to start transmission and download ubuntu iso set in preferences for that torrent to limit download speed 1kib/s and limit upload speed 1kib/s this will keep you connected to the server it works for me

---

### Post by wildmanne39 on 2011-09-25
Hi, your welcome! glad I could help.

---

### Post by shevin on 2011-10-15
> **wildmanne39 said:**
> Hi, your welcome! glad I could help.

i need your help again , I upgraded to 11.10 and it stopped working again :(

---

### Post by wildmanne39 on 2011-10-15
Hi, I a lot of people are having trouble after the upgrade.

Have you tried what made your wireless work in the previous release?
Thank you

---

