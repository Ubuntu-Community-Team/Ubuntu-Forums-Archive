---
title: "Graphic Card isnt the one i had on windows..."
date: 2014-07-24
forum: New to Ubuntu
---

### Post by cole5 on 2014-07-24
My pc specs are AMD Turion™ II Dual-Core Mobile Processor M520 Ubuntu 14.04 4GB DDR2 800MHz memory ATI® Integrated Graphics 320GB HDD (5400rpm, Serial ATA) DVD-SuperMulti (+/-R double layer) with Labelflash™ drive I need to some how get my amd 4xxx graphics back

---

### Post by Bashing-om on 2014-07-24
cole5; Hi !

Long story short -> AMD no longer supports the 4X series of ATI cards. If you run later releases/versions of 'buntu the only driver that supports that card is the open source driver 'radeon'.

IF you really really require to run the proprietary 'FGLRX' driver, then install ubuntu version 12.04.[color=red]1[/color]; as that version still has the Xserver that is supported by AMD. 12.04.1 will continue to have support 'till 2017.

[INDENT][INDENT]not good,
[INDENT][INDENT][INDENT]just the way it is
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by cole5 on 2014-07-24
how do i downgrade?

---

### Post by cole5 on 2014-07-24
is there a way i could make mine radeon instead of galium because my old graphics were for gaming..

---

### Post by Vladlenin5000 on 2014-07-24
> **cole5 said:**
> how do i downgrade?

You don't. You simply install the previously recommended version. Or not... Just keep the current one which should have good support with the open source driver.

---

### Post by Rob Sayer on 2014-07-25
The trouble with installing 12.04.1 is that when you do a system update, if you're using the proprietary video driver, it will get borked because of the above mentioned reasons.  I have an old Compaq laptop with AMD 4xxx video with the same problem.

This is fixable by using nomodeset on boot but then you'll be using the open source driver which doesn't support 3D acceleration.  Which means poor video performance.  You won't be able to play HD video properly, let alone run modern games.  IMO "good support" re the open source driver isn't 100% correct.  It works reliably but badly.

I've looked into this subject because I have a similar card but not exhaustively because I don't use that machine much at all. But there doesn't seem to be a good solution in ubuntu.  It's not as simple as holding back one thing from updating.  There are too many other programs involved, and you're going to cause other problems.  People here much more knowledgeable than I just recommend using the open source radeon driver.  Perhaps I'll try a lighter distro that uses an older kernel .... but those aren't for noobs.

---

### Post by grahammechanical on 2014-07-25
> [COLOR=#000000]is there a way i could make mine radeon instead of galium because my old graphics were for gaming[/COLOR]

Is the Details page telling you that the system is using Gallium? If so then you are using the open source video driver. Now if you open System Settings>Software and Updates>Additional Drivers tab you will see what video driver is being used.

I have an Nvidia card and I use the open source video driver by choice. It is called Nouveau. But for an ATI/AMD adapter the same open source video driver will be called Radeon.

Do you have some kind of hybrid graphic system? You have not accurately explained your graphic hardware. I am guessing that you have ATI integrated graphics and also a discrete AMD graphics adapter. Is this true?

Regards.

---

