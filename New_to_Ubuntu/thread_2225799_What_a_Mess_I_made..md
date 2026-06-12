---
title: "What a Mess I made."
date: 2014-05-23
forum: New to Ubuntu
---

### Post by gtravis3 on 2014-05-23
I had managed to wipe the HD and USB Stick; bad experience playing with Debian. So, I had a dead xps m140, so-to-speak, but it was found in a trash can, so I don't really mind what happens to it.
i tried to use a Macbook Pro to make the startup stick, FAT32, and got a  the old you need to put this in a Windows box warning when the Mac  tried to mount it. Perhaps it really meant with Windows installed and  running box? Because when I tried to boot the Dell from it, it just gave  me a dark page with a little blinking bar. 
 I broke down and bought $$$  the Ubuntu Unleashed book at Hasting$$$$ what a ripoff, alas it was an old book, Ubuntu 10.10. However I was able to install it and get it running, albeit, with all sorts of 'Out of Date' warnings. 


Happily, I was able to remake a Ubuntu 14 startup USB stick and get it installed.  i was advised to use a lighter version of Ubuntu, Lubuntu, given the age of this old laptop. I had tried a live version of it. However, I did not notice if it tried to setup an 'automatic' WiFi connection like Ubuntu Desktop does (even from the DE startup stick when I was installing it).
The desktop verson seems to be very slow as compaired to the lighter version. So I am thinking about going to Lubuntu.  
After all this, my questions are;
I have ordered the 2 Gig memory sticks and will up grade to it.  Will that make a difference in what I am seeing?
 Does Lubntu find and let me connect to WiFi like the desktop version does with out entering all that nasty network numbers? I looked into the network and wrote down all the various settings number that it shows for the current setup.

Thank you for your help,
trav

---

### Post by grahammechanical on 2014-05-23
2GB of RAM is better than 1GB but the CPU and the graphic adapter are still the same. More RAM is not a cure all. How much memory does the graphic adapter have? In my opinion anything less than 512MB will give a poor user experience with Ubuntu+Unity. 

From my own experience I have a fine user experience with an Intel Core2 Duo 2.40GHz + 1GB RAM because my video adapter has 1GB of memory of its own. I am using Ubuntu 14.04 and right now I am using Chromium to listen to a BBC program and access this web site and Ubuntu is using less than 550MB of RAM and the CPU is running at less than 15%.

There is something that you should know. If the graphic adapter does not have sufficient hardware acceleration to run Unity 3D then Ubuntu 14.04 will use an open source video driver called llvmpipe as a fallback to give a Unity 3D experience without video adapter hardware acceleration. That does seem very slow visually. It must be admitted. 

So, your poor visual experience could be down to a) not enough video memory; b) the video adapter not having 3D hardware acceleration; c) not using a proprietary video driver. The solution, apart from a hardware upgrade is Xubuntu or Lubuntu.

Regards.

P.S. WiFi connections are never automatic. They cannot be because we need to authenticate the connection to the wireless access point/router. And for that we need the wireless key or WPA-PSK pass phrase. The good news is that with Ubuntu 14.04 setting this up is much, much simpler than it ever was in Ubuntu 10.10 and I am sure that is the case with all the flavours of Ubuntu.

Basically, we select the wireless access point from a list and authenticate the action with the wireless pass phrase. That is it. Network manager does the rest.

---

### Post by gtravis3 on 2014-05-23
[[COLOR=#000000]Thank you grahammechanical[/COLOR]]("http://ubuntuforums.org/member.php?u=1087323") 	 

  						

 						
 Don't know about the 3D kinda thing, however, everything seems to be slow. I'm an Apple kinda guy since the old Apple II days. I am mostly playing around and plan to get into the terminal and Linux Bash pretty hard.

---

### Post by grahammechanical on 2014-05-23
Open About This Computer from the power/cog menu and the section on graphics should tell you if you are running llvmpipe.

---

### Post by gtravis3 on 2014-05-23
Ah, Intel 915GM x86/SSE2

---

### Post by tgalati4 on 2014-05-23
Linux Mint Mate will run well on that hardware.  I would connect a wired ethernet cable and use that to perform your initial updates.  There will be several hundred of them, and it is faster with a wired connection.  Once you have done a few update cycles, reboot and then attempt to set up wireless.  There are lots of guides in the Ubuntu documentation.  [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

