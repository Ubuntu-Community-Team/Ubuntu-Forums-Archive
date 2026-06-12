---
title: "New install, Wifi doesn't work"
date: 2013-07-13
forum: New to Ubuntu
---

### Post by buzz999 on 2013-07-13
Brand new to Ubuntu/Linux.  Trying to get a crappy little HP Mini netbook working better.  Was unusable  with Windows 7...dragging, hanging, lagging...ready to toss this  netbook.  So far it *flies* with Ubuntu, very happy, BUT...no wifi.  I can see all the wifi connections from my home, the neighbors, etc.  I believe it connected briefly during installation, but I can't get it to connect now.  This is a full install, or whatever you call that.  Wifi for all  other home devices working fine.  Network specs are below.  One of the moderators said it *should* work.  Wired connection working great, BTW.

Thank you in advance for your help

Machine is HP Mini 110. Ubuntu version is 13.04.  Would I have better luck with 12.04?

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev  04)
    Subsystem: Hewlett-Packard Company Device [103c:148a]
    Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:145c]
    Kernel driver in use: wl

---

### Post by JosephWraith on 2013-07-13
Hello,

I suggest you take a look a the documentation found here: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

There's a great fix for your error there.

Hope this helps!

Kindest regards,

Joseph Wraith

---

### Post by varunendra on 2013-07-13
> **buzz999 said:**
> 
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller **[COLOR="#FF0000"][14e4:4727][/COLOR]** (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:145c]
    Kernel driver in use: **[COLOR="#FF0000"]wl[/COLOR]**
Not a good driver for this card. The native one is better.
Please try -
```
sudo apt-get purge bcmwl-kernel-source
sudo modprobe brcmsmac
```
..and let us know if you can connect.

---

### Post by DGINSD on 2013-07-14
Make sure your BIOS has been updated this is what fix my  WiFi issue, along with installing the proprietary driver

---

### Post by buzz999 on 2013-07-15
> **varunendra said:**
> Not a good driver for this card. The native one is better.
Please try -
```
sudo apt-get purge bcmwl-kernel-source
sudo modprobe brcmsmac
```
..and let us know if you can connect.

Varunendra, that totally worked!  Thank you so much.  As a newbie, would you mind expaining what I did?  I can see I deinstalled something with the first command.  Regardless, much appreciated.  I'll keep this netbook now! :p

---

### Post by varunendra on 2013-07-15
> **buzz999 said:**
> would you mind expaining what I did?

Command description : The first one removed the proprietary driver (wl) and its settings, and the second one just loaded the native one (brcmsmac, would have been loaded anyway on the next boot, the second command just saved you one reboot).

Details :
Your card is supported by both the proprietary (wl) and the native (brcmsmac) broadcom drivers. The proprietary one blacklists the native ones at installation time to avoid conflict, however, itself doesn't work well with that particular card.

If you didn't install it by accepting the "Proposed" driver by "Additional Drivers" program, I suspect it must have been installed during installation if the system was connected to internet and you chose to "Install third party apps" during installation *(the installer isn't smart enough to judge the quality of drivers, so just prefers the proprietary ones if they are available)*.

So removing it not only removed the driver, but also the setting (blacklist entry) that prevents the native one from being loaded for the card.

However, the native one doesn't always work so well with every card. Sometimes, we do need to resort to the proprietary one, sometimes even a different version if needed.

---

