---
title: "Ubuntu 12.04 or 13.04?"
date: 2013-06-16
forum: Recurring Discussions
---

### Post by SkyBluesCCFC on 2013-06-16
I do like the look of ubuntu and would be using it along with windows
my computer is:

Processor: AMD Athlon II X2 240e 2.80 GHz
RAM: 4GB
64-bit

My question is, which Ubuntu do I pick, I am leaning towards 13.04 but is the 9 months support a bad thing? And are the differences that big? 
I'm looking to use it predominantly to just help and go along with my phone :D (HTC Sensation)

---

### Post by sudodus on 2013-06-16
Welcome to the Ubuntu Forums :-)

I suggest that you install 12.04 LTS with support until April 2017. By now it is well debugged and polished, and the support for your hardware is probably better than that of 13.04. You can also consider installing the point release 12.04.2 and avoid a lot of update/upgrade work.

I am running 12.04 LTS on a similar machine (with an Asus mobo and a slightly slower CPU).

---

### Post by cincinnatus13 on 2013-06-16
All up to you. I haven't had too many issues with 13.04 (Gnome) and would highly recommend it (along with the Gnome 3 PPA if you use that instead of Unity.)

It all comes down to stability. 13.04 is (supposedly) less stable than 12.04 but has newer packages and improvements. 9 months support just means too that all you have to do is upgrade to 13.10 when it comes around.

I personally go for the latest and greatest but if stability is your main concern, 12.04 all the way.

---

### Post by SkyBluesCCFC on 2013-06-16
Thanks for the replies so far, will my PC be able to cope with 13.04? I am now thinking of getting 12.04 as it seems it will perform better on my (slightly) old computer

---

### Post by howefield on 2013-06-16
> **SkyBluesCCFC said:**
> Thanks for the replies so far, will my PC be able to cope with 13.04? I am now thinking of getting 12.04 as it seems it will perform better on my (slightly) old computer

Your computer sounds fine, but you omit the graphics card specification.

I'd go for 13.04 for two main reasons, firstly because it is faster and more responsive than 12.04 (on my machines) and secondly because I know I'll move to 13.10 as soon as it is available so the 9 month support period is a moot point. If you can't handle the thought of upgrading so soon, then 12.04.2 is a good bet :)

---

### Post by cincinnatus13 on 2013-06-16
Honestly I think 13.04 has a smaller footprint IIRC. I thought they tweaked Unity to run better with less resources.
I could be wrong though.

---

### Post by kurt18947 on 2013-06-17
> **cincinnatus13 said:**
> Honestly I think 13.04 has a smaller footprint IIRC. I thought they tweaked Unity to run better with less resources.
I could be wrong though.

I have a desktop with very similar specs to the O.P.  13.04 and 13.10(so far) both run very well.  I'm using gnome-shell as the default desktop but Unity seems to work okay.  It'll be interesting to see if 13.04 can be upgraded to 13.10 once released and still be stable.  Ubuntu upgrades don't have a sterling history, re-installs have been generally recommended.

---

### Post by mastablasta on 2013-06-17
i have single core Athlon64 AMD works fine. the GPU can be a problematic part (or not).

---

### Post by grahammechanical on 2013-06-17
My machine dates back to 2007 and I have been using every new release of Ubuntu since 7.04 and they all work fine. I have run Raring Ringtail all through its  25 week development period. I am now running Saucy Salamander (development branch). I have just 1GB of RAM. Under 12.04 Ubuntu used about 70% of the RAM even with just System Monitor loaded but with 13.04 that dropped to just about 50%. At the moment on Saucy Salamander with just Chromium loaded System Load Indicator shows 519 MB RAM used with 455MB set aside as cache memory.

As far as I am concerned the choice comes down to this: Do you want to keep upgrading every six months? NO? Do you only want to upgrade every two years? Yes? Then stay with 12.04 until 14.04 is released and then upgrade. Otherwise, start at 13.04 and upgrade every six months and get the improvements that are being made to Ubuntu during the next 12  months.

In Saucy Salamander Unity is at Version 7 and we shall be getting version 8 (also called Unity Next) soon. And we will also get soon get an option at log in to try running Ubuntu with the new MIR display driver. These things will be standard in Ubuntu by the 13.10 release date.

Regards.

---

### Post by edeneen on 2013-06-17
I have tried both on the same machine- I went back to 12.04

---

### Post by craig10x on 2013-06-17
My experience has been after running 12.04 (LTS release) then 12.10 and now 13.04, that 13.04 is using less resources because of many improvements in unity...Personally, i couldn't see myself going back to 12.04 now...
What i will probably do is upgrade to 13.10 when it arrives and once 14.04 is here (next april) then i might clean install and start on a 2 year LTS to LTS cycle....perhaps you might want to consider doing something along those lines...

It's just that there have been so many changes in the unity desktop environment and as was mentioned, many more between now and next year's 14.04 that i figured that if i was to go with LTS versions i would want to wait to start doing that at 14.04's release rather then now...

---

### Post by Mark Phelps on 2013-06-17
Others have already mentioned this ... but I will emphasize this -- one major factor is the graphics chipset you have in your PC.

Why?

Because if you have an AMD chipset of the HD 2x/3x/4x variety, the latest Ubuntu version that will support AMD restricted drivers is 12.04.1.  Starting with 12.04.2, and continuing with 12.10 and 13.04, the X-server version got upgraded to a new version that is incompatible with the AMD restricted drivers for those chipsets.

If you don't have one of those AMD chipsets, or if you're willing to live with the default Radeon open source drivers, then the choice really is up to you.

---

