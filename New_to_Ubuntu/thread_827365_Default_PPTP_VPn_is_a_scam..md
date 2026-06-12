---
title: "Default PPTP VPn is a scam."
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Tethtibis on 2008-06-12
OK, I've got a bit of an odd problem. I cannot connect to my company's VPN. I've tried every VPN in the Ubuntu repositories, Including the one that sits in the network system tray icon, and none of them work. I've asked my System Admin at work for the configuration, and he tells me "it's a default VPN setup, i changed nothing when installing it." So it should be simple enough to connect to it with some program out there compatible with Ubuntu 8.04, right? i have a dual booted Inspiron 1420, and the windblows side works just fine with default setting VPN. I wish to get rid of that side, and the VPN is the only thing restricting me. Has anyone else had this problem, where they get the forums, "this is how you setup a default pptp VPN, they claim they did it, but you don't get the same results?" i have no idea what I'm doing wrong. I'm not a complete Newb, I know a fair amount, but I need some help please. Anyone willing to help, any info you need, let me know please. This is an awesome laptop i bought straight with Ubuntu on it, and I have a real itch to get windblows off of it. thanks.

---

### Post by Tethtibis on 2008-06-12
By the way, using Guarddog to turn off the ubuntu firewall while trying to connect, to have less in the way of getting this thing going.

---

### Post by Tethtibis on 2008-06-12
and sadly, I've spent the time adjusting every configuration in KVpnc and the applet that sits in the network tray, to no avail.

---

### Post by wormser on 2008-06-12
Stop bumping your post every 2 minutes.  Just use the edit feature to add updates if nobody has answered.  Leaving a thread with no replies can get you better responses.  The gurus like to answer the posts nobody else can.

You need to describe your set up better.  More details = better answers.

---

### Post by Xerp on 2008-06-12
Works fine for me - network manager & pptp. What settings / errors you getting? Most of the time with gre/pptp its your router causing the problems.

---

### Post by Tethtibis on 2008-06-17
sorry, wormser, I'd never noticed that edit button before, now i can't find the delete button to cancel my two add ins. More info..... hrmmmm. This is straight from the Dell website.
1	223-1342	Inspiron 1420, Intel Core 2 Duo T5450, 1.66GHz, 667Mhz, 2ML2 Cache
1	320-5524	Basic Black Matte LCD back color
1	311-7253	1GB, DDR2, 667MHz 2 Dimm
1	320-5497	Anti-glare, widescreen 14.1 inch display (1280x800)
1	320-5496	NVIDIA (R) GeForce TM Go 8400M GS with 128MB dedicated graphic memory
1	341-4864	120G 5400RPM SATA Hard Drive
1	420-7901	Ubuntu Linux version 7.10 withDVD Playback
1	430-0493	Integrated 10/100 Network Cardand Modem, for Inspiron
1	313-5277	8X DVD+/-RW Dual Layer Drive for Inspiron
1	313-4783	Integrated High Definition Audio 2.0
1	430-2334	Intel 3945 WLAN (802.11a/g) Mini Card
1	320-5523	No Camera
1	312-0539	56 WHr 6-cell Lithium Ion Primary Battery, for Inspiron 1420
1	950-3337	1 Year Limited Warranty
1	960-2780	Warranty Support,Initial Year
1	987-5397	Dell Hardware Warranty Plus Return To Depot, Initial Year
1	983-3180	Type 12- Mail-InService, 24x7 TechnicalSupport, Initial Year
1	987-8139	No Warranty, Year 2 and 3
1	310-9348	Intel Centrino Core Duo Processor


Now about the PPTP VPN, my system's admin says only that it is the default windows VPN setup, and he didn't change anything when installing it. And it works with no tweaks what so ever in Windows.....

And since this initial setup, I've reinstalled Ubuntu 8.04 from scratch and added a gig of ram.

And no error messages, Xerp, I get the little acending bar icon with a lock on it, But i can't browse the network or use my Terminal server connections like I can at work.

I just got some more info from my system's admin, he says it might be because the domain blocks anything without the proper Kerberos (hope i spelled that right) authentication. Is there a program I can install to authenticate Kerberos or something?

---

### Post by Tethtibis on 2008-07-01
has it been long enough to bump this yet?

---

