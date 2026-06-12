---
title: "[SOLVED] ATI driver issues"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by HavocXphere on 2008-11-21
Hi guys

I'm struggling to get my Radeon 3850 (RV670 core) working under Kubuntu 8.10.

Looks like the 3850 isn't properly supported..cause its running in VESA (I think) atm and I can't enable the proprietary fglrx drivers. Nothing happens when I click on the button to enable the proprietary drivers.

Live-CD and straight install only works when using Safe Graphics mode, else I get a black screen.

I want:   1024x768 @ 85hz
I've got: 1280x1024 @ 60hz

I tried editing the xorg.conf to get the right resolution. Worked in the past but not this time.

If I got to the normal display controls then the monitor switches to 1024x768 (still wrong refresh) as per XOrg.conf but the colours go psychedelic...almost looks like a photo with inverted colours. ctrl-alt-backspace resets it back to the normal colours.

Any ideas on how to sort this out? The 60hz is killing me and the current drivers don't appear to be working very well either.

Thanks

---

### Post by Peter09 on 2008-11-21
Have you seen 

[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

- does it help

---

### Post by HavocXphere on 2008-11-21
> **Peter09 said:**
> Have you seen 

[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

- does it help
That works.:guitar: Thank you & Peter09 for president & thanks awarded. 

Now I've got the right resolution & refresh rate. I didn't know whether I need the Direct Rendering thing (DRI) or not so I left that out.

BUT 2 problems:
1) Every couple of seconds a black bar like thing flashes over the screen. I'd guess the timing with the sync is off a bit.:( The bar moves up every few seconds & then start again from the bottom.

My screen (Physical) says its on 68.76khz HF and 84.91Hz VF. Can it be that missing 0.09 HZ thats the problem?

Using the gtf command I get

# 1024x768 @ 85.00 Hz (GTF) hsync: 68.60 kHz; pclk: 94.39 MHz
  Modeline "1024x768_85.00"  94.39  1024 1088 1200 1376  768 769 772 807  -HSync +Vsync

Will that work if I copy it into the Monitor section? Or must it go to the screen section?

2) The screen area is shifted to the left...and I can't move it with the physical screen settings cause then the other OS (Vista for games) will be wrong. Is there a place where I can adjust this?

---

### Post by HavocXphere on 2008-11-21
Fixed it.

For future googling reference:

The flashing black line is not caused by refresh rate issues. To fix it one needs to disable the "Detecting RANDR (monitor) changes" services. If one stops it..the flashing disappears instantly.

More info:
[http://blog.turbulentsky.com/2008/11/kubuntu-810-video-flashing-flickering.html](http://blog.turbulentsky.com/2008/11/kubuntu-810-video-flashing-flickering.html)

---

