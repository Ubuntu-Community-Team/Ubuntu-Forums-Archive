---
title: "Atheros Wireless"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by Zergpack on 2008-05-24
I am using Atheros AR5007EG wireless on my laptop. 8.04 is supposted to support this card and i enabled the driver but it doesn't connect to any wireless networks in my house. I've been having this problem a while, even back using 7.10, and i've never gotten it to work. ndiswrapper didn't work. Any sugestions?

---

### Post by diablo75 on 2008-05-25
> **Zergpack said:**
> I am using Atheros AR5007EG wireless on my laptop. 8.04 is supposted to support this card and i enabled the driver but it doesn't connect to any wireless networks in my house. I've been having this problem a while, even back using 7.10, and i've never gotten it to work. ndiswrapper didn't work. Any sugestions?

When you say "it doesn't connect", does this mean you are able to see nearby wireless networks to select from, or do those not show up at all?

Also, in System>Administration>Hardware Drivers, does it show the driver status as enabled (with a green light, instead of a red light)?

---

### Post by Zergpack on 2008-05-25
> **diablo75 said:**
> When you say "it doesn't connect", does this mean you are able to see nearby wireless networks to select from, or do those not show up at all?

Also, in System>Administration>Hardware Drivers, does it show the driver status as enabled (with a green light, instead of a red light)?

I type in the ESSID of my wireless router and i never get any signal no matter how close i am. I can't find anything that will search for wireless networks

under hardware drivers it is green, i make sure it is before i attempt to connect.

---

### Post by diablo75 on 2008-05-25
Could you type "iwconfig" into a terminal window and paste the output in here?

On the side, you can use Synaptic Package Manager to lookup a program called wifi-radar.  It's a wireless connection manager that you can use to browse wireless networks and connect to them.  Although you should already have the default network manager icon at the top in your task bar.  From the sounds of it, you've already disable roaming mode by entering manual settings.  Go back and re-enable roaming mode, restart, and left-click on the network connection icon at the top to see if it shows you any wireless networks (the icon is reminiscent of two computer screens overlapping each other diagonally, becoming "cell phone bars" after a wireless connection is established).

Also, does your computer have a switch for enabling/disabling your wireless adapter?  I've seen laptops where people accidentally disabled their wireless card simply by accidentally hitting Fn-F2.  You may have to disable this feature in your bios so the card is always on.

---

### Post by DrTaylor on 2008-05-25
I had the same problem with Gutsy - wondered if it would work in Hardy. Question answered.

Anyway, you need to get the drivers by using Synaptic to download the madwifi driver for Atheros.

And, just to make it more amusing, it still doesn't work. There's a patch that needs downloading and installing from the madwifi website.

At least that's how it works in Gutsy Gibbon.

---

### Post by Zergpack on 2008-05-25
> **diablo75 said:**
> Could you type "iwconfig" into a terminal window and paste the output in here?

On the side, you can use Synaptic Package Manager to lookup a program called wifi-radar.  It's a wireless connection manager that you can use to browse wireless networks and connect to them.  Although you should already have the default network manager icon at the top in your task bar.  From the sounds of it, you've already disable roaming mode by entering manual settings.  Go back and re-enable roaming mode, restart, and left-click on the network connection icon at the top to see if it shows you any wireless networks (the icon is reminiscent of two computer screens overlapping each other diagonally, becoming "cell phone bars" after a wireless connection is established).

Also, does your computer have a switch for enabling/disabling your wireless adapter?  I've seen laptops where people accidentally disabled their wireless card simply by accidentally hitting Fn-F2.  You may have to disable this feature in your bios so the card is always on.

I downloaded wifi-radar but not sure if it works, our routers don't broadcast for security reasons. I set back to roaming and restarted and went into the BIOS to set my wireless card to be on all the time and it doesn't have that option. my fn button doesn't work in ubuntu to my knowledge because i have messed with it before wondering if that cause my problem. On every reboot my hardware is enabled but reverts back to red saying not in use, i fix it by disabling it and reenabling it. 

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by discodover on 2008-05-25
I have the same chipset and the same problem.  Even though the card is detected and the restricted driver is being used, I could not see any wireless networks.  I followed the instructions [[COLOR="DarkOrchid"]here[/COLOR] ]("http://blog.linuxoss.com/2008/05/08/ubuntu-804-enabling-atheros-ar5007-based-wireless/")to get everything working.

Hope this helps.

---

### Post by Keiyentai on 2008-06-02
Thank you for posting that link. It fixed my wifi for my laptop :) Now I have even less reason to use windows hehe:lolflag:

---

### Post by liquerLOVER on 2008-06-04
This works for Acer Aspire 4520 with Atheros AR5007EG. With this kind of installation, you doesn't need to connected to internet. I install this for THREE times to make sure I didn't left any steps before i'm post this on the forums. If there is any mistake, please inform me because i'm a TOTAL newbie with Linux. This is my fifth week with Linux.

First, download this madwifi from this link:

[http://snapshots.madwifi.org/special...+ar5007.tar.gz](http://snapshots.madwifi.org/special...+ar5007.tar.gz)

Secondly, extract it to your home folder.

Third, you need to add your install CD as a installation source. Just follow the instruction below:

System &#8594; Administration &#8594; Synaptic Package Manager &#8594; Settings &#8594; Repositories &#8594; Third Party Software &#8594; Add CD-ROM.

Next, just wait fow a few minutes until the package manager have finish working. You will notice a grey colour "gear" beside the wireless network symbol on the top panel when it still working. If you place the cursor on that gear, it will saying "a package manager is working." After the package manager had finish, it will disappear automaticaly.

For the next step:

sudo apt-get install g++

Then, it will ask conformation from you to install or not. Just type "y" and press enter.

Next step:

cd madwifi-nr-r3366+ar5007/
sudo make
sudo make install
sudo modprobe ath_pci
gksudo gedit /etc/modules

After that, add this line at the bottom: ath_pci

Save, exit and reboot and PRESTO !!!

I'm not too sure whether this work for other laptop with AR5007EG or other AR5007. If this works, thank all the family member in this forum & me. However, if it doesn't works for you, try to look for other solution in this VERY-VERY friendly and caring family forums.

p/s: Can anyone help me with my graphic card? I'm using GeForce 7000m. Now I'm on Ubuntu with 800x600 screen. Post me a working solution. OK dude??? Chowlobetty...

---

### Post by liquerLOVER on 2008-06-04
try this link. the one that i post just now is error:
[http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz)

---

