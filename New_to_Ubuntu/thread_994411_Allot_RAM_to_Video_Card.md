---
title: "Allot RAM to Video Card?"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by mlwalter on 2008-11-26
Is it possible to allot some unused RAM for the video card to use?  My laptop has a 64MB video card, but I have 2GB of RAM (being largely unused from checking 'free -m').

---

### Post by halitech on 2008-11-26
depends on the laptop. If possible it would be done in the BIOS setup.

---

### Post by mlwalter on 2008-11-26
> **halitech said:**
> depends on the laptop. If possible it would be done in the BIOS setup.

The laptop is a Dell Inspiron 8600.  What would I look for in the BIOS setup?  Any keywords?

---

### Post by halitech on 2008-11-26
it should be labelled video memory or something similar. but by the looks of this info:

```

Video
Installed Video Memory64 MB · 32 MB · 128 MB
Graphic ProcessorATI MOBILITY RADEON 9000 · NVIDIA GeForce FX Go5200
External Video Resolution1600 x 1200
Graphic Bus InterfaceAGP x4
```

it looks like the video ram is seperate from your system ram

---

### Post by mlwalter on 2008-11-26
> **halitech said:**
> it should be labelled video memory or something similar. but by the looks of this info:

```

Video
Installed Video Memory64 MB · 32 MB · 128 MB
Graphic ProcessorATI MOBILITY RADEON 9000 · NVIDIA GeForce FX Go5200
External Video Resolution1600 x 1200
Graphic Bus InterfaceAGP x4
```

it looks like the video ram is seperate from your system ram

So from the looks of it, what I would like to do is not possible.  When I went into the BIOS setup, the most advanced thing I could do was to change the boot order.
The whole reason I am trying to do this, is that I am getting some choppy video on certain things (say like YouTube).  And I figured was probably because it was over-extending the Video RAM.  Am I wrong in assuming this?

---

### Post by halitech on 2008-11-26
alot of laptops have things locked down so you cant change much :(

I would say you are probably in the right ballfield. Are you running anything like Compiz? it usually makes things work a little harder so if you do, try turning it off and try youtube again.

---

### Post by mlwalter on 2008-11-26
> **halitech said:**
> alot of laptops have things locked down so you cant change much :(

I would say you are probably in the right ballfield. Are you running anything like Compiz? it usually makes things work a little harder so if you do, try turning it off and try youtube again.

I have Compiz on Normal (not Extra).  I've been thinking about replacing the current video card with a compatible 128MB video card.  I've got to assume that would help out a lot.  Thanks for your help though.

---

### Post by halitech on 2008-11-26
try turning it completely off and see if it helps. A 128meg card will certainly help though.

---

### Post by HittingSmoke on 2008-11-26
> **mlwalter said:**
> Is it possible to allot some unused RAM for the video card to use?  My laptop has a 64MB video card, but I have 2GB of RAM (being largely unused from checking 'free -m').

I've never tried this on a notebook before, but depending on the video card and laptop model you may be able to do this with an updated BIOS version that enables AGP Aperture.

All my older AGP mobos have a setting in the BIOS called AGP Aperture size which allots a certain amount of system RAM to the video card. It's not as fast as on-card video RAM but it can help.

I would check for an updates BIOS version for your laptop model and go from there.

*EDIT* [Here]("http://support.dell.com/support/downloads/driverslist.aspx?os=BIOSA&osl=EN&catid=1&impid=-1&servicetag=&SystemID=INS_PNT_P4M_8600&hidos=BIOSA&hidlang=en&TabIndex=") is a link to the Dell BIOS update page for the 8600 series. If you boot into BIOS see if yours is A14 or earlier. I doubt it will give you many more options, if any, but it's always worth a shot. Just make sure you back up whatever version of BIOS you have currently first.

---

### Post by mlwalter on 2008-11-26
> **HittingSmoke said:**
> I've never tried this on a notebook before, but depending on the video card and laptop model you may be able to do this with an updated BIOS version that enables AGP Aperture.

All my older AGP mobos have a setting in the BIOS called AGP Aperture size which allots a certain amount of system RAM to the video card. It's not as fast as on-card video RAM but it can help.

I would check for an updates BIOS version for your laptop model and go from there.

I actually just updated the BIOS a few weeks ago.  There is no option to change the aperture size.

---

### Post by whitethorn on 2008-11-26
Hi I also have a Dell 8600 with a Radeon 9600 with 128 mbytes of ram.  I can watch Youtube videos in Firefox, but not with fullscreen. Fullscreen is also choppy. Just thought I might mention before you went graphic card shopping. In Hardy I've tried installing the latest drivers from ATI but it didn't help. Hope you find a solution, and if you do post it here I'm gonna keep an eye on the thread.

---

### Post by kerry_s on 2008-11-26
you can try and use "OverlayMem"
then check your xorg log see if it worked.

---

### Post by mlwalter on 2008-11-26
> **kerry_s said:**
> you can try and use "OverlayMem"
then check your xorg log see if it worked.

That actually seemed to make my system run slower.

> **whitethorn said:**
> Hi I also have a Dell 8600 with a Radeon 9600 with 128 mbytes of ram.  I can watch Youtube videos in Firefox, but not with fullscreen. Fullscreen is also choppy. Just thought I might mention before you went graphic card shopping. In Hardy I've tried installing the latest drivers from ATI but it didn't help. Hope you find a solution, and if you do post it here I'm gonna keep an eye on the thread.

I planned on finding a used one on Ebay.  But I'm hoping that changing some of the nVidia settings help.

---

### Post by kerry_s on 2008-11-26
> **mlwalter said:**
> That actually seemed to make my system run slower.

in a terminal try> man nvidia
see if there are any settings particular to your card you could use.

---

### Post by NullHead on 2008-11-26
I also have these same issues. I have a Dell Inspiron 8600 with a Nvidia GeForce FX 5200 32mb graphics. This is incredibly .... I mean incredibly horrid when trying to run compiz or watch any movie in full screen. 

I've been looking around for **any** 128mb graphics cards, but I can't seem to find any. If only they were still making the cards ...

---

### Post by mlwalter on 2008-11-27
> **NullHead said:**
> I've been looking around for **any** 128mb graphics cards, but I can't seem to find any. If only they were still making the cards ...

I've been looking at eBay, looks like a used one will run anywhere from $49 to $129.

---

