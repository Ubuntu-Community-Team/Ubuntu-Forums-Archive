---
title: "Bios splash screen freezing upon boot up. ubuntu 12.10"
date: 2013-07-10
forum: New to Ubuntu
---

### Post by BlushBerry on 2013-07-10
I really want to use this operating system really badly Mainly because I went back to windows and regretted it. I took a home back in windows 7 and about a couple months afterwards it asked me for my serial number even though I put it in upon reinstall and it worked for about a month..

Now. It told me to re-enter my serial number because the one I entered was not valid and it keeps restarting my computer every hour. So I was fed up and switched back to ubuntu..

Now ubuntu wont start up properly after a fresh install It just freezes at the bios screen refusing to go any further :( I tried unplugging the power cord and taking out the cmos battery for 10 minutes but that diddnt work. I'm not very good when it comes to the bare minimums of a computer.. I cant even reinstall ubuntu. It wont boot from cd. Please help :( I hope my computer is not permanently screwed up.

---

### Post by DogMatix on 2013-07-10
Have you tried a different monitor? or checking power cables (or graphic cards) on the Motherboard are seated correctly?

---

### Post by BlushBerry on 2013-07-10
> **DogMatix said:**
> Have you tried a different monitor? or checking power cables (or graphic cards) on the Motherboard are seated correctly?

I have two monitors hooked up to my tower. And both freeze up. And yes I've checked everything. Everything is connected. It's booted up before but It seems random

---

### Post by DogMatix on 2013-07-10
It sounds like a hardware issue to me (the flickering especially). Have you successfully booted into an OS since the flickering issues started? Have you got a spare graphics card to try.

I had an issue with multi-coloured lines that turned out to be a dying graphics card.

---

### Post by grahammechanical on 2013-07-10
You do realize do you not, that taking out the CMOS battery resets the BIOS options to their default values? Could this be why you cannot run a Ubuntu live session? Have you set the boot parameters to give boot priority to the DVD drive. May be you need to replace the CMOS battery. This could be the reason Windows keeps asking for the serial number. The information is not being stored in the BIOS because the battery is not holding the charge.

You must be getting error messages when you switch on. What are they?

Regards.

---

### Post by BlushBerry on 2013-07-10
> **grahammechanical said:**
> You do realize do you not, that taking out the CMOS battery resets the BIOS options to their default values? Could this be why you cannot run a Ubuntu live session? Have you set the boot parameters to give boot priority to the DVD drive. May be you need to replace the CMOS battery. This could be the reason Windows keeps asking for the serial number. The information is not being stored in the BIOS because the battery is not holding the charge.

You must be getting error messages when you switch on. What are they?

Regards.

Yeah... I'm not getting errors and yes I am trying to reset the bios settings. Which I have done several times now. And I'm not trying to run a live session. I'm trying to boot ubuntu properly. Also another issue I forgot to mention is. Upon default settings the keyboard or mouse does not work.. Even with usb legacy enabled. I tried 60/64 emulation as well for I guess enhanced capability with usb devices but that doesnt seem to do anything. But when I turn on Iommu controller it tends to work. But only once. After i restart it just freezes at the bios.

---

### Post by BlushBerry on 2013-07-10
....What? I never said anything at all about a flickering issue..

---

