---
title: "Wireless Broadcom with HP Pavilion zv6000"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by bhoomija on 2008-05-26
Hi

I recently upgraded my ubuntu 7.04 to 8.04. Previously the wireless facility on my computer would work, but it stopped working on linux after the upgrade, though it does work on the windows partition. My hardware specifications are:

HP Pavilion zv6000 with AMD Athlon 64
 and wireless:
03:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
	Subsystem: Hewlett-Packard Company Unknown device 1355
	Flags: bus master, fast devsel, latency 64, IRQ 21
	Memory at b0204000 (32-bit, non-prefetchable) [size=8K]

Is there any way I can fix this? Any help would be appreciated...

---

### Post by shifty_powers on 2008-05-26
do you have a separate /home partition?

---

### Post by bhoomija on 2008-05-26
hi 

yes i do have a /home partition...[http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

---

### Post by shifty_powers on 2008-05-26
heh, well the upgrade distro idea seems to be a good idea, but really quite flaky.

personally i would rather do a clean install, just don't format or touch you /home partition ;)

will involve a bit of reinstalling of progs, but meh.

download and use the livecd for 8.04 before you do it to check that your wireless will work with a clean install ;)

---

### Post by Pioneer5000 on 2008-05-26
I have the same problem im using Dell Inspiron 1501 it was working with 7.04. To get everything setup i just went into prefences --> restricted drivers and then just had to update driver and then got it working. But this is bs that doesnt work in 8.04 the driver doesnt even show up for upgrading. And its so anoying why can Windows do this automatically just pick up the wireless connection so i can connect but Ubuntu cant?

Please help! Thanks.

---

### Post by mapes12 on 2008-05-26
Here are some resources that should help you out. If you can't find the answer here then it's unlikely you will find the answer anywhere:

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

Also, take a look at this excellent HOWTO:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

If the above doesn't work then consider abandoning your current wifi card and get one that Linux fully supports. I got mine (Comtrend RT2500 - just plug in and it works!) from these guys:

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

ndiswrapper is an option for cards not fully supported but in my experience the configurataion breaks down over time. I ended up having to go back to windoze for a while until I got the new card. Natively supported cards work much better.

.............or go back to 7.04 until updates are out that correct the 8.04 issue.

---

### Post by sam_delta on 2008-05-26
do you have a wired connection? do all updates to update your system and try going into system>administration>hardware drivers and check if there is a broadcom wireless listed there if so, click and enable it.

if its not there, try installing b43-fwcutter by typing
```
sudo aptitude purge b43-fwcutter
sudo aptitude update
sudo aptitude install b43-fwcutter
```
make sure you answer with YES when prompted if you want to fetch the firmware
restart your computer and check if it works/shows under system>administration>hardware drivers 

tell us if it works
sam

---

### Post by svk on 2008-05-26
You may find this link to be very helpful:
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

If you scroll down a bit, your card (bcm4318) is supported by the newer b43 drivers, so you can just go ahead and follow the directions on that page.  I have a b4328 card on my lappy, which is one of the few that isn't supported yet... that's just *my* luck.

Do tell us whether or not this fixed it, because this might not be the issue.  My wireless also broke when I updated to 8.04, although it worked just fine under 7.04.  But in my case, it was actually nm-applet that was broken: for whatever reason, it refused to manage my wlan0 device.  Basically, my wireless card worked, but the application that was supposed to manage it ignored its presence.  I could still connect using the iwconfig command from the terminal.  My friend fixed it for me, but I'm not sure how...

---

### Post by Pioneer5000 on 2008-05-31
> **sam_delta said:**
> do you have a wired connection? do all updates to update your system and try going into system>administration>hardware drivers and check if there is a broadcom wireless listed there if so, click and enable it.

if its not there, try installing b43-fwcutter by typing
```
sudo aptitude purge b43-fwcutter
sudo aptitude update
sudo aptitude install b43-fwcutter
```
make sure you answer with YES when prompted if you want to fetch the firmware
restart your computer and check if it works/shows under system>administration>hardware drivers 

tell us if it works
sam


Thank You, This worked.

---

### Post by sam_delta on 2008-05-31
no problem, glad its working

enjoy ubuntu :)

sam

---

