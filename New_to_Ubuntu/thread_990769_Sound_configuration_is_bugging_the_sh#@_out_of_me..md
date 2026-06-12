---
title: "Sound configuration is bugging the sh#@ out of me."
date: 2008-11-23
forum: New to Ubuntu
---

### Post by chen_tso on 2008-11-23
So far I'm pretty disappointed with Intrepid Ibex. I have an onboard Nvidia sound chip but I have an Creative Audigy2 plugged in. I've never had sound problems with the previous releases of Ubuntu. With 8.10, I can't get sound to all work. Mostly in Firefox flash, and the mplayer-plugin. 

I've tried several solutions after googling. Uninstalling libflashsupport, reinstalling it, installing flashplugin-non-free-extrasounds. I did manage to get it all to work at one point (flash and mplayerplugin), but then after a reboot, sound problem was back to square one. I've tried so many things that I don't even remember what it was that I tried to make it work. 

I'm currently in a middle of a midterm exam cramming crisis. All I want to do is listen to some web radio to help me study. Yet trying to figure how to fc$king configure sound has proven to be more stressful than studying for my exam. 

Can someone please explain to me what the difference between ALSA and OSS is? And which one I should use for my setting? And what is PulseAudio? In my search to fix my problem I've seen people say to stop PulseAudio session, some say to reset PulseAudio. What the f is PulseAudio? I know it's not possible for anyone to be able to fix my firefox/sound problem with the description I have given, but has anyone out there with the same hardware as mine figured out how to fix the firefox sound problem? 

Please??

---

### Post by zzHanks on 2008-11-23
It looks like I'm having the same problem. (Same card)

No sound in Flash at all.

I connected my amplifier to the Line out output on the main board instead, all sounds worked fine. Then one day the other channel stops working (fried or something).

My luck...

---

### Post by gigaferz on 2008-11-23
im sorry to hear that, and i really understand you.

But , Keep in mind that is partly your fault, why upgrade ubuntu right away?

I was like that since 6.06, problem after problem after problem.... and there is a point when the forums simply will not help you anymore and youll get exhausted of googling , and reading , and trying, compiling,,,etc,etc.....

At this point, honestly I recommend you just to go back and always wait at least 2 months before doing the change. Honestly they should make them like 10 months releases, I had some feistys installed and my friend wanted acetone2iso but i just couldnt install it because of missing packages, different versions, etc... so I was forced to upgrade.

Anyways my point is dont stress yourself  like that,  is not worth it, in 6 months,  youll have a graphics problem, networking problem, mics not working, permissions problems, etc etc.... If it aint broken leave it alone.

---

### Post by psyke83 on 2008-11-24
Take a look at [this]("http://ubuntuforums.org/showthread.php?t=789578") guide.

---

### Post by gn2 on 2008-11-24
I have Realtek on-board sound and a PCI Audigy SE in my desktop.
The cure to my audio problems was to remove all the pulse audio packages and libflashsupport.

---

### Post by chen_tso on 2009-03-09
I thought I'd bring bump this article back since I've solved my problem and I'm sure many who still have yet to solve the problem had the same issue. 

PulseAudio did not fix anything. Thanks, though. The problem was that I have an onboard sound card on top of the Audigy card. Disabling sound card from BIOS didn't seem to help, Ubuntu could still use it. (Question: Why would Ubuntu do this? Still use a disabled device?)

To fix this, I checked out what module my onboard by "lsmod" and saw that my onboard was "snd_hda_intel" (different for other people). Then edit the file /etc/modprobe.d/blacklist and add exactly that module name to the end of the list.

---

### Post by Paul D on 2009-11-01
I am also a new Ubuntu user, though I did install version 8.something in one of my PCs last year.  (So what?) Enough with my history....  I now am checking out Ubuntu 9.10 Studio. So here is my issue; The MoBo I am using is AMD has no audio ICs installed. The BIOS seems to not have any settings to choose anything about it - that I could find. Briefly back to my history story, I had installed that v8.x in a different MoBo and the audio worked fine.
So now I have an Audigy2 PCI audio card in this MoBo that has no on-board audio ICs.
lspci shows Multimedia audio controller: Creative Labs SB Audigy (rev 04), but that is the end of the story, no audio coming from it. By the way, I just purged XP from this same PC where the audio worked. I checked the volume and mute buttons. I get the impression that Ubuntu can see the Audigy2 hardware, but no driver for it? I am also bugged by this.
Help please? The next issue will be for the Ubuntu file browser to see my other LAN XP PCs, but one thing at a time.

---

