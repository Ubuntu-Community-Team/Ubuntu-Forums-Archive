---
title: "HOWTO: RT2500, etc. wireless cards"
date: 2007-09-30
forum: Outdated Tutorials &amp; Tips
---

### Post by wieman01 on 2007-09-30
**Dapper Drake** users should take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=192588") if this one doesn't work. This guide was tested with **Feisty Fawn**, **Gutsy Gibbon**, and **Hardy Heron**. 
--
To all **RT73** users, please also see [this post]("http://ubuntuforums.org/showthread.php?p=4732883"). Thanks to [Kiefer Rodriguez]("http://ubuntuforums.org/member.php?u=490665") for this solution.

Please post to this [Launchpad bug report]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/163020") with all of your specs, if you have problems with a Ralink based wireless adapter.

This is a simple guide for all Ralink based wireless adapters and everyone who wants to replace the Linux driver with "ndiswrapper" (e.g. because you want to make use of either [Network Manager]("http://www.gnome.org/projects/NetworkManager/") or [WICD]("http://wicd.sourceforge.net/")). 
[B]
_INSTRUCTIONS:_[/B]
[LIST]
[*]Get the latest version of the Windows driver for your card from [Linksys' website]("http://www.linksys.com/servlet/Satellite?c=L_CASupport_C1&childpagename=US%2FLayout&cid=1166859840888&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4088837314B372&displaypage=download") or from the CD that came with your device (whatever vendor). 
[/LIST]

[LIST]
[*]Install "ndiswrapper" package **with** working internet connection (Ethernet):
> sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
[/LIST]

[LIST]
[*]Install "ndiswrapper" package **without** working internet connection (alternatively, install it via Synaptic/Adept):
> sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
[/LIST]

[LIST]
[*]Load new driver module (may not be necessary any longer, but does no harm either):
> sudo depmod -a
sudo modprobe ndiswrapper

[/LIST]

[LIST]
[*]Add the module to "/etc/modules" to have it load automatically:
> echo 'ndiswrapper' | sudo tee -a /etc/modules
[/LIST]

[LIST]
[*]Create alias directive:
> sudo ndiswrapper -m
[/LIST]

[LIST]
[*]Pick a valid Ralink driver based on the chipset of your card (you might blacklist all of them if you are not sure):
> rt2500usb
rt2500pci
rt2500
rt2570
rt73usb
rt73pci
rt73
rt61usb
rt61pci
rt61
rt2860
rt2860sta
rt2x00usb
rt2x00lib
[/LIST]

[LIST]
[*]Blacklist Ralink driver:
> echo 'blacklist [COLOR="Green"]<your_ralink_driver>[/COLOR]' | sudo tee -a /etc/modprobe.d/blacklist
[/LIST]

[LIST]
[*]Now unzip the driver archive you have just downloaded (e.g. in your home directory):
> unzip [COLOR="Green"]<driver_archive>[/COLOR][COLOR="Red"].exe[/COLOR]
[/LIST]

[LIST]
[*]Now find the right driver in the resulting folder & deploy it (folder should also contain other driver files i.e. .cat, .sys):
> sudo ndiswrapper -i [COLOR="Green"]<your_ralink_driver>[/COLOR][COLOR="Red"].inf[/COLOR]
[/LIST]

[LIST]
[*]Make sure it has installed correctly:
> ndiswrapper -l
[/LIST]

[LIST]
[*]The output should yield something like this:
> [COLOR="Blue"]rt2500usb : driver installed
device (13B1:000D) present (alternate driver: rt2500usb)[/COLOR]

[/LIST]

[LIST]
[*]Last but not least open this file...
> sudo gedit /etc/network/interfaces
[/LIST]

[LIST]
[*]...and add these 2 lines if they are not there yet [COLOR="Red"][also try _without_ adding them if Network Manager does not pick up the card & reboot][/COLOR]:
> auto wlan0
iface wlan0 inet dhcp
[/LIST]
You can  now safely delete the extracted driver files & folders. Then reboot the computer and see if you can connect using your favorite networking applet (e.g. Network Manager, WICD, Wifi Radar, etc.). 

Feedback is - as always - appreciated.

_**CHANGE LOG:**_
30/09/2007: Minor fixes.
07/10/2007: Expanded "blacklist".
20/10/2007: Added missing part concerning "interfaces" file.
22/10/2007: Load module "ndiswrapper" at boot.
23/10/2007: Enhanced blacklist.
07/11/2007: Bug fix for Network Manager.
12/11/2007: Updated blacklist & module section.
13/01/2008: Launchpad bug report.
15/04/2008: Update for Hardy.
17/04/2008: RT73 note.

---

### Post by frodon on 2007-10-01
[SIZE="4"][COLOR="Red"]**PLease do not post here but in the thread linked below, no support will be given here**[/COLOR][/SIZE]


If you're looking for some support about this tutorial here is the original support thread :
[http://ubuntuforums.org/showthread.php?t=563547](http://ubuntuforums.org/showthread.php?t=563547)

---

### Post by EarthMind on 2008-06-22
My apologies, wrong topic. I was posting in the wrong tab..

---

