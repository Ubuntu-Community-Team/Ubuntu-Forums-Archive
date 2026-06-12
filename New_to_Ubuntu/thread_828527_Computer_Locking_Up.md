---
title: "Computer Locking Up"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by Bonzzai on 2008-06-13
There will be times when I'm using my laptop when it just crashes and won't respond. What usually happens is all of a sudden, without warning, the screen gets all messed up, all audio stops, and I can't even move my cursor. I thought it would possibly stop happening after I used Ubuntu for a few days (It happened to me when I used to run DreamLinux 3), but it hasn't shown signs of stopping.

Also, Firefox 3 will randomly close out, but I suspect that's a problem with the browser.

I'm running Ubuntu 8.04 on a Presario R3000 computer. I'm not sure what's causing the problem... If anyone could help, that would be perfect (:

---

### Post by Joeb454 on 2008-06-13
What graphics card do you have?

Also do you have desktop effects enabled?

---

### Post by Bonzzai on 2008-06-13
I do have desktop effects enabled... I used to have Compiz/Beryl running on my last distro, it never gave me any problems... But I might have to move down to basic desktop effects xD;

Also, I'm not sure exactly about the video card. I know I have nVidia (something like that), but is there a way for me to check exactly?

Thanks so much for your help x__x

---

### Post by Victormd on 2008-06-13
open a terminal and type lspci
This should list a series of devices installed, including your graphics card (you might have to scroll through to figure it out).

---

### Post by Bonzzai on 2008-06-13
Here's the complete results from that... Sorry if this isn't needed, just in case :S

> 00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go 64M] (rev a3)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)


**Edit:||**
P.S. - I moved the visual effects down to normal. I'll tell you if I still ever have any problems with this.

---

### Post by Joeb454 on 2008-06-13
Try disabling compiz, and see if you still get the issues.

Also, on Hardy (8.04) check System &#8594; Administration &#8594; Hardware Drivers, and see if there's anything in there about drivers that aren't currently enabled.

---

### Post by Bonzzai on 2008-06-13
> **Joeb454 said:**
> Try disabling compiz, and see if you still get the issues.

Also, on Hardy (8.04) check System &#8594; Administration &#8594; Hardware Drivers, and see if there's anything in there about drivers that aren't currently enabled.

Alright, done and done n__n
I'm down to normal, no signs yet, but... There might be randomly later, heh.
I checked that, there are two drivers listed and both are checked :]

---

### Post by Joeb454 on 2008-06-13
Well the 2 drivers installed is a good thing :)

Post back if it crashes (or if it doesn't ;))

---

### Post by Bonzzai on 2008-06-13
Grahhhh. Bad news. It just happened again.
Here's a bit more specific info...

When this happened last time, the screen didn't jumble or anything. It showed exactly what was happening. I was watching a YouTube video, mouse at rest...

The only programs I can think of that I had open are Pidgin and Rhythmbox. Oh, and of course Firefox 3... I had a couple of tabs open is all... -Headdesks-

---

### Post by Joeb454 on 2008-06-13
Hmm strange, I can't think of any reason why it would be locking up the way you described :confused:

---

### Post by stalkier on 2008-06-13
> **Bonzzai said:**
> Grahhhh. Bad news. It just happened again.
Here's a bit more specific info...

When this happened last time, the screen didn't jumble or anything. It showed exactly what was happening. I was watching a YouTube video, mouse at rest...

The only programs I can think of that I had open are Pidgin and Rhythmbox. Oh, and of course Firefox 3... I had a couple of tabs open is all... -Headdesks-

Personally I get lockups a lot using 8.04. At first I thought it was related to not having enough RAM but I recently upgraded to 1.5GB. I get lockups even while NOT using FF3. I use Pidgin, Amarok, and FF3 on a regular basis. Lockups seem to happen even when not using the aforementioned apps. Personally I believe this is a bug in 8.04, not in the apps used/installed. Funny though, I use the exact same setup (software) on both my laptop and my desktop. I only get lockups on my desktop. Weird.

---

### Post by Victormd on 2008-06-13
At least now you know your card is a nVidia Corporation NV17 [GeForce4 440 Go 64M]. This could be your problem right here. This card is not very powerfull and you might in fact run into problems with compiz.

---

### Post by Bonzzai on 2008-06-13
Well, my graphics card always was able to run stuff on Beryl.
It never locked up before. As for RAM, I have 1 GIG of it... But at the moment I'm not using Compiz at all.

Well... I'm hoping it's just a bug in 8.04. Maybe it was an installation error. -Shrugs- I'll order a CD from Ubuntu...

---

### Post by Joeb454 on 2008-06-13
You could try using Ubuntu 7.10 instead? That also has compiz by default.

It's up to you :D

---

### Post by Bonzzai on 2008-06-13
Is there a way to 'downgrade' to an older Ubuntu?
I'm new with the whole Linux thing, sorry x__x
The only way I knew how to keep my files when I upgraded to 8.04 was because it did it for me. Usually I have to pretty much reformat my computer :/

Hopefully this will stop.

---

### Post by Joeb454 on 2008-06-13
If you wanted an older version you would have to backup all your stuff, and then reinstall completely (like you usually do :()

---

### Post by Victormd on 2008-06-13
> **Bonzzai said:**
> Is there a way to 'downgrade' to an older Ubuntu?
I'm new with the whole Linux thing, sorry x__x
The only way I knew how to keep my files when I upgraded to 8.04 was because it did it for me. Usually I have to pretty much reformat my computer :/

Hopefully this will stop.

Unfortunately, to downgrade you pretty much have to reformat, meaning, backup all your data stored on your home folder and any other data you might have...

---

### Post by Victormd on 2008-06-13
> **Bonzzai said:**
> Well, my graphics card always was able to run stuff on Beryl.
It never locked up before. As for RAM, I have 1 GIG of it... But at the moment I'm not using Compiz at all.

Well... I'm hoping it's just a bug in 8.04. Maybe it was an installation error. -Shrugs- I'll order a CD from Ubuntu...

It might be a bug or it might be that Hardy uses more system resources than Gutsy and that's why you're having a hard time with it now...

---

### Post by Bonzzai on 2008-06-13
Wouldn't it be acting more slow if it were having problems, though?
I would HOPE that 1gig of RAM is good enough.
I've disabled Compiz for now, so... I would hope it would be okay x[

---

