---
title: "Setting up Network Manager with wireless in Ubuntu 6.06"
date: 2006-06-18
forum: Outdated Tutorials &amp; Tips
---

### Post by NeoChaosX on 2006-06-18
Okay, I've seen a lot of people have wireless and/or Network Manager problems, so I've decided to write a simple FAQ on how to do this. For those of you about to say "But isn't Network Manager included with Ubuntu?", you are somewhat mistaken. It is included on the Ubuntu CD, but not with a default install. You have to install it yourself - which is what this FAQ is helping you do.

0. **Find out the wireless chipset on your card or computer and read [this page](http://live.gnome.org/NetworkManagerHardware) to find out if your wireless hardware is compatible with NM, and what encryption modes (WEP, WPA, etc.) it supports, as well as troubleshooting tips for osme cards. IT IS VERY IMPORTANT YOU DO THIS - a lot of people have had trouble and it usually turns out their network card isn't fully supported, so reading this will save you some headaches.**

1.**Edit your /etc/network/interfaces file so it looks like this:**
```
auto lo
iface lo inet loopback
```
That's it. You don't need anything else in there. The reason being that the Ubuntu version of NM doesn't "see" any network devices managed by that file (and thus doesn't use it), so clearing the interfaces file of any configuration allows NM to use the device.

2.**If you installed from the Ubuntu 6.06 Desktop CD, add the CD to your apt-get sources if you haven't already done this.** Just put the CD in your drive and from a terminal, enter this:
```
sudo apt-cdrom add
```
Unlike the alternative install CD, the Desktop CD *does not* add itself to your apt sources by default. For Kubuntu and (possibly Xubuntu) users, you're SOL - it's CD doesn't include NM, it's only on the Ubuntu CD. You'll have to download that in order to be able to install NM, and you need a working Net connection to get the KDE interface for NM.

Now you can install network-manager.

3. **Install Network Manager for GNOME** by typing this in a terminal:
```
sudo apt-get install network-manager-gnome
```

Now run the GNOME Network Manager applet by pressing Alt+F2 in a panel and running ```
nm-applet
``` or run that same command in a terminal. For GNOME users, make sure you have the Notification Applet added to your GNOME panel, otherwise you won't see the NM icon.

4. **Installing Network Manager in KDE**. This one is tougher, since unlike GNOME users, you will have to have a internet connection (I'd say use a wired Ethernet connection if possible) to install the KDE interface for NM. When you get a network connection, run this command:
```
sudo apt-get install knetworkmanager
```

Now run it with this command, either in the KDE Run menu, or in a terminal:```
knetworkmanager
```

Now you should have NetworkManager running and managing your wireless card.

---

### Post by kverde on 2006-07-28
Wow, this fixed my problem.  I wish this was in KDE by default.  It took me forever to find this useful tool.  

btw, what is the best way to get this to start up when I fire up my laptop?

---

