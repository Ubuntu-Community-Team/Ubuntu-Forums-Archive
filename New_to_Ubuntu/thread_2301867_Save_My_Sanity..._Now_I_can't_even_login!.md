---
title: "Save My Sanity... Now I can't even login!"
date: 2015-11-05
forum: New to Ubuntu
---

### Post by Piro_Alexander on 2015-11-05
Okay, so, last week my hard drive died on me (3rd one in the past 2 years...) that had my windows installation. My computer (that I built) doesn't have a CD drive (the one i had busted and haven't had money to get a new one) and for whatever reason it woudln't let me install windows onto it from a USB... So I instaled Ubuntu, thinking "i do alot of programming, am generally technologically inclined, this shouldn't be toooo bad"... oh how wrong I was. this has been a living nightmare this past week. I've managed to soft brick my system, and lock myself out several times... and IDK how much more I can take......


This time... I have 3 screens on my computer, but can't use them because I didn't have my graphics card drivers installed... wasn't working for whatever reason. So I found one that seemed to work (nvidia btw) and installed drivers and all was well enough....untill I tried to turn the 3rd screen on. I opened what I thoguht was the control panel, tried to turn the screen on, and it prompted me to save things to... uhm. Xserver? that doesn't seem right... but I clicked OK, and then it said to restart, so I did. and now when I try to login my 3rd screen that I was trying to login to is another screen, my first 2 screens are merged as 1 (can still move between all 3, just the 3rd one isn't linked to the other 2 like they are together) and I can't login to my acccount OR the guest....


I haven't enough experience with linux to really know...anything. I just wanted to be able to use the internet, to have my graphic cards' drivers installed, and to install steam. the plan was to get that out of the way and then start learning the system and getting more configure-y after that.......


And to add to my anger, I've asked a few people that know linux better than myself.. .and basically got the equivilant of "if you can't figure this out, you're too stupid to be on linux".........

Also I was told by 1 person to get them an error report.... when I asked how, they just ignored me....


SMS...Save My Sanity....

---

### Post by Bashing-om on 2015-11-05
Piro_Alexander; Hello; Welcome to the forum .

I do not know that I can help the end goal of 3 functioning monitors, but I can help save your sanity and at least get the system booting.

Try;
Disconnect all but the primary monitor;
Boot the system to the grub boot menu -> advanced options -> recovery kernel -> recovery console -> fail safe boot.

can you activate the GUI at this point ?
If so we can work on getting the graphics driver properly installed
OR find out what else the fault may be.

a) This is linux, if it is hard, you are doing something wrong
b) No one was born knowing, we do understand this
c) Here there are no stupid questions, except the one you do not ask
d) We address the issue, and get it resolved.

[INDENT][INDENT]this is 'buntu
[INDENT][INDENT][INDENT]all for 1 and
[INDENT][INDENT][INDENT][INDENT]one for all
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oldos2er on 2015-11-06
Please list your hardware specs, particularly video card make/model, and Ubuntu version.

---

### Post by Piro_Alexander on 2015-11-11
Sorry I didn't respond, I ended up really busy with work and had to put that in priority.

I cannot get to a gui because i get an error "The system is running in low-graphics mode" "your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself." with an OK box that I can't click or enter through (in fact my mouse is nonexistent)

I have a custom built PC-
Intell Haswell i5 (4690K)
ASRock z97 Extreme6 mobo
2x Zotac nVidia gtx 570 graphic cards
16gb DDR3 ram
Western Digital blue 1tb HDD (was my backup, but my SDD died on me and yeah)

Ubuntu version... uhm. uh. 14.04?

---

### Post by Bashing-om on 2015-11-11
Piro_Alexander; Hey !

Making progress; Maybe " nVidia gtx 570 graphic cards " ....
[http://www.nvidia.com/download/driverResults.aspx/92826/en-us](http://www.nvidia.com/download/driverResults.aspx/92826/en-us)
Nvidia recommends the 352 version driver for this card, not available in the 14.04 software repository. 
We do have options !

1st however is to get you booting to something we can work from.
One option:
What results in an attempt to boot to the grub boot menu:
reboot and as soon as the bios screen clears depress and hold a *shift* key -> grub boot menu 
advance options -> recovery kernel -> resume normal boot.
In this environment Kernel Mode Setting is disabled such that the kernel's fall back video driver is loaded. 

Do you boot to a usable GUI ? Degraded graphics is OK at this point.
If you can get to this point we work to get a supported driver installed.

Else we do something else to get us a work environment.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

