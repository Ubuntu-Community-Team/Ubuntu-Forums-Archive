---
title: "Sound Problem"
date: 2012-01-14
forum: New to Ubuntu
---

### Post by inayatseliya on 2012-01-14
Hello Everyone,
 I am absolutely new to ubuntu (Linux) OS, I downloaded Ubuntu Desktop OS 11.10 and tried installing from USB but couldn't install, so I give a try to 10.04 LTS version, it got install but sound was not available it also suggest me to update OS 12.04 and so I did it, still i can't get sound working, I am using windows 7 on that machine and its working perfectly. 
Its Gigabyte Motherboard H55M-S2 with Realtek High Definition Audio - ALC888B Codec and my display card is ATI 4300/4500 Series it also have audio codec, ubuntu is detecting audio for ATI but not for Realtek which i want to use for my 5.1 speaker. 

I tried to search on google and this website but I couldn't do. To be honest it's to much code thing in linux, i really want to use it, but without sound I don't think I can. can expert over here solve my problem or I have to uninstall linux

---

### Post by LinuxCharms on 2012-01-14
Let's let Ubuntu Cat have a crack at this!

So sound isn't working... You see up on the top of your screen you have a bar? You should see a bit to the right that there's a little sound symbol. Click it, then go into sound settings. Tell me what's selected.

---

### Post by inayatseliya on 2012-01-15
Thanks for your reply Sir
After Clicking on Upper right sound symbol I clicked on **sound settings** , in **Hardware** Tab choose a devise to configure its empty nothing shows there.
does this means my sound driver is not installed?

---

### Post by Rodney9 on 2012-01-15
These two manuals give good advice for solving sound problems:

[Sound Troubleshooting Guide]("https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit")
(by Lkjoel and Wildmanne39)


[Sound Troubleshooting Procedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")
(by Mark Rijckenberg)

---

### Post by inayatseliya on 2012-01-15
after doing some coding i got this thing but still no sound 

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by inayatseliya on 2012-01-15
in upper right sound setting in hardware and in output Tab i can see 

[B]RV710/730 HDMI Audio [Radeon HD 4000 Series]
1 Output
Digital Stereo (HDMI) Output
[/B]
which is my ATI Display Card, I even try to make default card and device to realtek one but still  no success.

---

### Post by inayatseliya on 2012-01-16
Can reinstalling Ubuntu solve my sound problem?

---

