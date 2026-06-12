---
title: "HELP !!!low screen reslolution and no wireless"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by cello_911 on 2008-05-30
Hi, 
Can anyone help I have just installed onto a fujitsu siemans esprimo mobile laptop ubuntu 8.04 lts ,, the problem i have it only gives me a low screen resolution of 800 x 600 ,how do i get a higher resolution.... also There is no wireless showing , please can you give me step by step advice as how to resolve this two issues.. 

Many thanks 

Cello_911

---

### Post by ukripper on 2008-05-30
> **cello_911 said:**
> Hi, 
Can anyone help I have just installed onto a fujitsu siemans esprimo mobile laptop ubuntu 8.04 lts ,, the problem i have it only gives me a low screen resolution of 800 x 600 ,how do i get a higher resolution.... also There is no wireless showing , please can you give me step by step advice as how to resolve this two issues.. 

Many thanks 

Cello_911

Can you run following commands in termianl and paste the output here

```
lspci
```

```
iwconfig
```

---

### Post by khehla on 2008-10-18
I have same problem as above. Could you help me instead :D ?
thanks...


lspi:
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.

---

### Post by stanwow on 2008-10-18
First,you can click into:system-hardware drivers,and maybe you can find out it support you to enable the driver that fit for your graphic card.(I did it on my laptop just like that).

Second,your wireless device is the same as mine.And I just make it run several days ago.And I will just tell you what I have done,I hope you can fix it.
1.
> sudo apt-get install --reinstall build-essential linux-headers-`uname -r`

2.remove the madwifi-tools
> sudo apt-get remove --purge madwifi-tools

3.Go to this website([http://snapshots.madwifi.org/](http://snapshots.madwifi.org/)) to download the file:madwifi-hal-0.10.5.6-current.tar.gz

4.> tar zxf madwifi-hal-0.10.5.6-current.tar.gz

5.> cd madwifi-hal-0.10.5.6-current.tar.gz

6.> make
sudo make install

7.> sudo modprobe ath_pci

And that will be done.When you want to connect with the wireless device,you must use the step7.

I just do it like that.I hope you will be successful in fixing the wireless.
You can search in the forum to find more.

---

### Post by khehla on 2008-10-18
Hi Stanwow,

I followed steps for wireless and seemed to work, but hard to check cos no wireless in my current area (I am in portugal, setting up ubuntu for friend who will go back to uk).

Thanks for that. Anyway to check that it is working. I have this now:
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:23979  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ppp0      no wireless extensions.


I presume there is no way to get some gui to control the wireless??

Also, for the graphics driver (Atheros Hardware Access Layer (HAL)) I found some stuff on it

[http://ubuntuforums.org/showthread.php?t=766529](http://ubuntuforums.org/showthread.php?t=766529)

, but really it did not make ANY difference. I'm a bit of a newbie myself. Any further tips on graphics drivers. I saw a thread on changing resolution by going into the appropriate files, but can't find that thread now!!

Any further help would be greatly appreciated

---

### Post by stanwow on 2008-10-18
> **khehla said:**
> Hi Stanwow,

I followed steps for wireless and seemed to work, but hard to check cos no wireless in my current area (I am in portugal, setting up ubuntu for friend who will go back to uk).

Thanks for that. Anyway to check that it is working. I have this now:
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:23979  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ppp0      no wireless extensions.


I presume there is no way to get some gui to control the wireless??

Also, for the graphics driver (Atheros Hardware Access Layer (HAL)) I found some stuff on it

[http://ubuntuforums.org/showthread.php?t=766529](http://ubuntuforums.org/showthread.php?t=766529)

, but really it did not make ANY difference. I'm a bit of a newbie myself. Any further tips on graphics drivers. I saw a thread on changing resolution by going into the appropriate files, but can't find that thread now!!

Any further help would be greatly appreciated



You can try this command:
> lsmod | grep ath
And if you have set your wireless fine,it will list something like this:
ath_rate_sample 16128 1
ath_pci 193324 0
wlan 252272 5 wlan_tkip,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal 280416 3 ath_rate_sample,ath_pci

if not,try step 7 again:
> sudo modprobe ath_pci


Make sure that Atheros Hardware Access Layer (HAL) is ticked(enabled),although it will appear to be "no use",but you can now use the wireless.

And you can find if there is a "wireless connection" in the network management.

Good luck!!!!

---

### Post by stanwow on 2008-10-18
By the way,the Atheros Hardware Access Layer (HAL) is not for the graphic cards, but for the wireless.

About your graphic card, maybe you can go to the wiki to find the drivers right for your laptop.

---

### Post by khehla on 2008-10-19
ah yes, sorry about that..just some confusion cos I had so many pages open :D
I'll try the wiki, thanks

---

