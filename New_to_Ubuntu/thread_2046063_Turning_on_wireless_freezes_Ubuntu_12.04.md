---
title: "Turning on wireless freezes Ubuntu 12.04"
date: 2012-08-22
forum: New to Ubuntu
---

### Post by Suzdal on 2012-08-22
Hello

I have an older HP nx6125 that I've just installed Ubuntu on. It also has Windows XP installed.
This laptop has a little button above the keyboard that enables and disables the wireless connection. 
My problem is that whenever I press this button in order to enable the wireless Ubuntu freezes up. And equally disturbing, if I leave it on, Ubuntu will not start at all. It freezes at the splash screen. 
This does not happen in Windows XP.

Also, whenever I try to enable wireless from System Settings -> Network, the button snaps back and will not stay in the ON position. 

I have a BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller. 

Any help would be appreciated.

Thanks

---

### Post by Hadaka on 2012-08-22
Hi, the 4318 card requires b43 driver, from a wired connection at
terminal enter..

```
 

sudo apt-get install b43-fwcutter firmware-b43-installer


 
```

re-boot ,disconnect hardwire and give that a try.

---

### Post by eneskuray on 2012-08-22
i had same problem and i solved it . first go network menu and close wifi at it after press button what closing wifi on keyboard . after press again . go to menu again and activate network . that's it

---

### Post by Suzdal on 2012-08-22
Hi. thanks for the quick replies. Unfortunately neither of your suggestions worked for me.. i had already tried the fwcutter/installer combination before posting. sorry i didn't mention that. and i canter toggle between statea from the network menu. it snaps to off whatever i do.

---

