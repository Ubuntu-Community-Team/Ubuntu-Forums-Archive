---
title: "sound is at wrong time in a video"
date: 2015-08-29
forum: New to Ubuntu
---

### Post by milktoast on 2015-08-29
When Playing a video, for example, through Youtube, the sound seems normal  but it is at the wrong time with the video.   It seems like the sound is able to start and then about one or two seconds later the video starts... then they both play at what is at normal speed but they are not together.


I've done many searches and tried the "Solved answers" but the issue has not changed or gotten better

How and what can I change or edit to get the sound and the videos to be at the same "start time" and "playing time"??

Thanks

---

### Post by SeijiSensei on 2015-08-29
What computer and video card do you have, and what video driver are you using?

---

### Post by milktoast on 2015-08-29
The computer and video card came from "Dell"... it is about one year old .. it is a Inspiron 3847 desktop

lspci gave me this

lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)

lshw -c video
  *-display               
       description: VGA compatible controller
       product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:64 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)

---

### Post by tristan16 on 2015-08-29
Are you using Flash Player or the HTML5 player on YouTube? If you're using the HTML5 player, what browser are you using?

---

### Post by milktoast on 2015-08-29
I'm using Chrome and Firefox... they both get the same issue

I've tried turning off Adobe Flash Player several times... same issue when it is on or off.


From Chrome Plugins

Adobe Flash Player - Version: 18.0.0.233
Shockwave Flash 18.0 r0
Name:	Shockwave Flash
Description:	Shockwave Flash 18.0 r0
Version:	18.0.0.233
Location:	/opt/google/chrome/PepperFlash/libpepflashplayer.so
Type:	PPAPI (out-of-process)
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	.swf
application/futuresplash	FutureSplash Player	.spl

---

### Post by milktoast on 2015-08-29
Just another info... 

This issue doesn't happen when I boot into windows... this is setup to dual boot with two different drives... and this issue still happened when the dual boot was not set up so it was just a single boot into Ubuntu.

---

### Post by tristan16 on 2015-08-29
> **milktoast said:**
> I'm using Chrome and Firefox... they both get the same issue

I've tried turning off Adobe Flash Player several times... same issue when it is on or off. 

OK, not what I was thinking then. I know Firefox needs some tweaks to work best on YouTube without Flash Player, but Google Chrome works out if the box, so it must be something else.

---

