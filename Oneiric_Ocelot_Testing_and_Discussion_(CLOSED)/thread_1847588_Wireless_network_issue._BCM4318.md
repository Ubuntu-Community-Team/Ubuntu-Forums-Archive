---
title: "Wireless network issue. BCM4318"
date: 2011-09-21
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by shawntausch on 2011-09-21
Okay, so, I've been out of the Ubuntu loop for quite a while, switched an old laptop to 11.10 and now I am unable to connect to my wireless network. I have uninstalled and reinstalled Ubuntu about 4 differant times today, and have tried The synaptic package manager fix, and still nothing. The driver is there, and the system check recognizes that the card is there, however, it does not show up anywhere on my PC. I'm stumped. if there is anything anyone can do to help, please let me know. I'm seriously frustrated, and I really want to start using Linux again, but if my wireless cant be fixed, I may have to go back to windows. =/   any information you'd need to help me out I will provide no problem, I'm just not sure what you need or whatever. 

Thanks in advance!

---

### Post by repkam09 on 2011-09-21
I've always had trouble with my Broadcom BCM4322 Wireless card.

Which driver do you have installed now? Probably the b43 drivers from the 'firmware-b43-installer' package judging from the WiFiDocs page. ([Link]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing_b43_drivers")) Does the network manager applet show anything or have a message such as "firmware not ready" under wireless?



Other people might be able to give you a little more help if you post some more details. The commands below can be typed into the Terminal (Press: "Ctrl-Alt-T" or open the Dash and type 'Terminal') to get more information about your machine. Then post the output of those commands.

Wireless Brand and Model:
```
lspci | grep Broadcom
```

Wireless Chipset:
```
lspci -n | grep '14e4'
```

Kernel/Architecture:
```
uname -mr
```


Also, you could try a different version of Ubuntu if you are just trying to get back into using Linux. The 11.10 version is still a bit unstable as it is a beta release. Give 11.04 or 10.10 a shot?

If you have a normal wired Ethernet connection, you could plug that in so you can check that you are updated completely.

Good luck!




Edit: I also just noticed that you might have to have both 'firmware-b43-installer' and 'b43-fwcutter' installed. (Quoted from [Ubuntu WiFiDocs]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_Internet_access") Step 1)
> Since Ubuntu 11.04 Natty Narwhal additional installation of the package firmware-b43-installer can be helpful and/or necessary, respectively:

~$ sudo apt-get install b43-fwcutter firmware-b43-installer
or, if you need a legacy driver, use:

~$ sudo apt-get install firmware-b43legacy-installer
This assumes that you have some other form of internet access. If not, there are "No Internet" instructions as well.

---

### Post by shawntausch on 2011-09-21
okay, first line of code produced this.

06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)



second,

06:02.0 0280: 14e4:4318 (rev 02)

Third

2.6.38-11-generic i686

I'm not sure if this was anything you were looking for. I've followed several different solution methods, and none of them seemed to have any affect. here were the ones I've given a go. 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

[http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177)

Now, I'm thinking somewhere in all of this, I may have screwed somthing up, and now I'm running into issues because of it. I really don't want to have to do another wipe and reinstall, I just need to be sure that I have to before I do. Downgrading to 10.1 or 11.04 isn't an issue, I just need to know that there is no other way to fix this first. =/

thanks again!

---

### Post by cariboo on 2011-09-21
Both of those solutions are pretty old. If you have a wired connection, make sure you have the universe repositories enabled and install synaptic package manager. Once you have synaptic installed search for firmware-b43-installer, right-click to mark it for installation, then click apply. After the packages have downloaded, open the install terminal, and watch to see if the firmware is installed properly. If the firmware installed properly all you should have to do is reboot, and once at the desktop you should have working wireless.

---

### Post by bbrg548 on 2011-09-22
> **shawntausch said:**
> Okay, so, I've been out of the Ubuntu loop for quite a while, switched an old laptop to 11.10 and now I am unable to connect to my wireless network. I have uninstalled and reinstalled Ubuntu about 4 differant times today, and have tried The synaptic package manager fix, and still nothing. The driver is there, and the system check recognizes that the card is there, however, it does not show up anywhere on my PC. I'm stumped. if there is anything anyone can do to help, please let me know. I'm seriously frustrated, and I really want to start using Linux again, but if my wireless cant be fixed, I may have to go back to windows. =/   any information you'd need to help me out I will provide no problem, I'm just not sure what you need or whatever. 

Thanks in advance!

Just to knock out the obvious, when you open the "Additional Drivers" dialog box (just type in into the dash and select), does it show a Broadcom driver, and does it show that it's activated? I had a similar issue when I did a clean install of Natty, and activating the driver is all it took.

---

