---
title: "Wireless Connection difficulties-Intel 1000 BGN wireless adapter"
date: 2012-03-19
forum: New to Ubuntu
---

### Post by brainglitch on 2012-03-19
Hey everyone,

I will start this off by stating that I am completely new to Ubuntu and Linux, so please be patient with me if I seem confused at times about this question!

I just downloaded the latest version of Ubuntu. I am trying to connect to the internet on my wireless router at home and am unable to turn the wireless connectivity on. I believe that I need a specific device driver for my integrated wireless card but am not sure what to use or how to put it in.

My laptop is a Lenovo V570, and the wireless adapter is an Intel WiFi Link 1000 BGN. 

I saw what looked like a device driver for this adapter here:[http://intellinuxwireless.org/?n=Downloads](http://intellinuxwireless.org/?n=Downloads), but I am not sure how to install it correctly.

Any help or tips would be greatly appreciated. Thank you very much to anybody who replies to this thread!

---

### Post by raja.genupula on 2012-03-19
have you download that ? 
give us contents of that file , i mean what kind of file it is and  what it have in it . then we can help you on how to install .

---

### Post by brainglitch on 2012-03-19
OK.....I was very unclear last time. Again, I am a complete beginner at this!

I actually have the driver installed. When I run :

 sudo lshw -C network

I get this (I cut some out to save space):

*-network DISABLED      
      
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
   **    configuration: broadcast=yes driver=iwlagn driverversion=3.0.0**-12-gneric firmware=39.31.5.1 build 35138 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn

So,, the driver is already there. However, the network is disabled. When I try to turn it on in the Network part of Settings, I slide the little bar from Off to On. It immediately slides back to off. I know it sounds dumb, but I am at a loss to explain why it happens.

When I run sudo iwconfig, I get:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on

With sudo iwlist scan,
o        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : **Network is down**,

Now, I know that the network is not down, because when I boot up in Windows 7 I have no problem connecting at all.

Any ideas? Perhaps there is a way to connect manually through Terminal??? 

Thanks in advance!

---

### Post by brainglitch on 2012-03-19
BTW, just FYI for anyone who is looking at this: I went into System Settings and clicked on Additional Drivers. According to that, I don't have any proprietary drivers. So.....I'm pretty sure I have the right driver, now I have to figure out how to enable the wireless. 

And yes, the little switch for WiFi is turned on....:)

---

### Post by brainglitch on 2012-03-20
Any ideas anyone? How can I get the WiFi up and running on Ubuntu? It sees the wireless card and the driver, I just can't turn it on. Thanks!

---

