---
title: "Upgrade Video Card"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by wnishantha1 on 2008-10-12
Is it possible to upgrade my video card. If so please tell me what i need to have to do this and if my Ubuntu might have problems with it.

please give me some advice on which ones to buy (not too expensive please) and how to put them into my computer (not laptop). 

also it might be handy to see someone do it their selves on the web or to have someone actually come over and help me. do you think the guys from the store would know how to do this. sorry if there are any spelling mistakes...

---

### Post by schauerlich on 2008-10-12
Swapping out a video card is usally pretty self explanitory. Your computer will either have a PCI or PCI Express slot. Buy a video card that will fit, then put it in the slot. If there is already another video card, you should take it out unless you want to do something with dual monitors.Ubuntu will probably not boot up into X unless you download and install the correct video drivers. I would figure out what driver you will need before you install the video card, download and install it, put it in your xorg.conf, shutdown the computer, install it, and reboot.

EDIT: There are tons of videos of people swapping out video cards on youtube. If you're not sure what to do, try watching a few.

---

### Post by aeiah on 2008-10-12
you'll need to know your computer specs first. you may not have a graphics card, you may just have onboard video right now. either way, you'll need to know what slot your motherboard supports. it'll be either AGP (which is getting quite old now) or PCI-E. and make sure you get one that is correct. its probably gonna be PCI-E unless your computer is over 3 or 4 years old.

putting components into your computer is a lot easier than you think. there's loads of info on websites and youtube etc so dont be intimidated. provided you havent got magnetic hands and power the machine off before poking around inside, you wont do any damage.

what are you hoping to do with your new graphics card? this will affect what the best choice of card is for you. you should also check to see how well they're supported in ubuntu. nvidia seem to have more linux support but i imagine this will change in the coming years.

---

### Post by JoshuaRL on 2008-10-12
> **EDavidBurg said:**
> Swapping out a video card is usally pretty self explanitory. Your computer will either have a PCI or PCI Express slot. Buy a video card that will fit, then put it in the slot. If there is already another video card, you should take it out unless you want to do something with dual monitors.Ubuntu will probably not boot up into X unless you download and install the correct video drivers. I would figure out what driver you will need before you install the video card, download and install it, put it in your xorg.conf, shutdown the computer, install it, and reboot.

EDIT: There are tons of videos of people swapping out video cards on youtube. If you're not sure what to do, try watching a few.

With Hardy, the autodetection has gotten pretty good.  From what I hear, it is going to get a lot better with Intrepid too.  So I'd suggest you try that without editing the xorg.conf first.  

So get your new video card (I'd suggest an Nvidia card myself) and turn off your computer.  Then after about 20 seconds, unplug the power cable to make sure you don't fry anything.  Touch some large metalic object to make sure you aren't statically charged, then insert the card into your computer.  Should be pretty straightforward.  Next, plug in and reboot.  At the BIOS splash page, you'll want to change the settings.  Make sure the BIOS points to your new card's position.  So again, either the AGP or PCI-E port.  Then boot into Ubuntu and it should autodetect for you.  Make sure you have restricted drivers enabled and it should install all the drivers you need pretty easily.  Your system will probably want to restart, but then you should be good.

---

