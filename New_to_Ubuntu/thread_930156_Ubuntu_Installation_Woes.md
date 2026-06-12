---
title: "Ubuntu Installation Woes"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by captain_buckethead on 2008-09-25
Hi All

Last night I finally had enough of Vista and I had obtained Ubuntu 7.10 on DVD so I backed up all my important stuff and rebooted my system from the DVD Drive to install Ubuntu.
The inital install menu came up, so I duly selected install ubuntu. After that the screen went blank and no more action.
I rebooted again and checked the DVD for errors, which it came through fine.
I rebooted a third time and selected text based install, which seemed to work fine, installing all the packages needed, then restarting when finished.
The intital splash screen came up, but nothing after that, the screen just went blank.
Do I need to obtain a package for my LCD Display (A 22" ACER X223W) or can someone tell me what I am going wrong?

My hardware config is: Acer M3200 quadcore Athlon 64 bit processor, 500Gb HDD, 4Gb DDr2 Ram, Dual layer DVD Drive, TV card, card reader. Acer Wireless Keyboard and mouse.

Thanks all

---

### Post by spiderbatdad on 2008-09-25
try booting into safe graphics mode from the options menu.

---

### Post by egalvan on 2008-09-25
> **captain_buckethead said:**
> Hi All

Last night I finally had enough of Vista and I had obtained Ubuntu 7.10 on DVD 

My hardware config is: Acer M3200 quadcore Athlon 64 bit processor, 500Gb HDD, 4Gb DDr2 Ram, Dual layer DVD Drive, TV card, card reader. Acer Wireless Keyboard and mouse.

Thanks all

Very new hardware, so is there any specific reason you are using and older Ubuntu (7.10) ?

If not, then try the latest 8.04.1.
It has better hardware detection.
And I've read that 8.10 will have even better 64bit support.

If yes, then others will have to chime in with more knowledge than I have.

ErnestG

---

### Post by captain_buckethead on 2008-09-25
I have just tried to reboot using safe graphics mode, but when I do I get the Ubuntu splash scree, you know, the one with the hozizontal orange moving bar, then nothing. Screen doesnt switch off, but just stays black.

---

### Post by captain_buckethead on 2008-09-26
> **egalvan said:**
> Very new hardware, so is there any specific reason you are using and older Ubuntu (7.10) ?

If not, then try the latest 8.04.1.
It has better hardware detection.
And I've read that 8.10 will have even better 64bit support.

ErnestG

Cheers for the reply Ernest

yeah your right, I should be using a newer version of Ubuntu.I just had the older version on DVD waiting for such an occasion. Im downloading the 64bit Ubuntu now, but its going to take about 40 odd hours to get it over a 56k modem connection. Hopefully I wont get the drama with the newer version, though still have no idea why the installation didn't work this time around.

Glenn.

---

### Post by spiderbatdad on 2008-09-26
probably the boot up is hanging, as Ubuntu tries to discover a network connection while starting. It may be if you wait 5minutes or so, thesystem will fully start. Then can try to configure your modem.

---

### Post by captain_buckethead on 2008-09-27
> **spiderbatdad said:**
> probably the boot up is hanging, as Ubuntu tries to discover a network connection while starting. It may be if you wait 5minutes or so, thesystem will fully start. Then can try to configure your modem.

Thanks for the tip. Tried it and no go. Tried booting it with the CD in normal installation, safe graphics mode, only get the ubuntu splash screen then the screen goes black, there is a flashing cursor up in the top left hand corner for a few seconds, then that dissapears. The monitor is getting power, and its working OK because I am running memory test now (no errors either).
Tried also just booting it with its current install, and still nothing.

Glenn.

---

### Post by Sef on 2008-09-27
> its working OK because I am running memory test now (no errors either).

Have you run [memtest]("http://memtest86.com") for at least about 8 hours?  If not, then the results may not be accurate.

---

### Post by kansasnoob on 2008-09-27
Have you even been able to run the Live CD? Without changes to your computer?

---

### Post by captain_buckethead on 2008-09-29
> **kansasnoob said:**
> Have you even been able to run the Live CD? Without changes to your computer?

Hey there all

I thought something was odd, because I would run setup and everything would be good, then Id restart the machine and the screen just wouldnt display anything. Power was getting there, but no screen. So I thought, I would pull out the graphics card and just run Ubuntu setup from the motherboards VGA. Hey it worked! Im the proud parent of an Ubuntu installation even though I am going to remove it soon as I finish downloading the 64bit supported incarnation of Ubuntu.
To test my theory, after I had installed Ubuntu and everything was going fine, I put the ATI RADEON graphics card back in, and guess what, the same result. Power getting to the monitor, but no graphics.
Does anyone know how I can get my RADEON graphics card to work under linux? Or is it just a windows incarnation. The specs printed on a wee sticker on the back of the card are:

RADEON HD3450 256MB DD2 V/D/VO HDCP
PN:188-08E40-023AC

Cheers All and thanks for the wisdom.
Glenn.

---

### Post by thepizzaman on 2008-10-21
yes you have to get the ati drivers from the package manger hmm i had no install issues with my 3450 but.... :)

---

### Post by mkvnmtr on 2008-10-21
8.04 has an install drivers application. It most likely it can detect what driver you need and then install it for you. If not there a workarounds you can ask about  here in the forums.

---

