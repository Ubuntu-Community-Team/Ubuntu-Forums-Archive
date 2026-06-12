---
title: "Dell Latitude D360 wireless problems"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by ceperezleighton on 2008-09-11
Hi all, I just installed Ubuntu 8.04 in my laptop and everything on the surface seems to work nice, but I cannot connect to any wireless network. From what I see it does not seems to recognize that there is a wireless card installed. Any suggestions are more than welcome!!!!

---

### Post by DFlame on 2008-09-11
If you are using a card or the internal wireless, open the terminal and please post the output of:

```
lspci
```

If you are using a USB wireless adapter, post the output of:

```
lsusb
```

Cheers

DFlame

---

### Post by ceperezleighton on 2008-09-12
Hi, thanks... here's the output. I guess the needed info is my type of card: I think it is a Broadcom Corporation BCM4312 802.11b/g, but here is the output. Thanks for the help!!!

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

---

### Post by DFlame on 2008-09-12
Looks like ndiswrapper is the way to go with you! It isn't too hard to set up with some help either :) Connect your computer via a wired connection for now.

**1.** Open Synaptic Package Manager (System > Administration). Hit Search, specify ndiswrapper. From the results, mark ndiswrapper-common and ndiswrapper-utils for installation if they are not already installed. Close the manager after this.

**2.** Check that ndiswrapper is working. Open a Terminal window and enter:

```
ndiswrapper -v
```

You should get some version information if all is well.

**3.** Find the driver for your card. I've taken the liberty of finding, extracting and uploading the right parts for you. [Click here](http://one.xthost.info/waamgames/driver.zip) to download the archive. Save this file in your Home directory.

**4.** Extract the driver. In your Home directory, right click the zip file and select "Extract Here". Some new files will appear.

**5.** Install the driver. Open Terminal again if you closed it already, and try this command:

```
sudo ndiswrapper -i bcmwl6.inf
```

**6.** Check the driver is functioning. This command *should* give an output that the hardware is present and the driver is installed:

```
ndiswrapper -l
```
[COLOR="SeaGreen"]
Congrats if you've got this far.[/COLOR]

**7.** We should now unload any drivers which may cause a conflict with ndiswrapper, and ndiswrapper itself. Perform these commands in Terminal:

```
sudo rmmod b43xx
sudo rmmod b43
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo depmod -a
```

**8.** Now to load the driver!

```
sudo modprobe ndiswrapper
```

If your card is an external one, you should see it power up as indicated by an LED on the card itself.

**9.** If you see it light up, or the system hasn't crashed, or both - It's a good sign that the driver is OK. We should now blacklist the previous drivers and make ndiswrapper load on startup. More terminal work ;)

```
sudo gedit /etc/modprobe.d/blacklist
```

Gedit will load the file. All you have to do is add these lines to the bottom of the file:

> 
#Prevent loading of non-ndiswrapper drivers
blacklist b43
blacklist ssb
blacklist b43xx


Save this file and close gedit to be taken back to Terminal. Now enter:

```
sudo gedit /etc/modules
```

Like blacklisting, but all you have to do is add

> ndiswrapper

on a new line. Save and close gedit for a final time.

**Note:** [COLOR="SeaGreen"][COLOR="Red"]Your card is now set up. The correct drivers will load at boot time. You may choose to stop here and have the network manager built into Gnome manage your wireless connections. However, I find a tool called WICD much better at the job. So it's your choice now :)[/COLOR][/COLOR]

**10.** Install WICD. Download these packages just incase the install doesn't work: [network-manager](http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.6.6-0ubuntu5_i386.deb), [network-manager-gnome](http://launchpadlibrarian.net/13564739/network-manager-gnome_0.6.6-0ubuntu3_i386.deb). Crack open Synaptic Package Manager again. In Settings > Repositories, click the Third Party Software tab. Click Add.. and paste this line into the provided box:

> deb [http://apt.wicd.net/](http://apt.wicd.net/) gutsy extras

Hit Add Source and close the Repositories. Synaptic will complain about needing to refresh, so hit the Refresh button in the top left of the manager. After the packages have been reloaded, search for wicd. Mark wicd for installation. This will remove the original packages (hence why we downloaded backups) and install wicd.

**11.** Start WICD. Easy as pie here. Just go to Applications > Internet > WICD. It should start and you will be ready to browse and connect to networks! There's also options the the program from connecting to networks on startup, encryption and other bits and bobs.

There are loads of guides out there on this forum and the wider Internet, I just thought you might prefer some tailored instructions :lolflag:

Please post back if you get stuck!

DFlame

---

### Post by ceperezleighton on 2008-09-14
Something kind of weird happened. I can connect to the internet using the non-wifi connection. And so I decided to run the applications manager to update and no problem. So later on I get into my computer and double click on wired network connections and now I have access to wireless networks. The other thing is I have a notification icon saying I am running a restricted driver (wl). So, does it makes sense to think that we I got the updates I downloaded the driver?... This is very confusing... any hints?

---

### Post by DFlame on 2008-09-14
How far did you get through my previous post, and is the wireless working properly?

DFlame

---

