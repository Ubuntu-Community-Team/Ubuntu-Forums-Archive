---
title: "Heron 8.04: Can't see any wireless networks"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by mogwins on 2008-04-25
HI all,

I realise there are more than a few wireless threads already, but I can't find the solution in the existing ones. Also, I'm very new to linux (recently uninstalled XP), so probably wouldn't be able to adapt someone's solution to my circumstances...

I've just installed 8.04 on an old Dell laptop. All seemed to go smoothly, but I can't see any wireless networks using the "Wireless Networks" app (I know there are several in range). When I type lspci -n in the terminal, I get:

**02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)**

Googling the issue, it seems teh drivers for this hardware device are part of 8.04? Any one got any ideas? Thanks in adavnce!

---

### Post by aeiah on 2008-04-25
im not sure whether they're included or not, but have a look here:
[http://ubuntuforums.org/showthread.php?p=4443721](http://ubuntuforums.org/showthread.php?p=4443721)

that should get you up and running, hopefully. wireless is a bitch, but if you get it sorted you'll have learnt how to use the command line, how to compile drivers, and how to make your wireless card work, so look on the bright side ;)

---

### Post by mogwins on 2008-04-25
Thanks for the link - that guide was very useful, and I think I've nearly got things sorted! I'm still confused that the ubuntu wiki states that the drivers for this device are included as part of the default installation, but I'm happy to have wireless internet access again!

---

### Post by gerben1 on 2008-04-25
Could you perhaps also shed some light on getting wired internet working in Hardy Heron. I uninstalled b43-fwcutter (using: aptitude remove b43-fwcutter) following some tutorial to get wireless working, perhaps that has something to do with it? I already reinstalled it (downloaded b43-fwcutter_001-1_i386.deb on another computer and installed that) but I still cannot connect to the internet...

---

