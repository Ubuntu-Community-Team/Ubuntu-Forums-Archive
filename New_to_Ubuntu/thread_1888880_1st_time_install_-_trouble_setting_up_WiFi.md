---
title: "1st time install - trouble setting up WiFi"
date: 2011-11-30
forum: New to Ubuntu
---

### Post by Cruixer on 2011-11-30
Hi All, 
1st post and first full linux install yesterday. I has messed around a bit before with a pen drive version in the past and have been toying with this for years but to be honest making my mind up which version to install was baffling and I decided just to take the plunge and install Ubuntu 11.10 on my home PC.
 
I had a lot of trouble trying to install alongside Windows on my perviously partitioned home computer which already had two instances of windows. I read some stuff about problems with drives partitioned with partition magic so in the end I just scrubbed the whole thing and went with an Ubuntu only installation - my home is now a windows free zone!! The plan is eventually to set it up as a media centre PC and also to use it to learn about Linux.
 
To my problem - The install seems fine and is connected to the internet through a wired connection but where I need to move the PC to would need a wireless connection and Linux doesnt seem to 'see' my USB wirelss stick. It is a 'Buffallo AirStation Wireless G' - the information on the manufacturer site says they dont supprt linux. I have found some information by searching where people have made it work for example here but I dont really understand these at this early stage. 
 
Any help appreciated.

---

### Post by nothingspecial on 2011-11-30
Hi, welcome to the forums :)

It would help if you posted a link to the instructions you don't understand.

Also, lets see if it's detected. Open a terminal Ctrl-Alt-T and type
```

lsusb
```

Followed by ```
sudo lshw -C network
```

You will have to type your password but you won't see it. Post the resulting gobbldy gook back here. In code tags please (highlight the text then click the # in the formatting options at the top of the posting box).

---

