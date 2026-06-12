---
title: "Running WICD and network manager together"
date: 2012-08-20
forum: New to Ubuntu
---

### Post by Moralz on 2012-08-20
Hi, first time post but have been lurking on the forums for about a couple of months now and its a WEALTH of information. For that, thank you all.
 
Im running BT5R2 Ubuntu 10.04 gnome 64 on samsung series 5, and wicd will connect to WPA/WPA2 and even open networks...however it wont with WEP. My home WPA network is no problem and so are open networks. However WEP encryption is a huge problem and I can never get it to "obtain a ip"....Ive even tried manually setting a static IP through wicd and while Im connected I have no internet access...Im at my wits end here.
I used this to connect to connect manually in case anyone asks:
 
```
 
ifconfig <interface> down
dhclient -r <interface>
ifconfig <interface> up
iwconfig <interface> essid "MYNETWORK"
iwconfig <interface> key 123456
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>
ifconfig <interface> up

```
 
Output yields no errors but no internet connection and iwconfig shows me connected to MYNETWORK.
 
Ive searched the BT forums and here and found that Network manager could run side by side with WICD as it supposedly has no issues connecting with WEP. This I see as my only solution, or manually connecting which doesnt do much but show me connected with no internet access as mentioned earlier.
 
Bottom line is how can I get network manager (which I had installed yesterday but then removed) to auto scan for networks (as when I opened it it was empty) and have the wireless icon appear on the tray. I would still like to run both (not at the same time obviously), and I cant find any resources on running both together. Ideal would be when I boot I choose which one to use to scan for networks to connect to or I can iwlist scan and then choose based on the encryption whether to use network manager or wicd. Its so freaking annoying that wicd can handle WPA/WPA2 & unsecured but not WEP. For the love of god any advice would be great. 
 
Thank you again, and this is such a great site, Im kind of glad this problem happened because it gave me the kick in the pants to register and become part of the community. Im one of those people that typically just reads and reads but on this topic albeit covered thousands of times all the "solutions" were more user side errors, and all of those have not helped in the least. Network manager appears to be my only hope.

---

### Post by Terl on 2012-08-24
Here's a how-to on getting network manager up and running for you:  [http://hackwarts.blogspot.com/2011/10/network-manager-in-backtrack-5-r1.html]("http://hackwarts.blogspot.com/2011/10/network-manager-in-backtrack-5-r1.html")

---

### Post by Zill on 2012-08-25
> **Moralz said:**
> ...Im running BT5R2 Ubuntu 10.04 gnome 64 on samsung series 5, and wicd will connect to WPA/WPA2 and even open networks...however it wont with WEP. [COLOR="Red"]My home WPA network is no problem[/COLOR] and so are open networks. However WEP encryption is a huge problem and I can never get it to "obtain a ip"...
As do you seem to have access to *your own* WPA network, are you actually authorized to access *someone else's* WEP network?

---

