---
title: "Toshiba laptop wireless glitch"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by geomur on 2008-05-15
Hi Folks.  I have a Toshiba Satellite Pentium Dual Core now running Ubuntu 8.04.  I managed to install the Atheros AR5007 wireless utility via instructions on another forum (showthread.php?t=766529)and it sees my home network.  But firefox and other apps will not connect through it even though wireless seems enabled OK.  Help!  Complete newbie with Ubuntu but very impressed so far.

---

### Post by nicedude on 2008-05-15
I have a Acer with AR5007 so I can help you. Please tell me how you enabled your Atheros though. Did you use madwifi drivers ( these are the best IMHO ) or another solution? Please describe steps you took and I will know where your at now and help you get your situation resolved.

---

### Post by geomur on 2008-05-15
Hi, many thanks for getting back.  The thread I followed reads as follows:

go to "System/Administration/Hardware Drivers" and disable by un-ticking the box.:

Code:
Atheros Hardware Access Layor (Hal)Then Reboot

Then open the terminal "Applications/Accessories/Terminal" and copy the following:

Code:
wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gzCode:](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gzCode:)
sudo apt-get install build-essentialCode:
tar xfz madwifi-ng-r2756+ar5007.tar.gzCode:
cd madwifi-ng-r2756+ar5007Code:
makeCode:
sudo make installCode:
sudo modprobe ath_pciCode:
sudo reboot


All of the above seemed to go well (although I needed to hitch up a tempoaray ethernet internet link to make it work).  But although the adapter now sees the home network, I can't get any further.  looking forward to hearing from you.

Geoff

---

### Post by nicedude on 2008-05-15
If you were using ubuntu gutsy 7.10 then that driver would work for your wifi card however for ubuntu Hardy 8.04 you need madwifi 3366 driver ( or at least I did and I have installed this device with both Gutsy & hardy ). Just because it sees your network does not mean it is functional. 

First you need to go to madwifi forum and look at how to uninstall the driver you already installed, if after trying you can't figure it out I will look it up and walk you through that as well, I just don't remember what I had to do back when I made the same goof as you just did :-)  It wasn't hard though compared to the rest of the fixings.

NOTE IF YOU HAVE AN NVIDIA OR ATI GRAPHICS CARD YOU WILL HAVE TO GET THOSE DRIVERS FROM THEIR WEBSITE AND INSTALL THEM AS WELL IF YOU FOLLOW MY WAY AND REMOVE THE RESTRICTED MANAGER AND MODULES 
This is best though in my opinion as it lets you have control over what drivers your system uses and lets you learn how to install them. My nvidia was pretty simple I just got the driver installer from Nvidia and followed the directions on their site and I have the newest driver possible :-)

