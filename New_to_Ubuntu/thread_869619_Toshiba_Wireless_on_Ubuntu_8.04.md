---
title: "Toshiba Wireless on Ubuntu 8.04"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by xnerdx on 2008-07-25
Hi everyone,
    I am still new to Ubuntu and just recently purchased a Toshiba laptop. It came preloaded with Windows Vista *gag* so I formated the HDD and installed Ubuntu 7.10 and upgraded to 8.04. Now the problem my laptop has a built in wireless card that I can't get Ubuntu to bring up. I have a Toshiba Satellite A205-S5000. It has a built in 'network card' so I can use that for Ethernet connection but when I am on the move I do not have access to my WiFi! If anyone could help me pull up my WiFi I would be more than appreciative! I really don't want to go back to Windows... On a side note I am starting to learn to write in C# and I was wondering if anyone could help me get the tools and such to write and compile my code on Ubuntu 8.04. Thank you!

---

### Post by adult swim on 2008-07-25
lets see what type of wireless card you have.
if you go to applications/accessories/terminal 
open the terminal and they type in 
```
lspci
```
copy the information that it returns and paste it here.

---

### Post by stchman on 2008-07-25
> **xnerdx said:**
> Hi everyone,
    I am still new to Ubuntu and just recently purchased a Toshiba laptop. It came preloaded with Windows Vista *gag* so I formated the HDD and installed Ubuntu 7.10 and upgraded to 8.04. Now the problem my laptop has a built in wireless card that I can't get Ubuntu to bring up. I have a Toshiba Satellite A205-S5000. It has a built in 'network card' so I can use that for Ethernet connection but when I am on the move I do not have access to my WiFi! If anyone could help me pull up my WiFi I would be more than appreciative! I really don't want to go back to Windows... On a side note I am starting to learn to write in C# and I was wondering if anyone could help me get the tools and such to write and compile my code on Ubuntu 8.04. Thank you!

That model appears to have the 3945 wireless card.  That card should work OOB with Ubuntu.

---

### Post by bbqsandwich on 2008-07-25
The user in this thread is also having the same problem:

[http://ubuntuforums.org/showthread.php?t=867773](http://ubuntuforums.org/showthread.php?t=867773)

I suspect we will see a few more questions from owners of this model; Wal-Mart has been having a sale on them...

---

### Post by markab9569 on 2008-07-25
I have the same problem with the same computer and am getting some help at the following thread.

[http://ubuntuforums.org/showthread.php?t=867773](http://ubuntuforums.org/showthread.php?t=867773)

I am having trouble getting my Toshiba on the net, with the ethernet connection too.

Did you have any problems with that?

---

### Post by xnerdx on 2008-07-25
```
michael@michael-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
0c:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0c:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0c:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0c:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```

There is the information requested by Adult Swim, also I didn't have any problems with the Ethernet connection. Wal-mart had some like 'limited supply' sale and so I had to get my hands on one :).

---

### Post by xnerdx on 2008-07-25
Also, I tried to use the following tutorial to configure my wifi
```
http://ubuntuforums.org/showthread.php?t=718244&highlight=Atheros
```
Didn't work... My computer doesn't recognize any ath0 or wlan0 just eth0.

---

### Post by germanix on 2008-07-25
[http://www.linuxmint.com/wiki/index.php/MintWifi](http://www.linuxmint.com/wiki/index.php/MintWifi)
I do not have the same machine but I had the same problem. If you follow the link above you will find full instructions on how to connect to wifi. It is on the Linux Mint page but it works as well on Ubuntu.

---

### Post by silverglade00 on 2008-07-25
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


Atheros chipset needs the madwifi package installed.

---

### Post by xnerdx on 2008-07-25
> **silverglade00 said:**
> 05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


Atheros chipset needs the madwifi package installed.

I went through this tutorial as an attempt to install madwifi to run the Atheros chipset
```
http://ubuntuforums.org/showthread.php?t=718244&highlight=Atheros
```
No luck.

> **germanix said:**
> [http://www.linuxmint.com/wiki/index.php/MintWifi](http://www.linuxmint.com/wiki/index.php/MintWifi)
I do not have the same machine but I had the same problem. If you follow the link above you will find full instructions on how to connect to wifi. It is on the Linux Mint page but it works as well on Ubuntu.

Same thing, I went through this with not much luck... Might I add that the drivers for my Wireless card are run under "restricted devices" under linux ubuntu? I see no wireless selection in the Network Manager and I tried right clicking and pressing 'Edit wireless networks' yet there are no networks under the network selection. Please help

---

### Post by germanix on 2008-07-25
When you go to System-Administration-Network, do you see a wifi connection there at all?

---

### Post by bluzepher on 2008-07-25
I just found this site which might help you with your Toshiba wireless Woes >>


How to: Install Ubuntu Hardy Heron on a Toshiba l40-10O

[http://www.catswhocode.com/blog/os/gnu-linux/how-to-install-ubuntu-hardy-heron-on-a-toshiba-l40-10o-17](http://www.catswhocode.com/blog/os/gnu-linux/how-to-install-ubuntu-hardy-heron-on-a-toshiba-l40-10o-17)

Good Luck

---

### Post by xnerdx on 2008-07-25
> **germanix said:**
> When you go to System-Administration-Network, do you see a wifi connection there at all?

No I don't under the Connections tab it just says Wired Connection (Roaming mode enabled) and Point to Point Connection

---

### Post by xnerdx on 2008-07-25
> **bluzepher said:**
> I just found this site which might help you with your Toshiba wireless Woes >>


How to: Install Ubuntu Hardy Heron on a Toshiba l40-10O

[http://www.catswhocode.com/blog/os/gnu-linux/how-to-install-ubuntu-hardy-heron-on-a-toshiba-l40-10o-17](http://www.catswhocode.com/blog/os/gnu-linux/how-to-install-ubuntu-hardy-heron-on-a-toshiba-l40-10o-17)

Good Luck

No luck my friend, this is becoming more of a pain than it really should be! Please any idea's?

---

### Post by xnerdx on 2008-07-25
Hey,
   I just fixed the problem, all I had to do was go to this thread:
```
http://ubuntuforums.org/showthread.php?t=861683&highlight=toshiba
```
I ran the codes in the terminal and ran
```
sudo reboot
```
Let the computer reboot and then when it loaded back up I had wireless access!!! Thanks for the attempt guys!

---

### Post by DagMan on 2008-07-26
Not all the atheros cards are supported by what's out of the box in ubuntu apparently.  mine was like that and as you can see from the link it's specific to a particular laptop, however this might be the way for some others as well.
[http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly#enabling_wifi](http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly#enabling_wifi)
I initially followed a differant guide as there seems to be more than one madwifi driver out there, and both drivers in fact can work for me. It the other one I had to do the extra step of disabling the linux-restricted-modules-common boot script because it was loading a conflicting module.  If you find this works for you but still need restricted modules, perhaps putting them in /etc/modules will work just as well... not really sure and it seems it would be a case by case basis.
The other driver that worked was basically the same little tutorial but with this driver [http://snapshots.madwifi.org/special/madwifi-hal-0.10.5.6-r3698-20080604.tar.gz](http://snapshots.madwifi.org/special/madwifi-hal-0.10.5.6-r3698-20080604.tar.gz)
also I had to add to /etc/modules ath_pci

---

