---
title: "HOWTO: Broadcom 4306 &amp; Edgy"
date: 2006-11-02
forum: Outdated Tutorials &amp; Tips
---

### Post by iseebluuue on 2006-11-02
Here's a quick guide (my first attempt at one) on how I got my Broadcom 4306 wireless card to work in Edgy (Gateway laptop). 

A while ago I downloaded the Edgy RC .iso and installed it. I followed the typical procedures I was accustomed to using in Dapper to get my card working via ndiswrapper, but to no avail. I got some random errors and was frustrated for a few hours. So I decided to start all over again, and here's exactly what I did. I re-installed the Edgy RC and connected through ethernet (my wireless did not seem to work out the box, big surprise :p ) to get any updates I needed. Here's where the guide really begins:

**1)**Install ndiswrapper 1.8 through Synaptic 
(make sure to enable universe, multiverse repositories in software sources)

note: the rest of the steps were a combo of the following guides:
[http://ubuntuforums.org/showpost.php?p=752155&postcount=7]("http://ubuntuforums.org/showpost.php?p=752155&postcount=7")
[URL="http://ubuntuforums.org/showpost.php?p=1169984&postcount=1"]
http://ubuntuforums.org/showpost.php?p=1169984&postcount=1[/URL]

**2)**I next grabbed the necessary driver files here:
[http://home.nc.rr.com/thehinnants/stuff/drivers/]("http://home.nc.rr.com/thehinnants/stuff/drivers/")
and then fired up the terminal

**3)** sudo rmmod bcm43xx

**4)** sudo gedit /etc/modprobe.d/blacklist
          add "blacklist bcm43xx" to the bottom (without quotes)

**5)** sudo ndiswrapper -i /path/to/bcmwl5.inf     
(adjust path to suit your needs; for some it may be easier to just drag n drop the file into the terminal window)

**6)** ndiswrapper -l 
          (if installation was successful you should see 'bcmwl5 driver present hardware present')

**7)** sudo modprobe ndiswrapper

**8.)** sudo ndiswrapper -m

**9)** goto System->Administration->Networking and enter the essid and appropriate WEP (if any)

**10)** boom! I was online at this point

optional steps: for some reason my wireless is always eth1 by default, but I'm just a little too particular to allow this. So I changed all instances of eth1 (I suppose it could be different for you) to wlan0 in the following files:

/etc/network/interfaces
/etc/iftab

(I rebooted at this point and was up and running again, but now under the wlan0 interface)



I hope this helps people out there who were having the same difficulties as  I was. I couldn't believe how flawlessly it worked for me. I hope it's not just me that it works for. Cheers!

---

### Post by motang on 2006-11-02
Sweet, I was looking something like this, I am going to go home and try it out, and let you know if it worked out for me.  Thanks. :D

---

### Post by Jeff Gavett on 2006-11-03
I did everything as prescribed on this guide and now in network settings, my wireless device no longer even appears. Any ideas?

---

### Post by skierkegaard on 2006-11-03
I had the same result with this Howto Jeff, I had more success with the fwcutter style instructions.

---

### Post by justynbutler on 2006-11-05
Hi, I found that using the native driver (using fwcutter for the firmware) works for me in Edgy with my WMP54G PCI card with bcm4306 chip.

I put some instructions on thw wiki:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy)

Good luck.
Justyn

---

### Post by iseebluuue on 2006-11-12
my wireless interface disappeared briefly when i changed the interface name from 'eth1' to 'wlan0'; after i restarted it came back and has been working fine. i don't know if you did this step or not, but you may want to skip it. i'm sorry it doesn't seem to be working for you, it worked perfectly on my laptop.

---

### Post by darthchaosofrspw on 2006-11-26
Using these steps, my wifi works, and these steps are confirmed by me to work with Dapper, Edgy, and Feisty.

---

### Post by 0MG on 2006-12-24
Just wanted to drop a line to say that this worked flawlessly with my Broadcom 4306 (Linksys WPC54GS v1.1 PCMCIA card).

Thank you.

---