Below are general directions on what to do to get it working fully. This was no simple task for me with hardy as I got the 3366 to install only to have it act all crazy at bootup. so I did some reading and ended up using synaptic package manager to remove linux-restricted-modules ( VIDEO & WIFI DRIVERS THAT ARE COPYRIGHTED ) as well as Jockey ( the restricted driver manager ) then after a reboot I installed the 3366 madwifi aircrack patched drivers from the madwifi site ( Help ticket #1679 ) by unzipping them and placing the folder into my home directory where once I opened a terminal and cd'd into there I had to run "sudo make" & then "sudo make install" to get the driver installed and then you run "sudo modprobe ath_pci" to load them. I also had to add the following  to the mentioned file

Location to add modules at startup

/etc/modules

This is added for my AR5007 Wifi card
ath_hal
ath_pci 

use "sudo gedit /etc/modules" to allow simple access to edit it

after all that I still found that the standard network manager software didn't work right for me so I uninstalled it as well as gnome network manager which is just a front end to it, and I now use WICD to manage my network connections and since then all is well and my encrypted network connection functions with a simple click like it should :-)

WICD INSTALL INFO

Installing Wicd in Ubuntu is very simple. You just have to add the Wicd repository to the Ubuntu package manager. To open the package manager in Gnome, go to Administration > Synaptic Package Manager. When it appears, go to Settings > Repositories > Third Party Software > Add..., and enter the following line:

LINE FOR GUTSY IS

deb [http://apt.wicd.net](http://apt.wicd.net) gutsy extras  

LINE FOR HARDY IS 

deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras

Then WICD will be available for install in synaptic.

---

### Post by geomur on 2008-05-15
Hi, really appreciate your full reply.  I will go away and digest this and let you know how it goes.  Best regards, Geoff

---

### Post by balagosa on 2008-05-15
trust me, nicedude knows his AR5007 Wireless Adapter

---

### Post by nicedude on 2008-05-15
You are correct sir, and via kismet I know everyone else's that is within range as well :-)

Praise be to the gods at MADWIFI

---

### Post by nicedude on 2008-05-17
Geomur if you read this I made a full guide step by step for all AR5007 users and link to it is below.

[http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984)

---

### Post by geomur on 2008-05-19
Hi Nicedude,

You are really giving us newbies a leg up on this one, many thanks!

I followed your previous instructions but as yet with no joy, again seeing the home net but not connecting.  Could you quickly cast your eyes over the steps I followed just to see if there are any obvious errors (or shall I just follow your new post!!)

The previous version of madwifi seemed to install in geoff/home/madwifi-ng-r2756+ar5007  (I was a bit surprised to find it here, I thought it would install into the system folder(s)

went to this dir and did 

sudo make uninstall

then

wget [http://snapshots.madwifi.org/special/](http://snapshots.madwifi.org/special/)
madwifif-nr-r3366+ar5007.tar.gz

sudo apt-get install build-esential

tar xfz madwifif-nr-r3366+ar5007.tar.gz

cd madwifi-nr-r3366+ar5007

make

sudo make install

sudo modprobe ath_pci

sudo reboot

(didn't get any obvious error messages whilst doing the install)

the only bit I didn't do was the step relating to /etc/modules because I couldn't figure out how to use the 'gedit' facility (so of course this might be the problem?!)


Anyway, your experienced glance at all this would be much appreciated....I REALLY want to get Ubuntu working on this laptop, in all other repects I am a very excited about migrating to Linux!

Once again, many thanks for your help to all of us starting out in Linux.

Geoff

---

### Post by nicedude on 2008-05-20
Two things you missed as to how I get my AR5007 to work as well as working with all available modes etc 

1. In my guide I remove via synaptic package manager both linux-restricted-modules & jockey ( which is the restricted driver manager utility ) The only drawback for that is that anything listed for your system as being controlled presently by the restricted driver manager will have to have its drivers installed by you. Not a bad thing though as that is how you can control your own system instead of using such utilities that may or may not provide the best drivers for your hardware in the first place.

2. You must do the modules thing as you called it since that is what will load the drivers for your card at system startup time. If you didn't do that and you are still seeing anything to do with your wireless after bootup then you still have jockey or the linux-restricted-modules installed as they have madwifi drivers included ( The wrong ones ) and they are more than likely trying to work but will not. You could blacklist those drivers from loading but it was better for me to just rip them out rather than leave them around to screw something up later.

PLEASE NOTE - if you do remove your linux restricted modules and you have a Nvidia or ATI graphics card you will then have to install the driver for it by getting a copy as I outline in my guide from the manufacturer and following the manufacturers directions to install it. For nvidia it was a bit tricky but I got mine done and I have 3D desktop & compiz working just fine right now as I type this. I think the factory newest driver is better anyway since it supports more cards and will have a better chance of having any bugs fixed ( For example I noted at the Nvidia site that the latest linux driver listed in its change log that the newest gives more power management for Nvidia 8XXX series cards well yahoo since that is what I have in my laptop),  so I got a bonus :-)

Command for how to do the modules thing
sudo gedit /etc/modules

That will open the configuration file you need to edit then just add the 2 things I listed in my guide to the bottom of anything already listed. But as I said you would also need to remove the 2 softwares I outline in #1 of this post as otherwise they will affect your results , just first look at system -> administration -> restricted manager to see what things it is handling on your PC

Please PM me by clicking on my name and selecting "send private message" if you need further advise as I might not see the request here. If you can't figure all this out then just PM me and tell me what kind of laptop and video you have and I will advise.

PS edit your profile to allow private messages as there is no reason not to do so, its not like there are stalkers or cyberbullies here :-)

---

### Post by geomur on 2008-05-20
It Works!!  Many thanks indeed, Nicedude.  Just followed your instructions step-by-step (this time!) and after a few tense seconds the connection lit up perfectly.

Can't thank you enough for taking the trouble to spell it out in newbie steps, I'm sure I'm not the only one who has been dug out of a real deep hole by your efforts!

Many thanks again and very best wishes

Geoff

---

