---
title: "I Almost have BCM43xx fixed....I think..."
date: 2008-07-13
forum: New to Ubuntu
---

### Post by gcraney on 2008-07-13
Hello all,

This is my first post here.  I know that there are many posts about BCM43xx wireless problems. I have read through many of them and still can't seem to get wireless working. 

even after going through lots of threads and all kinds of walk throughs I still can't get Hardy Heron to have anything to do w/ wirelessness (I guess my laptop just really likes Ethernet cables...)

Here is my lshw -C network output:
*-network DISABLED
description: Wireless interface
product: BCM4328 802.1a/b/g/n
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:01:00.0
logical name: wlan0
version: 03
serial: 00:1a:73:7b:09:0b
width: 64 bits
clock: 33Mhz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

iwconfig:

lo   no wireless extensions
eth0 no wireless extensions
wlan0 IEEE 802.11g ESSID:off/any
      Mode:managed Frequency:2.462GHz Access Point: Not-Associated
      Bit Rate:130Mb/s Tx-power:32 dBm
      RTS thr:2347 B Fragment thr:2346 B
      Power Management:off
      Link Quality:0 Signal level:0 Noise level:0
      Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
      Tx excessive retries:0 Invalid misc:0 Missed beacon:0

I know that my wireless network is working because that is what I'm using from another computer to post this.

I know that my network card is working on the laptop with Ubuntu on it.  I just made it a dual boot machine w/ Vista in one corner and Hardy Heron in the other.  When I boot to Vista the wireless works just fine.

I can connect through ethernet.

Any thoughts?

---

### Post by gcraney on 2008-07-13
So this just in.  I plugged it into an ehternet this morning to put compizconfig settings manager on it.  Then when I unplugged it and took it back to my desk I started WICD.  I changed wireless to wlan0 and restarted. It saw my wireless networks!! Yay.  I connected to my neighbors unprotected network, but could never connect to my WPA-PSK w/ a TKIP encryption.  How do I do this?

I have selected in WICD the only WPA security option under advanced and entered my code.  Still just bounces around forever trying to connect...

---

### Post by OttifantSir on 2008-07-13
Since Ubuntu 7.04 I haven't had the need to use ndiswrapper for my BCM43xx-card (Dell Inspiron with Dell Wireless), I just use System -> Administration -> Hardware Drivers or the driver-icon that pops up in the system tray (upper right corner).

This installs b43-fwcutter, extract the firmware and enables wireless.
Try uninstalling ndiswrapper. Also, retrace the steps from the guides, HOWTOs or whatnot you have been following, and undo all changes you've done. Delete any configuration files you may, or may not, have CREATED (not just MODIFIED!! You MUST have created the files. If you are unsure, leave them). Then see if you don't have better luck with jockey (as the program is called)

---

### Post by PinkFloyd102489 on 2008-07-13
OttifantSir, that's weird. I have an Inspiron 1720 with a bcm4328 rev 03 in it, but it didnt have anything listed in the Hardware Drivers. I had to use ndiswrapper. Now Im wanting to get rid of Ndiswrapper so I can put the card into monitor mode.


You think if I uninstall ndiswrapper, it'll pop up with fwcutter?

---

### Post by anewguy on 2008-07-13
If wicd doesn't give you all the options you need, try just network manager.  When you request to log on to a network you can specify 3 different options for wep, 2 for wpa, 2 for wpa2 and 1 for leap.  I would think you should be able to get it to work from there.  Also, be sure wpa-supplicant is installed, configured and running.

:)

---

### Post by TSS on 2008-07-13
> **PinkFloyd102489 said:**
> OttifantSir, that's weird. I have an Inspiron 1720 with a bcm4328 rev 03 in it, but it didnt have anything listed in the Hardware Drivers. I had to use ndiswrapper. Now Im wanting to get rid of Ndiswrapper so I can put the card into monitor mode.


You think if I uninstall ndiswrapper, it'll pop up with fwcutter?

I'd be interested to know this too.  I have a Broadcom 4321 card, and I use ndiswrapper.  I also always tell people to use ndiswrapper whenever they have a Broadcom problem because there is a guide ([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)) that pretty much gets the job done every time.  If it works like this though, I'll have to uninstall ndiswrapper and use this method.  Does the Hardware Drivers download the needed firmware itself?

---

### Post by oilchangeguy on 2008-07-13
see this link:
[http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware)

---

### Post by Tim Sharitt on 2008-07-13
>  Does the Hardware Drivers download the needed firmware itself?
Yes, it should download the firmware. However, it does come up with a prompt asking if you want to download it as it is non-free software.

---

### Post by OttifantSir on 2008-07-14
> **PinkFloyd102489 said:**
> You think if I uninstall ndiswrapper, it'll pop up with fwcutter?

It might. I have done the ndiswrapper route myself too, and have since forgotten how to do it as it's been working with Hardware Drivers. I had two qualms with Ubuntu until 7.04: Wireless and widescreen. Wireless became easy in 7.04, widescreen in 7.10

I would think however, that you need to restart after getting rid of ndiswrapper. Maybe only networking, but the system needs to know that it no longer has a driver for wireless. To restart only networking, in a terminal type: sudo /etc/init.d/networking restart

I hope you get it right. My Broadcom has been a good puppy for some time now.

---

### Post by PinkFloyd102489 on 2008-07-14
> **oilchangeguy said:**
> see this link:
[http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware)

My card is unsupported ( 4328 ) but thanks anyway.

---

### Post by gcraney on 2008-07-15
yeah, I never got the bcm4328 card to work w/ fwcutter.  I actually read somewhere that it doesn't work.  I am using ndiswrapper.  I did a complete clean reinstall of Hardy and just went straight into the guide found here:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

This guide works great for Ubuntu 8.04 on a HP DV2419us.

I am using a fairly difficult to configure wireless at the university I attend and it works well also.  

This problem is fixed and I am glad, now everything (including my onboard webcam) works great in Hardy on a DV2419us. YAY!

---

