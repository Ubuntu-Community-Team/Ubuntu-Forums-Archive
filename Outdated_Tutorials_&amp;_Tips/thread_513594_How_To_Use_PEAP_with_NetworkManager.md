---
title: "How To: Use PEAP with NetworkManager"
date: 2007-07-30
forum: Outdated Tutorials &amp; Tips
---

### Post by worldgnat on 2007-07-30
How to use PEAP with NetworkManager (or how I learned to stop worrying and click the "connect to other network" option)

As many people, I used to have trouble connecting to Networks using PEAP. The trouble is that when you select a network supporting PEAP in network manager, it seems to only offer different types of WEP. 

First, what  we need is called WPA Enterprise, and as far as I understand mschap v2 needs WPA2 Enterprise. 

Second, you'll obviously need:

-wireless tools: [wireless-tools]("http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Tools.html")
-wpa_supplicant: [URL="http://hostap.epitest.fi/wpa_supplicant/[/URL]
-A configured wireless card (sorry, can't help you there)

For those who don't know, these are tools you'll need to do just about any kind of wireless anything. In addition, some may not have dhcpcd, dhclient, or another dhcp client, but most systems should have one by default. 

Ok, so once all that's setup, run

nm-tool 

in the command line. You should see three or so lines with WPA, WPA2 etc. Find them: they should all be enabled. If not, make sure that you have wpa_supplicant installed. If that doesn't do the trick, try running:

killall NetworkManager
killall nm-applet
NetworkManager
NetworkManagerDispatcher

Then type alt-F2 and in kde run:

knetworkmanager

and in gnome type alt-F2 run

nm-applet

If that doesn't work, you could try my solution which would be to manually re-compile NetworkManager and nm-applet, but someone else may have a better suggestion. 

Assuming that NetworkManager is now operational, left click on the icon. Click on the "Connect to other network..." menu option EVEN IF you see the Access point to which you would like to connect. Now manually enter the essid of your access point. Set the wireless security combo box to WPA Enterprise or WPA2 Enterprise (play around with it and see what works). 

Click connect and hope it works. I've noticed that if wpa_supplicant was started at boot, it seems to block NetworkManager. 

Good luck.

---

