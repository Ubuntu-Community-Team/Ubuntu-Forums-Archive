---
title: "Wireless Connection on New Install"
date: 2012-03-17
forum: New to Ubuntu
---

### Post by czechman45 on 2012-03-17
Hi all,  I'm very new to Ubuntu, so this is probably a pretty common question.  I've checked the forums for answers to it, but so far the things I've found either don't apply or don't work.

So, I just installed Ubuntu 11.10 onto my machine (Dell Inspiron).  My wireless internet was working fine with Windows XP and still is.  However, when I try to run it in Ubuntu, it doesn't work.

First, I found advice to run iwconfig in the terminal.  After a bunch of other stuff, it said 'disabled'.  Then I tried to change this with the dell keyboard wireless control.  I checked iwconfig and still got the same thing.  

I then realized that there was a drop down menu on the top right of the desktop for network connections.  It said 'wireless connection', but it was grayed out and said firmware missing.  I followed another person's advice and went to System Settings->  Additional Drivers.  It searched for and installed a new driver (Broadcom STA wireless driver) and then I restarted.  

Now when I run iwconfig nothing wireless related even  shows up.  Also, no wireless shows up on the drop down menu on the desktop.  I can only see 'wireless connection 1' and 'VPN connections'.  

What do I need to do to get this thing working?  Any help you could offer would be wonderful.

Thank you,
Dan Geiger

---

### Post by ts3 on 2012-03-17
> **czechman45 said:**
> It searched for and installed a new driver (Broadcom STA wireless driver) and then I restarted.  

Ahoj, czechman ;)

First, it looks like you have a broadcom wireless card.  Running the following command in terminal will show you which of the many you have on your dell:

```
lspci | grep BCM
```To open a terminal window press ctrl + alt + T, then type the command as shown above.  The first part (lspci) lists your devices, then grep BCM searches for the Broadcom card# (my card for example is BCM4313).  Not all drivers work with all broadcom cards so this narrows it down a bit and you can search for a more specific solution.

You can also run

```
lspci -k
```This lists the kernel drivers and modules in use. There will be an entry for the network controller towards the end of the list; take a look (and post here) the kernel driver in use and the kernel modules.

Generally, once you pinpoint which Broadcom card you have it's a matter of downloading the correct driver from the Ubuntu Software Center, making sure there are no conflicts with other drivers and making sure the wireless is not blocked by a hardware switch.  You can check for hardware switches by running in terminal

```
rfkill list all
```If the results list gives you a yes, you can run 

```
sudo rfkill unblock all
```When you start a command with sudo you are using root privileges and the terminal will ask you for a password.  Type your password (nothing will show on the terminal while you type, don't worry about that, just continue typing the password and then press enter).

That's all I can think of, hope some of it helps. 

Cheers :)

---

### Post by czechman45 on 2012-03-17
Ahoj!  Mluvite moc cesky?

Thanks for the advice.  


Here are the results:

 lspci | grep BCM
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)


 lspci -k
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
    Subsystem: Dell Device 01d8
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Dell Device 01d8
    Kernel driver in use: i915
    Kernel modules: intelfb, i915
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Dell Device 01d8
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
    Subsystem: Dell Device 01d8
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
    Subsystem: Dell Device 01d8
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
    Subsystem: Dell Device 01d8
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
    Subsystem: Dell Device 01d8
    Kernel driver in use: uhci_hcd
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
    Subsystem: Dell Device 01d8
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
    Subsystem: Dell Device 01d8
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
    Subsystem: Dell Device 01d8
    Kernel modules: leds-ss4200, iTCO_wdt, intel-rng
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
    Subsystem: Dell Device 01d8
    Kernel driver in use: ata_piix
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
    Subsystem: Dell Device 01d8
    Kernel modules: i2c-i801
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
    Subsystem: Dell Inspiron E1405
    Kernel driver in use: b44
    Kernel modules: b44
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
    Subsystem: Dell Device 01d8
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci
02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
    Subsystem: Dell Device 01d8
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
02:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
    Subsystem: Dell Device 01d8
02:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
    Subsystem: Dell Device 01d8
    Kernel driver in use: r852
    Kernel modules: r852
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card
    Kernel driver in use: b43-pci-bridge
    Kernel modules: wl, ssb


rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

 sudo rfkill unblock all


I have little idea what all of that means and even less idea what I'm supposed to do with it all.  

If you can think of any more advice, I certainly need it.

Also, I've connected to my apartment's router with an Ethernet cable since the wireless isn't working.  After I plug it, it will work for about 20 seconds or so and then a message will pop up in the top right that says "Wired Connection Disabled".  Shortly after that it says "Wired connection 1 Connection Established".  However, it still doesn't work.  The only way I can get the wired connection to work again is to unplug the Ethernet cable and plug it back in.  Any thoughts here?



Thanks so much.

---

### Post by czechman45 on 2012-03-17
Never mind on that last part.  I figured out the wired connection problem:  bad Ethernet cable.

---

### Post by ts3 on 2012-03-17
> **czechman45 said:**
> Ahoj!  Mluvite moc cesky?
Malo a spatne, hodne se toho zapomina kdyz clovek dlouho nebyl v Praze + nejsem rodily mluvci :)

> 
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card
    Kernel driver in use: b43-pci-bridge
    Kernel modules: wl, ssb

rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

 sudo rfkill unblock all

Back to English with apologies for chatting in foreign languages.

Basically you need to search for solutions for your wireless card which is BCM4311 as you can see from above.  Here's one: [http://ubuntuforums.org/showthread.php?t=1816292&highlight=bcm4311](http://ubuntuforums.org/showthread.php?t=1816292&highlight=bcm4311) 

Here's a good explanation about the b43 drivers [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Since you have wired internet access take a look in particular at the heading about installing b43 driver with internet access.  

You can use the command line (sudo apt-get install) to install the drivers, as described in the links.  More easily, you can open the Ubuntu Software Centre, type b43 in the search box and then install the two packages you need (b43-fwcutter and firmware-b43-installer).  

If installing the b43-fwcutter and the firmware-b43-installer and then rebooting does not help please come back and ask.  There might be a conflict with the drivers that are already loaded.  Removing and blacklisting drivers is easy once you know how to do it.

> I have little idea what all of that means and even less idea what I'm supposed to do with it all. 

As to the commands the easiest way to find out is google.  

A couple of brief explanations: rfkill is a tool for enabling and disabling wireless; your results of rfkill list all show you that there is a problem with the software and hardware (the two 'yes' should be 'no' with working wireless); sudo rfkill unblock all is very helpful in removing hardware blocks (usually one of the F buttons, F2 or F12 can be used to switch wireless on/off but they don't always work and are a bit quirky, so rfkill unblock all takes care of that).  

The command lspci lists various devices.  

Adding sudo and entering your password allows you to do things with root privileges that a normal user is not allowed to do, such as installing or removing packages.

The wireless troubleshooting guide [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) explains very well what some commands and tools related to wireless do.

Cheers and please post back what works and what doesn't :)

---

