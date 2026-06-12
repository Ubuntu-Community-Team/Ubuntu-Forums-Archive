---
title: "looking for a laptop os"
date: 2009-01-31
forum: Other OS Talk
---

### Post by markp1989 on 2009-01-31
im looking for a distro that will fit a laptop with the following specs

Model: Fujitsu Siemens Amilo Pro V2030

CPU: 1.5ghz caleron M 
RAM: 1 gb
HDD: 2gb CF card. (read speed 45mbs)
WLan: Broadcom BCM4318
VGA: UniChrome Pro IGP Rev 01 

I want something that is light,boots fast and easily supports the hardware. 

Just had a spin at arch, and i cannot get the Graphics card to work properly.

---

### Post by smartboyathome on 2009-01-31
Puppy Linux would be a perfect fit. It has some of the best hardware support around. :)

---

### Post by markp1989 on 2009-01-31
the network card has always been abit of a bitch, with all distors i have tried. Are there and mini PCI wlan cards that you would recomend that have "out of the box" support with most linux distros?

---

### Post by steveneddy on 2009-01-31
Gos from Google is a great little distro.

It's based on Ubuntu but has Wine and bunch of little GoogleDesklets you can install.

Real Mac looking out of the box, though.

I've been using it for the last couple of days testing different distros for my daughter who wants to make the switch from PCLOS.

thinkgos.com

---

### Post by MarblePanther on 2009-01-31
Try Xubuntu.  [http://www.xubuntu.org/](http://www.xubuntu.org/)

Try going to Hardware Drivers (I believe it is under system settings or something like that) and installing the proprietary driver there.

Your card works easiest on an ubuntu-based distro (like xubuntu)--all you have to do is go to hardware drivers and install it.  You will need a cabled connection of course.

---

### Post by markp1989 on 2009-01-31
> **MarblePanther said:**
> Try Xubuntu.  [http://www.xubuntu.org/](http://www.xubuntu.org/)

Try going to Hardware Drivers (I believe it is under system settings or something like that) and installing the proprietary driver there.

Your card works easiest on an ubuntu-based distro (like xubuntu)--all you have to do is go to hardware drivers and install it.  You will need a cabled connection of course.

I have never found the restricted drives all that good with this wifi card. always has reduced range.

EDIT: currently downloading puppy at 350kbs. should be done in no time

---

### Post by MarblePanther on 2009-01-31
Do you have the option for the STA driver?  My Broadcom card absolutely flies with it.  I'm not sure if it is available for your card--if it is, try that out.  Otherwise you'll have to use ndiswrapper or a usb-wireless card.

Oh and no need for Puppy--your laptop is plenty capable Ubuntu, though Xubuntu runs the lighter XFCE DE out of box.  I run it on my eeepc and it is very fast.

---

### Post by markp1989 on 2009-01-31
> **MarblePanther said:**
> Do you have the option for the STA driver?  My Broadcom card absolutely flies with it.  I'm not sure if it is available for your card--if it is, try that out.  Otherwise you'll have to use ndiswrapper or a usb-wireless card.

Oh and no need for Puppy--your laptop is plenty capable Ubuntu, though Xubuntu runs the lighter XFCE DE out of box.  I run it on my eeepc and it is very fast.

i just tried puppy from the live cd, its improved alot since i last used it. my monitor runs at full resolution out of the box.

WIFI is detected, and scanning detects the AP, but it fails to pass the connection test

---

### Post by smartboyathome on 2009-01-31
> **steveneddy said:**
> Gos from Google is a great little distro.

It's based on Ubuntu but has Wine and bunch of little GoogleDesklets you can install.

Real Mac looking out of the box, though.

I've been using it for the last couple of days testing different distros for my daughter who wants to make the switch from PCLOS.

thinkgos.com

For the last time, gOS is not by Google, it is independant from Google. :|

---

### Post by MarblePanther on 2009-01-31
^
he's right

> Google, Google Icons, and the Google Logo are trademarks of Google Inc. Cloud and gOS are not affiliated with Google or their partners.

--from the gOS site




anyways...

xubuntu should fit fine on your 2gb card  (my xubuntu install was i believe 1.69 gb on my eeepc)

---

### Post by Crafty Kisses on 2009-01-31
I'd suggest Slitaz, it runs very nice on older machines.

---

### Post by wolfen69 on 2009-02-01
> **MarblePanther said:**
> 
Oh and no need for Puppy--your laptop is plenty capable Ubuntu
he said he wanted something light and fast. 

i think puppy is a good choice for a lightning fast distro.

---

### Post by markp1989 on 2009-02-01
running puppy fine right now. just need to get the wifi  workng properly.and i`ll be set

---

### Post by markp1989 on 2009-02-01
its strange, i can connect to open networks, but none with WEP?

do i have to install any packages to support wep or what?

---

### Post by steveneddy on 2009-02-01
> **smartboyathome said:**
> For the last time, gOS is not by Google, it is independant from Google. :|

OK, then stop bringing it up.

---

### Post by MarblePanther on 2009-02-01
> **wolfen69 said:**
> he said he wanted something light and fast. 

i think puppy is a good choice for a lightning fast distro.

Xubuntu has better support for his wireless at the moment (Hardware Drivers, install)...
Not to mention a plethora of other things, it was just a suggestion


You may want to try going manually into the driver list that Puppy provides and trying some of those that sound similar to the card you have.  Sometimes it is trial and error with Puppy's wireless detection.


Edit:

This may help you, this person has the same problem and it is answered:

[http://www.murga-linux.com/puppy/viewtopic.php?t=22459](http://www.murga-linux.com/puppy/viewtopic.php?t=22459)

---

### Post by gjoellee on 2009-02-01
I recommend Arch

(I use Arch with Openbox...it uses just 119mb RAM at the moment, that is just with PyPanel running ofcourse)

---

### Post by smartboyathome on 2009-02-01
> **markp1989 said:**
> its strange, i can connect to open networks, but none with WEP?

do i have to install any packages to support wep or what?

Probably the drivers in Puppy don't support WEP. What version of Puppy are you using, 4.1.2? I know with my wireless card (an Intel 4965), I have to use Puppy 4.1.2 to get it to connect without an Ethernet cord.

> **gjoellee said:**
> I recommend Arch

(I use Arch with Openbox...it uses just 119mb RAM at the moment, that is just with PyPanel running ofcourse)

they said in the OP they tried Arch and it didn't work for them. ;)

---

### Post by notwen on 2009-02-02
Perhaps you could give [AntiX]("http://antix.mepis.org/") a spin?  May work for ya.  =]

---

### Post by Crafty Kisses on 2009-02-02
I've been wanting to try antiX for awhile, I just haven't heard anything about it, I guess I'll try it out later on tonight, I'll let you guys know.

---

### Post by Hallvor on 2009-02-03
TinyMe should run like a dream. Uses Openbox, but has great GUI config tools.

---

### Post by pmicheal on 2009-02-04
I recommend you to use Ubuntu 8.10 on your laptop

---