### Post by Cruixer on 2011-11-30
Sorry, I had mean to paste in the link - it is [http://ubuntuforums.org/showthread.php?t=1831454](http://ubuntuforums.org/showthread.php?t=1831454) and there are some other links from that. The model referred to in this link may not be exactly the same as the one I have. 

I have done as you suggested and the response from the command line is below. 

Thanks for the help.

```

kenny@kenny-Dell-DM051:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 003 Device 002: ID 0461:4d22 Primax Electronics, Ltd 
kenny@kenny-Dell-DM051:~$ sudo lshw -C network
[sudo] password for kenny: 
  *-network               
       description: Ethernet interface
       product: N10/ICH 7 Family LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 01
       serial: 00:13:72:e6:43:eb
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.64 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:efbfb000-efbfbfff ioport:dcc0(size=64)
```

---

### Post by Lisiano on 2011-11-30
Judgin by the output of those 2 commands, the card is not detected by your PC. Also judging by the thread you linked here, the adapter uses a "experimental driver" of sorts. Currently there 2 courses of action
[LIST=1]
[*]Find the model with the chipset and make it work
[*]Buy a working out-of-the-box adapter
[/LIST]
We'll do the 1st choice, but before we try to find the model, try looking if Ubuntu actually noticed the card, plug it in and open Additional Drivers, see if it says anything about wireless or networking.
If that fails, we need to find the model and make it working ourselves. Judging by Google ([http://en.wikipedia.org/wiki/Buffalo_AirStation](http://en.wikipedia.org/wiki/Buffalo_AirStation)), either Buffalo releases 2 types of products under the same name or you gave us the wrong name. Try to find the box from your adapter and try to find the model (If there is a revision, also state it). For example "TL-WN722N Rev 1". If the chipset is written on the box, even better. If you threw out the box then try to find it on the adapter itself, usually on the back. The FCC ID works too.

---

### Post by Cruixer on 2011-11-30
Hi Lisiano, I think they do use the term 'Airstation' for a whole range of disimilar devices. The model I am using is WLI-U2-KG125S and on the front page of the setup guide it is referred to as a 'usb Wireless-G 125* High Speed USB 2.0 Keychain Adapter'. I tried opening additional drivers before and nothing appears there, I tried this again and tried it in a few different USB slots but nothing appears here.

---

### Post by Lisiano on 2011-11-30
Don't have a guide on how to install this yet but to anyone passing by, it seems the chipset is a Broadcom BCM4320 (Woopie... Not)

To the OP: Broadcoms are known to be... Well... Not friendly on Linux. While I'll keep looking for how to get this adapter working, start thinking about getting a new one.


EDIT: Seems rndis_wlan should be covering BCM4320
[http://linuxwireless.org/en/users/Drivers/rndis_wlan](http://linuxwireless.org/en/users/Drivers/rndis_wlan)

EDIT 2: Yes. rndis_wlan should be working. One way to find out if the PC is ACTUALLY seeing it is looking at logs. Basically what I want you to do is open a program called Log File Viewer and locate a line saying kern.log (If it is blank, like for some reason mine did, click File -> Open -> /var/log/kern.log)
Now, I want you click ANYWHERE in the window, now press these 2 buttons, Ctrl+End, plug in your USB adapter and look at the file window, once it looks like it stopped spitting out stuff, just press Shift+Ctrl+End, then Ctrl+C. Now without closing it, post it here in the code tags. In a ideal world, it would look like this, keep note that I have a different adapter so this WILL look different.
```
Nov 30 22:53:37 Lisiano-Ubuntu kernel: [119422.764070] usb 1-5: new high speed USB device number 7 using ehci_hcd
Nov 30 22:53:37 Lisiano-Ubuntu kernel: [119423.204996] usb 1-5: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
Nov 30 22:53:37 Lisiano-Ubuntu kernel: [119423.441089] ath9k_htc 1-5:1.0: ath9k_htc: HTC initialized with 33 credits
Nov 30 22:53:38 Lisiano-Ubuntu kernel: [119423.661386] ath9k_htc 1-5:1.0: ath9k_htc: FW Version: 1.3
Nov 30 22:53:38 Lisiano-Ubuntu kernel: [119423.661396] ath: EEPROM regdomain: 0x809c
Nov 30 22:53:38 Lisiano-Ubuntu kernel: [119423.661400] ath: EEPROM indicates we should expect a country code
Nov 30 22:53:38 Lisiano-Ubuntu kernel: [119423.661406] ath: doing EEPROM country->regdmn map search
Nov 30 22:53:38 Lisiano-Ubuntu kernel: [119423.661410] ath: country maps to regdmn code: 0x52
Nov 30 22:53:38 Lisiano-Ubuntu kernel: [119423.661415] ath: Country alpha2 being used: CN
Nov 30 22:53:38 Lisiano-Ubuntu kernel: [119423.661419] ath: Regpair used: 0x52
Nov 30 22:53:38 Lisiano-Ubuntu kernel: [119423.661426] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
...snip...
Nov 30 22:53:38 Lisiano-Ubuntu kernel: [119423.661966] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
Nov 30 22:53:38 Lisiano-Ubuntu kernel: [119423.667346] cfg80211: Calling CRDA for country: CN
Nov 30 22:53:38 Lisiano-Ubuntu kernel: [119423.667492] ieee80211 phy2: Atheros AR9271 Rev:1
Nov 30 22:53:38 Lisiano-Ubuntu kernel: [119423.670390] Registered led device: ath9k_htc-phy2
Nov 30 22:53:38 Lisiano-Ubuntu kernel: [119423.670401] usb 1-5: ath9k_htc: USB layer initialized
Nov 30 22:53:38 Lisiano-Ubuntu kernel: [119423.671234] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
...snip...
Nov 30 22:53:38 Lisiano-Ubuntu kernel: [119423.671282] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Nov 30 22:53:38 Lisiano-Ubuntu kernel: [119423.671284] cfg80211: Disabling freq 2484 MHz
Nov 30 22:53:38 Lisiano-Ubuntu kernel: [119423.671287] cfg80211: Regulatory domain changed to country: CN
Nov 30 22:53:38 Lisiano-Ubuntu kernel: [119423.671288] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 30 22:53:38 Lisiano-Ubuntu kernel: [119423.671290] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Nov 30 22:53:38 Lisiano-Ubuntu kernel: [119423.671292] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm)
Nov 30 22:53:38 Lisiano-Ubuntu kernel: [119423.905890] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 30 22:53:38 Lisiano-Ubuntu kernel: [119424.106497] userif-3: sent link down event.
Nov 30 22:53:40 Lisiano-Ubuntu kernel: [119424.106505] userif-3: sent link up event.
Nov 30 22:53:40 Lisiano-Ubuntu kernel: [119426.240880] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 30 22:53:41 Lisiano-Ubuntu kernel: [119427.562234] wlan0: authenticate with 00:11:22:33:44:55 (try 1)
Nov 30 22:53:41 Lisiano-Ubuntu kernel: [119427.564816] wlan0: authenticated
Nov 30 22:53:42 Lisiano-Ubuntu kernel: [119427.672403] wlan0: associate with 00:11:22:33:44:55 (try 1)
Nov 30 22:53:42 Lisiano-Ubuntu kernel: [119427.675307] wlan0: RX AssocResp from 00:11:22:33:44:55 (capab=0x411 status=0 aid=2)
Nov 30 22:53:42 Lisiano-Ubuntu kernel: [119427.675316] wlan0: associated
Nov 30 22:53:42 Lisiano-Ubuntu kernel: [119427.682718] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
```
It's ok if it seems giberish to you. Some of it is giberish to me, for example the capability codes. Anyway. This will tell us what the kernel, AKA the Heart and Brain of Linux thinks when you plug in a USB adapter.

---

### Post by Cruixer on 2011-11-30
Hi Lisiano,
I've a feeling that the USB adaptor is now not working at all. Prior to seeing your last post I tried it in my work laptop and windows 7 didnt appear to be seeing it either. I followed your instructions and nothing happens in the Log File Viewer when I plug in the USB Adaptor. I verified that I was not doing anything daft by plugging in a USB flash drive and the events rack up, tried the USB Adaptor again and nothing happens. 
 
This is strange as it was working in XP immediately prior to installing linux on the same machine but may just have been a coincidence that it has packed at the same time as the new install. I presume if nothing happens in the Log File Viewer the USB Adaptor is dead? When plugged in there is a green led on the Adaptor, it glows noticibly bright green for a moment when plugged in then dims.

---

### Post by Lisiano on 2011-11-30
If absolutely nothing get's printed in the log, then you can assume it's either Very Linux incompatible or dead. I would advise getting a new USB adapter, but before you make your purchase, check in with us. Also any adapter with an Atheros chipset will work out of the box. I have one that's kinda new and it didn't work before, now it works marvelously.

Also it's a very weird coincidence. If I were you, I'd try it on a friends PC, it doesn't matter if they run XP or Vista or even 7. Just ask if you can see if the adapter is still working and plug it in, if Windows starts installing drivers or says "Hey, feed me drivers" or just asks where you want to connect, then it's just Very Linux incompatible.

EDIT: About the LED, the power is still supplied to the adapter so probably that's why it is green for a while then "dead".

---

### Post by bluexrider on 2011-11-30
> **Cruixer said:**
> Hi Lisiano,
I've a feeling that the USB adaptor is now not working at all. Prior to seeing your last post I tried it in my work laptop and windows 7 didnt appear to be seeing it either. I followed your instructions and nothing happens in the Log File Viewer when I plug in the USB Adaptor. I verified that I was not doing anything daft by plugging in a USB flash drive and the events rack up, tried the USB Adaptor again and nothing happens. 
 
This is strange as it was working in XP immediately prior to installing linux on the same machine but may just have been a coincidence that it has packed at the same time as the new install. I presume if nothing happens in the Log File Viewer the USB Adaptor is dead? When plugged in there is a green led on the Adaptor, it glows noticibly bright green for a moment when plugged in then dims.

its funny how sometimes you turn "ON" the light switch and theres "POP" and then the light goes out and you find yourself in the dark. :confused:

---

### Post by Cruixer on 2011-12-01
I am fairly confident now that the USB stick is 'gubbed'!! Still it was a worthwhile experience for me as I learned a bit about using the command line etc, already Linux seems a lot more accesable than windows when trying to diagnose something. I've just run a telephone extension cable around the outside of the room to reposition the router where the PC needs to go so that I have the internet for now.
 
Thanks Luciano for all your help (and nothingspecial at the start too).

---

### Post by nothingspecial on 2011-12-01
No problem :)

Feel free to ask if you have any more questions.

---

