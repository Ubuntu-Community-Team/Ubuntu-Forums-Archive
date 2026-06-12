---
title: "can anyone guide me with this issue?"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by vistasucksss on 2008-07-06
i recently installed ndiswrapper on my laptop and probably by sheer luck i got my wifi to work. now i am installing ubuntu on my sisters desktop computer and cant really figure out how i did it on my laptop. can anyone help me with how to set up this wifi card? thanks in advance..:KS

i have ndiswrapper but dont know where to go from here... 


girls@girls-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 11)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 11)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)
02:0b.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
02:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
girls@girls-desktop:~$


i know it is the ralink rt2500 and have searched the forums but i am just getting flustered and confused thanks again to anyone who can help me out

---

### Post by james_vanb on 2008-07-06
Did you try this thread?

[http://ubuntuforums.org/showthread.php?t=563547&highlight=RaLink+RT2500](http://ubuntuforums.org/showthread.php?t=563547&highlight=RaLink+RT2500)

---

### Post by vistasucksss on 2008-07-06
hey thanks and sorry for the late reply.i did try that thread and a few others.. im ready to just call it quits and find a wireless card that is supported.... do you have any suggestions?

---

### Post by vistasucksss on 2008-07-07
i actually got this far if anyone is reading this:

> girls@girls-desktop:~$ ndiswrapper -l 
autorun : invalid driver!
bcmwl5 : invalid driver!
girls@girls-desktop:~$ 


---

### Post by BGFG on 2008-07-07
Hey sorry i can't really help. but you could really help yourself if you change the topic of your thread or even start a new one. Ensure that you mention ndiswrapper in the subject. that should attract assistance from the advanced users that you need.

Good luck man.

---

### Post by tjwoosta on 2008-07-07
actually 

i was just searching google, and by the looks of it this card has native support (meaning you wouldnt even need ndiswrapper)

check out this thread (read 4th post and down and it says it worked out of the box)[http://ubuntuforums.org/showthread.php?t=570]("http://ubuntuforums.org/showthread.php?t=570")

---

### Post by cariboo on 2008-07-07
Ndiswrapper is pretty simple, the best way for a newbie to install the windows drivers for this card is to use **ndisgtk**. You can install it using Add/Remove Programs or Synaptic package Manager. Make sure you have your Windows 2000 or Windows XP drivers for the card and use the *.inf to install the drivers. I had better luck with the Windows XP drivers, but someone chimed up in an other thread and said he had better luck with the Windows 2000 drivers.

Jim

---

### Post by steveo314 on 2008-07-07
try this:

1.   apt-get install rutilt
2.   [http://ubuntuforums.org/showthread.php?t=554089&highlight=rutilt](http://ubuntuforums.org/showthread.php?t=554089&highlight=rutilt)

---

### Post by james_vanb on 2008-07-07
The bcmwl5 driver also happens to be used in a Belkin Desktop Wireless card I'm using.  Getting it to work was a challenge indeed.  Since you have an error with the driver, uninstall it:

sudo ndiswrapper -r bcmwl5

Reboot

I followed this post:

[http://ubuntuforums.org/showthread.php?t=766560&highlight=bcmwl5](http://ubuntuforums.org/showthread.php?t=766560&highlight=bcmwl5)

I didn't use all the steps.  What I used was the following with the install cd (Set up a file in Home - I called mine Belkin - Copy all files in the install cd contained in the xp drivers file by draggind and dropping - .inf, .sys, whatever - First command - sudo ndiswrapper -i bcmwl5 - has to be modified to point to the file you created - in my case - sudo ndiswrapper - i /home/(your user name)/Belkin/bcmwl5.inf):

> **alex_kent_18 said:**
> 
**Step 3 (run in terminal)**

[COLOR="Blue"]sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant[/COLOR]

**Step 4  (run in terminal)**

[COLOR="Blue"]sudo aptitude remove b43-fwcutter[/COLOR]

**Step 5  (run in terminal)**

[COLOR="Blue"]sudo gedit /etc/init.d/wirelessfix.sh[/COLOR]

**Step 6**

Paste the followings in the opened file(wirelessfix.sh)and **make sure you save it before continuing Step 7**

[COLOR="Blue"]#!/bin/bash
modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44
[/COLOR]
**Step 7  (run in terminal)**

Run this :

[COLOR="Blue"]cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh[/COLOR]

**Step 8  (run in terminal)**

finally run this:

[COLOR="Blue"]sudo update-rc.d wirelessfix.sh defaults [/COLOR]

**Step 9**

[COLOR="Blue"]Restart your machine[/COLOR] and enjoy the freedom from those wires....

Worked like a charm.

---

### Post by hyper_ch on 2008-07-07
rt2500 chipset pci should run out of the box...

---

