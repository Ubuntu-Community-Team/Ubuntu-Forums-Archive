---
title: "Lubuntu static screen Inspirion 800"
date: 2014-06-02
forum: New to Ubuntu
---

### Post by corey13 on 2014-06-02
I have been trying to get an old laptop I bought at a yard sale to work. It had Windows XP pro on it, or so it seemed but was getting messages basically saying it was a knock off version. So, after some research I decided to install Lubuntu 14.14 (I think that was it) and things went pretty smooth. Now that I have it installed and running, the desktop has three separate sections with what appears to be static between each. Basically, I see my mouse in 3 places and window in 3 places but unable to view entire windows. I was able to get it to log onto the net and found the "start" > accessories > LXTerminal to try the suggestions I found on the web. Only thing is, I am a complete noob when it comes these matters and seem to be missing steps or answers are explained in a way as to be way above my knowledge. So, if someone could help me step by baby step on exactly what I need to do to fix this problem I would greatly appreciate it.

My experiences so far:

* First I tried Puppy Linux and was able to get the same issue fixed by use xworgwizard in the prompt.

* I could not get the Puppy Linux to connect to the internet, after three hours of trying I decided to try a different one.

* Found reviews on Lubuntu on Youtube and followed steps to create a "Live CD" that was 689 MB and installed.

* Fought my way through the "static" to get it installed.

* Tried different xorg commands including xorg -configure and others from forums. Reads a message asking if I ment 
   'forg.'

I am pretty sure you will need me to tell what I have, and am such a noob I will need help on finding how to get the information needed. If you could use a step-by-step instructions to make up for my lack of experience I would be grateful, an example being...

start > accessories >  LXTerminal > type: "blah blah" > type: "blah blah" > create file by: "Blah blah" > move file by: "Blah blah" 

This is how noobish I am. Seems when I research and find a step I need to take, I end up getting lost in trying to figure out how to accomplish said task.

Thank you in advance for your extreme patiences and time in helping me.

***Edit***
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 02)
 00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 02)
00:1f.2 USB controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
 01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Rage Mobility 128 AGP 4X/Mobility M4
02:03.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
02:06.0 Ethernet controller: 3Com Corporation 3c556 Hurricane CardBus [Cyclone] (rev 10)
 02:06.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 10)
02:0f.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:0f.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
 02:0f.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller
**Edit**

---

### Post by mörgæs on 2014-06-02
Hi, welcome to the fora.

You have a very old graphics processor and it might be worthwhile to try VESA drivers. More info in the link in my signature.

---

### Post by corey13 on 2014-06-02
Okay... noting the above post I listed before, I am completely new and lost at this. Following the links in your signature just leads to more confusion as I have no idea what I am looking at and it's not written for the "average Joe" to read and understand. Perhaps if it gave a little information on what it is I am looking at and how it works would be useful to a noob. My technical lingo is about a 3 out 10... those links lead to technical lingo that is 7 out of 10.

---

### Post by mörgæs on 2014-06-02
Just search in the text for VESA and try in a live boot if you get a better screen picture (press F6 at the boot menu and so on).

---

