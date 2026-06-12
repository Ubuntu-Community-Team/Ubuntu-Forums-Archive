---
title: "[SOLVED] graphics"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by heyshona_mjdewji on 2008-07-27
hey i jsut installed ubuntu...with some help...but now i have a problem with the graphics...i try the normal graphics thing but it crashes....tried a few times....help please...and im still new so if you can explain it simply...tht would b awesome:)

---

### Post by halitech on 2008-07-27
open a terminal and post the output of
```
lspci
```

do you know what you have for a video card and did you check for and enable the hardware drivers for it - System - Administration - Hardware drivers?

---

### Post by gjoellee on 2008-07-27
for me it seams like yo haven't installed the graphic card driver, if you need help with that just give me a notice

---

### Post by Vakman on 2008-07-27
I agree with halitech. Once you post the output of that we will know what hardware you have (in particular, your video card).

---

### Post by halitech on 2008-07-27
actually, I'm thinking we should get some clarifiation. Are you going to System - Preferences - Appearences and clicking Normal or are you having troubles with the actual desktop and getting graphics to work?

---

### Post by heyshona_mjdewji on 2008-07-27
hey thanks for the promt responces. i go via the system,prefs,appearance,visual effects,normal

as to the lspci...here is what i get

00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:08.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:08.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:08.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

---

### Post by halitech on 2008-07-27
ok, so you have an onboard video card
[color="red"]01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)[/color]

go into System - Admin - Hardware Drivers and see if there is a restricted drive for that card

---

### Post by heyshona_mjdewji on 2008-07-27
"do you know what you have for a video card and did you check for and enable the hardware drivers for it - System - Administration - Hardware drivers?"

my lspci is above and i think there is a vid card...when i went syst admin hardware drivers...there was nothing on teh list.

---

### Post by heyshona_mjdewji on 2008-07-27
here is a screenshot

---

### Post by halitech on 2008-07-27
you would have to have a video card or you wouldn't see any output on your monitor :D

ok, so no restricted drivers for the VIA S3 Unichrome card. 

Under Applications - System do you have an application called Sysinfo listed? if you do, run that and check out the video info. I'm thinking you may not have enough video RAM to run Compiz on your machine.

---

### Post by heyshona_mjdewji on 2008-07-27
i have 704mb reg ram and then have a 2g swap space...is there a way that i can dedicate video ram??

---

### Post by halitech on 2008-07-27
704 sounds like an odd amount of ram. Do you know what the total amount is in the system? Usually the amount of video ram with onboard cards is set in the BIOS

---

### Post by heyshona_mjdewji on 2008-07-27
sorry i have 768 a 512 chip and a 256 chip...both ddr ram....

---

### Post by heyshona_mjdewji on 2008-07-27
is ther an easier way to check bios or do i have to restart and go from tehre

---

### Post by halitech on 2008-07-27
if you open a terminal and do
```
htop
```
it should show you the amount of memory that is available for the system minus whatever the video is using

---

### Post by heyshona_mjdewji on 2008-07-27
when i typed htop it said wansnt installed but then i rebooted and opened bios....VGA share is only 64 mb...can i change that...on bios screen i could only choose between 16...32...64...so yea i dont know what to do or wether i will b able to run compiz....and btw i have also a 2gb swap....is ther a way to use that??

---

### Post by halitech on 2008-07-27
was going to guess that you are using 64 as 704+64=768. 64 *should* be enough although where it is an onboard card, it may interfere. I have an Nvida Gforce 440mx that is only 64 meg and I can use the effects with little problem. Far as I know, there is no way to use your swap space to get more video ram.

---

### Post by heyshona_mjdewji on 2008-07-27
k so now should i try again and see what happens

---

### Post by halitech on 2008-07-27
no harm in trying

---

### Post by heyshona_mjdewji on 2008-07-27
yea its not wrking :(

---

### Post by halitech on 2008-07-27
it may be a case of the on board video you are using doesn't have 3d support which is 1 thing the effects tend to use. Might be worth your while to pick up a cheap 64 or 128meg video card (Nvidia has the fewest issues) and use it instead of the onboard chip

---

### Post by heyshona_mjdewji on 2008-07-27
thanks for trying...ill post another thread with my video card model and see if anyone can relate or know more about if it can work

---

### Post by halitech on 2008-07-27
ok, if you are starting a new thread, mark this one as solved so you don't get any more responses on it

---

### Post by heyshona_mjdewji on 2008-07-27
ok thanks alot

---

