---
title: "internet not working"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by sabti on 2008-05-21
I just installed Ubuntu 8.04 and the internet doesn't work. wired internet is fine but i can't seem to get the wireless to work... i have a broadcom 4318 wireless card on an aspire 5100 and i do understand there are some driver issues but it seems like this time when i installed it it actaully recognized the card.... my question is... how do i check if my hard is installed properly and if it is... how do i log onto the internet using wireless... i can't seem to find a list like windows has that tells me the wireless signals in the area... i'm an absolute noob but i want to make the switch to linux thanks!

---

### Post by kilroy423 on 2008-05-21
you need to double check to make sure your card is detected with

lsusb
iwconfig
ifconfig

if you could post those it will help us help you

Kilroy

---

### Post by sabti on 2008-05-21
thanks 4 the promp reply kilroy!!

sabti@Betoola:~$ lsusb
Bus 003 Device 002: ID 0402:5602 ALi Corp. Video Camera Controller
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

sabti@Betoola:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


sabti@Betoola:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d4:1d:ab:bf  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fe1d:abbf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1024 errors:0 dropped:0 overruns:0 frame:0
          TX packets:894 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:812718 (793.6 KB)  TX bytes:121475 (118.6 KB)
          Interrupt:21 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:194 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9700 (9.4 KB)  TX bytes:9700 (9.4 KB)

thanks

---

### Post by Xiong Chiamiov on 2008-05-21
> **sabti said:**
> thanks 4 the promp reply kilroy!!
Prompty reply?  He waited 25 minutes!  You obviously haven't been around the Ubuntu forums very much. ;)

It seems that your wireless isn't installed.  I'm not an expert by any means on these things, but could you please post the output of
```

lspci

```
preferably between [ code ][/ code] tags.

---

### Post by sabti on 2008-05-21
lets see how promt this will be :P

sabti@Betoola:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
sabti@Betoola:~$

---

### Post by Xiong Chiamiov on 2008-05-21
[It appears]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom?highlight=%28wireless%29") that you'll have to use [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") to get it to work.  Blegh.  Not the most enjoyable thing, but we're here to help.

---

### Post by kilroy423 on 2008-05-21
> Prompty reply? He waited 25 minutes! You obviously haven't been around the Ubuntu forums very much. :'( I try and grab the unanswered ones, although he is right it was a slow reply.

try this

```
modprobe bcm43xx
```

if not ndiswrapper usually will do the trick, this should still work

[http://ubuntuforums.org/showthread.php?t=285809](http://ubuntuforums.org/showthread.php?t=285809)

Kilroy

---

### Post by sabti on 2008-05-21
how do i go about doing that? is there instructions for th 4318 card that i have?

---

### Post by Xiong Chiamiov on 2008-05-21
> **kilroy423 said:**
> :'( I try and grab the unanswered ones, although he is right it was a slow reply.


Sorry if that sounded insulting at all.  It was meant to be a light-hearted jest about the insane response speed of these forums, not pointed at you.

And yes, unanswered posts ftw.

---

### Post by Xiong Chiamiov on 2008-05-21
> **sabti said:**
> how do i go about doing that? is there instructions for th 4318 card that i have?
Just start [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-715b64e4eb010761a0c694dde40d3a569f414b5e") and tell us when you get stuck.

---

### Post by tashmooclam on 2008-05-21
I found the solutions to the Broadcom card problem unsatisfactory. My solution was to spend $25 on eBay for an Intel card.It took just a few minutes to swap it. This solved the problem immediately, since Intel drivers are already in Ubuntu. It was definitely the best $25 I ever spent. Note that the Dell Ubuntu laptops have Intel cards. There is a reason for it.

---

### Post by sabti on 2008-05-21
sabti@Betoola:~$ modprobe bcm43xx
WARNING: Error inserting ieee80211_crypt (/lib/modules/2.6.24-16-generic/kernel/net/ieee80211/ieee80211_crypt.ko): Operation not permitted
WARNING: Error inserting ieee80211 (/lib/modules/2.6.24-16-generic/kernel/net/ieee80211/ieee80211.ko): Operation not permitted
WARNING: Error inserting ieee80211softmac (/lib/modules/2.6.24-16-generic/kernel/net/ieee80211/softmac/ieee80211softmac.ko): Operation not permitted
FATAL: Error inserting bcm43xx (/lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko): Operation not permitted

---

### Post by sabti on 2008-05-21
incase the xx was supose to be for me to fill in

sabti@Betoola:~$ modprobe bcm4318
FATAL: Module bcm4318 not found.

---

### Post by iaculallad on 2008-05-21
Or try peeking in [here]("http://ubuntuforums.org/showthread.php?t=318539") for wireless issues.

---

### Post by tashmooclam on 2008-05-21
See what I mean? A screwdriver, eBay and paypal are much easier to fathom.

---

### Post by kilroy423 on 2008-05-21
> Sorry if that sounded insulting at all.

It's all good no insult taken

sabti make sure and let us know how it goes either way, we will get you through this


Kilroy

---

### Post by Xiong Chiamiov on 2008-05-21
Whenever you get a permission error, generally the first thing to try is adding sudo to the front of it.  Alternatively, 
```

sudo !!

```
will run the last command given as root.

---

### Post by sabti on 2008-05-21
so... 
i installed ndiswrapper and i got the "windows wireless drivers" thing under administrator... i found my driver and loaded it up in the ndiswrapper GUI but i don't see wlan0 under ifconfig or iwconfig help?

---

### Post by bradford72 on 2008-05-21
What worked for me was a program called ndiswrapper...if I could remember where I found it would be real cool...I'm looking for it now...if I find it fast, I'll let ya know

---

### Post by sabti on 2008-05-21
i am using ndiswrapper and i got the driver from there website to my corrosponding wireless card but ifconfig and iwconfig doens't show a wlan0

---

### Post by sabti on 2008-05-21
sabti@Betoola:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
sabti@Betoola:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d4:1d:ab:bf  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fe1d:abbf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2333 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1793 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1825205 (1.7 MB)  TX bytes:232345 (226.8 KB)
          Interrupt:21 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:194 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9700 (9.4 KB)  TX bytes:9700 (9.4 KB)


when i click on the network manager on the top right hand corner of the PC i don't see my wireless networks even though i have the roaming engaged.... whats going on`

---

### Post by sabti on 2008-05-21
sorry double post

---

### Post by sabti on 2008-05-21
SOLVED!!!!!!!!!!!!! thank you guys!

---

### Post by kilroy423 on 2008-05-22
> SOLVED!!!!!!!!!!!!! thank you guys!

ndiswrapper did the trick??


Kilroy

---

