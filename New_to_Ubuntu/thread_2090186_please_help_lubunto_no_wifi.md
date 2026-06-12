---
title: "please help lubunto no wifi"
date: 2012-12-01
forum: New to Ubuntu
---

### Post by keefer2k4 on 2012-12-01
hello i have a dell d430 with lubunto 12.10 on i just installed and I can not get the wifi working..if i do lspci it shows the card. 
If i do rfkill list.. it doesnt no show up only my bluetooth does.
I have tried many things by searching yet nothing seems to work. I had Ubunto 10.04 on this before and the list of proprietary drivers found the card and the wifi did work and now I cant seem to get it running.

---

### Post by Abhinav Kumar on 2012-12-01
> **keefer2k4 said:**
> hello i have a dell d430 with lubunto 12.10 on i just installed and I can not get the wifi working..if i do lspci it shows the card. 
If i do rfkill list.. it doesnt no show up only my bluetooth does.
I have tried many things by searching yet nothing seems to work. I had Ubunto 10.04 on this before and the list of proprietary drivers found the card and the wifi did work and now I cant seem to get it running.

Hi keefer2k4,
Do you have Broadcom BCM4311 wireless chipset ?

Regards,
Abhinav

---

### Post by keefer2k4 on 2012-12-01
> **Abhinav Kumar said:**
> Hi keefer2k4,
Do you have Broadcom BCM4311 wireless chipset ?

Regards,
Abhinav


yes..this comes up if i enter 
lspci -nnk | grep -iA2 net

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
	Subsystem: Dell Wireless 1490 Dual Band WLAN Mini-Card [1028:0007]
	Kernel modules: ssb

---

### Post by Abhinav Kumar on 2012-12-01
Please visit this link

[http://ubuntuforums.org/showthread.php?t=2072887](http://ubuntuforums.org/showthread.php?t=2072887)

Regards,
Abhinav

---

### Post by keefer2k4 on 2012-12-01
> **Abhinav Kumar said:**
> Please visit this link

[http://ubuntuforums.org/showthread.php?t=2072887](http://ubuntuforums.org/showthread.php?t=2072887)

Regards,
Abhinav



still doesnt work....if i click on the network connections in the corner it doesn't say anything for wireless.

---

### Post by keefer2k4 on 2012-12-01
now if i enter 
lspci -nnk | grep -iA2 net

it comes up 
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
	Subsystem: Dell Wireless 1490 Dual Band WLAN Mini-Card [1028:0007]
	Kernel modules: wl, ssb


it looks like two modules are being conflicted is this in issue?

---

### Post by Abhinav Kumar on 2012-12-01
> **keefer2k4 said:**
> now if i enter 
lspci -nnk | grep -iA2 net

it comes up 
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
    Subsystem: Dell Wireless 1490 Dual Band WLAN Mini-Card [1028:0007]
    Kernel modules: wl, ssb


it looks like two modules are being conflicted is this in issue?

 I am not sure whether they are conflicting or not. Sorry, I am too struck at this point.

Regards,
Abhinav

---

### Post by keefer2k4 on 2012-12-01
I have solved it finally..I went over to

[http://www.linuxwireless.org/en/users/Drivers/b43](http://www.linuxwireless.org/en/users/Drivers/b43)

and followed the directions at the bottom of the page there is a section call switching between drivers.. I followed the commands and my wifi instantly turned on!!

   modprobe -r b43 bcma
   modprobe -r brcmsmac bcma
   modprobe -r wl

then
   modprobe b43

---

### Post by Abhinav Kumar on 2012-12-01
> **keefer2k4 said:**
> I have solved it finally..I went over to

[http://www.linuxwireless.org/en/users/Drivers/b43](http://www.linuxwireless.org/en/users/Drivers/b43)

and followed the directions at the bottom of the page there is a section call switching between drivers.. I followed the commands and my wifi instantly turned on!!

   modprobe -r b43 bcma
   modprobe -r brcmsmac bcma
   modprobe -r wl

then
   modprobe b43
Really glad, it worked out for you. 

Regards,
Abhinav

---

### Post by keefer2k4 on 2012-12-01
Thank you for the help and the quick responses!

---

