---
title: "Network card/connection Problem"
date: 2011-12-11
forum: New to Ubuntu
---

### Post by Rhumar on 2011-12-11
I am a new user to Ubuntu and just put 11.10 on a flash drive, hoping to install on a partition and have a dual-boot.  When I booted up Ubuntu from the flash drive and went to connect to the internet, it showed my neighbor's network but not mine.  I have tried waiting for it to load, making sure internet is manually enabled, and trying to install my card's drivers for Ubuntu, although I don't think that is the problem since it detected the other network.  I was literally 10 feet from my router during this, so distance is not the issue either.  My network card: Ralink RT5390 802.11b/g/n WiFi Adapter.  This card has given me no trouble on my Windows partition.  Any help would be much appreciated and please just ask if you require any additional information to help me.  Thanks

---

### Post by phidia on 2011-12-11
From searching that card it seems people have had problems getting it to work in linux.
You could try ndiswrapper which is a program designed to enable windows network cards to work in linux with windows drivers.
You still might find help in the ubuntu [wireless wiki]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") but if that doesn't help you will need to get ndiswrapper-[guide here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").

---

### Post by daemondign on 2011-12-12
If you're having trouble recognizing your own Wifi Gateway, it might be a problem with the router itself. Unplug it, plug it back in. If that doesn't work, check your configurations and make sure that you're broadcasting your SSID; still have problems, reset it? Or, if you're that close and you have an Ethernet option, use it. Install and update; then read up on the forums and work on fixing the connectivity issues as you go along.

---

### Post by Bucky Ball on 2011-12-12
Stay away from ndiswrapper. Largely superseded. Plug your computer in with a cable and get online that way. You will probably be offered updates. If not, go to update manager and update.

Check System>Administration>Additional Drivers. Anything there for your card?

Is your router serving you an IP via DHCP or are you using static IP addresses (or both)? If static IP you need to set that up by right clicking the network logo and editing connections. You could even try putting the details of your router in there and see if that works (add a network connection and your network name and security passcode (WEP, WPA, whatever).

You are booting Ubuntu from the USB stick by the sounds of it. That is not going to install Ubuntu to a hard drive. 

11.10 has problems on many machines and I would advise new users to stay away. The most stable release is 10.04 LTS (long-term support) but 10.10 and 11.04 are pretty stable also.

---

### Post by Rhumar on 2011-12-12
Thank you for your feedback Bucky, you seem to be a very knowledgeable person.  What exactly do you mean when you say that ndiswrapper is largely superseded?  What don't you like about it?  Also, I tried many of your suggestions.  When I went to "Additional Drivers", it said "No proprietary drivers are in use on this system."  My router is DHCP.  I know that booting from the USB is not installing it, I put it on because I wanted to be sure everything worked before I used the "Install Ubuntu" icon on the desktop.  Will there be any disadvantages to using an older version?  

Also, something else that you might want to know, I went to the HP website and downloaded the Linux drivers for my network card.  I booted into Ubuntu, extracted the files from the .tar file that was downloaded, which gave me a .rpm file which I had to extract again which gave me a folder with a bunch of folders in it, inside of which was a .ko file.  I tried running the .ko file but nothing happened.  My friend suggested going into properties and checking the box that allows it to be executed, but it wouldn't let me check the box, it kept unchecking it automatically.

---

### Post by Bucky Ball on 2011-12-12
That is probably why your wireless drivers won't install. You are running a 'Try Ubuntu' from the USB (same as running it from the CD) and therefore there is nowhere to install the drivers to. You might have better luck with a full install. If everything else working you might like to just install and then work out the wireless. Chance that will install immediately.

Trying anything to get wireless working when running off the USB is pretty pointless. Unless the driver is already part of the kernel (which it obviously isn't) you won't be able to install it anyway. ;)

---

### Post by anewguy on 2011-12-12
If it's just the same as a LiveCD then it probably won't install or remember the drivers, as Bucky Ball said.  You may want to try to create a persistent USB install and see if you can get things to work that way.

As Bucky Ball indicated, ndiswrapper has been superceded, and by that meaning that there are more and more native Linux drivers becoming available.  Any time there is a native Linux driver for these it is much better to use it (a few exceptions have speed/disconnect problems).  However, when there is no native driver available, or the native driver that is available is problematic, then ndiswrapper should be used as sort of a "last resort" to use Windows drivers to get the wireless working.  Please note that there is nothing wrong with ndiswrapper or using it, it is just preferred to use a native driver - amongst other things you can probably get support for it if you need it.

Dave ;)

---

### Post by Rhumar on 2011-12-12
I installed Ubuntu on my hard drive and everything worked perfectly.  My home network even showed up!  Thank you so much for your help :)

---

### Post by Bucky Ball on 2011-12-12
Hey, no problems, that is what the forums are here for! Good work. Could you please mark the thread as solved from thread tools to help others. ;)

Have fun with your new system and happy learning curve. Make sure to post a new thread if you have any other probs/questions ...

---

