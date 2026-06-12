---
title: "~~Linksys WPC54G WIRELESS CARD~~"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by watsgoodg on 2008-11-21
I have read threat after thread and nothing has worked. Tried installing windows wireless drivers and its still not working. Can someone finally help me out with this issues.

Thanks.

---

### Post by wolfen69 on 2008-11-21
i am not an expert with wireless, but if you can not get this card to work, why not sell it and buy one that *is* compatible? it will save you alot of frustration.

how long have you been working on this problem? what have you tried?

---

### Post by Michael.Godawski on 2008-11-21
[FONT=Verdana]If I am correct the linksys card is based on a broadcom chipset. So a lot of troubles are before you. Try this:

[https://help.ubuntu.com/community/WifiDocs/Device/LinksysWPC54GS-UK](https://help.ubuntu.com/community/WifiDocs/Device/LinksysWPC54GS-UK)

Please post the result of this command:
[/FONT][FONT=Verdana]```
sudo lspci
```

If you have a [/FONT]Broadcom chip. Saionara... Get another card.

---

### Post by watsgoodg on 2008-11-21
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
07:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by Michael.Godawski on 2008-11-21
Not good. 

Try this: 
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

What version of Ubuntu are you using?

---

### Post by watsgoodg on 2008-11-21
8.10 


 sudo lspci -n
00:00.0 0600: 8086:1a30 (rev 04)
00:01.0 0604: 8086:1a31 (rev 04)
00:1d.0 0c03: 8086:2482 (rev 02)
00:1e.0 0604: 8086:2448 (rev 42)
00:1f.0 0601: 8086:248c (rev 02)
00:1f.1 0101: 8086:248a (rev 02)
00:1f.5 0401: 8086:2485 (rev 02)
00:1f.6 0703: 8086:2486 (rev 02)
01:00.0 0300: 1002:4c57
02:00.0 0200: 10b7:9200 (rev 78)
02:01.0 0607: 104c:ac51
02:01.1 0607: 104c:ac51
07:00.0 0280: 14e4:4320 (rev 03)

---

### Post by Michael.Godawski on 2008-11-21
I have found a very long thread dealing with broadcom and 8.10. 
[http://ubuntuforums.org/showthread.php?t=963978](http://ubuntuforums.org/showthread.php?t=963978)

I know your pain mate. I had also a braodcom wlan card in my dell notebook. The last solution I saw after countless hours of tweaking and screwing up my whole system ( it was fun though) I just smashed the wlan card and bought another one which IS compatible with linux.

---

### Post by watsgoodg on 2008-11-21
ls /lib/modules/`uname -r`/volatile
ath_hal.ko            ath_rate_onoe.ko    wlan.ko           wlan_wep.ko
ath_pci.ko            ath_rate_sample.ko  wlan_scan_ap.ko   wlan_xauth.ko
ath_rate_amrr.ko      wlan_acl.ko         wlan_scan_sta.ko  wl.ko
ath_rate_minstrel.ko  wlan_ccmp.ko        wlan_tkip.ko


echo `uname -r`
2.6.27-7-generic

---

### Post by watsgoodg on 2008-11-21
sudo modprobe -r b43 ssb bcm43xx wl
[sudo] password for test: 
FATAL: Module bcm43xx not found.


sudo depmod -a

udo /etc/init.d/networking restart
 * Reconfiguring network interfaces...

---

### Post by watsgoodg on 2008-11-21
i think im just going to go back to xp and call it a day...wait until the next release of ubuntu and try it then...

---

### Post by sdowney717 on 2008-11-21
[http://ubuntuforums.org/showthread.php?t=340689](http://ubuntuforums.org/showthread.php?t=340689)
broadcom 4306 was working back in 2006
I have a pci br4318 and it works with the ndisgtk sys

I found a link to an old post where I got one working using this
[http://ubuntuforums.org/showthread.php?t=407081](http://ubuntuforums.org/showthread.php?t=407081)

here is a source sys file for a BR4325 
This was the only one that worked for me, the one on the drivers was not working and someone kindly made the right modifications
[http://ubuntuforums.org/showthread.php?t=741959](http://ubuntuforums.org/showthread.php?t=741959)

---

### Post by xenolalia on 2008-12-09
Hi watsgoodg!

I also had a few issues with configuring a WPC54G in ubuntu.  I remember sifting through thread after thread about complicated ndiswrapper-related command line procedures, to no avail.  In the end, I found a very good ndiswrapper GUI -- ndisgtk, which turned out to be the simplest solution for me.

Although it sounds like your internet problems are more hardware-related :) than mine were, here's a link to a short howto I wrote a while ago about configuring Linksys wireless cards in ubuntu 8.04.1 (written with the WPC54G in mind): [http://ubuntuforums.org/showthread.php?t=919964](http://ubuntuforums.org/showthread.php?t=919964).

Good luck!
xenolalia

---

### Post by 3rdalbum on 2008-12-09
> **watsgoodg said:**
> i think im just going to go back to xp and call it a day...wait until the next release of ubuntu and try it then...

Wrong attitude. It's not a problem with Ubuntu, it's a problem with Broadcom. Waiting until the next release of Ubuntu is likely to do diddly-squat because Broadcom does not cooperate with the free software community.

Buy a new wireless card... seriously, they're cheap as chips. And then tell Broadcom that you had to buy a new wireless card because theirs don't work on Linux.

---

