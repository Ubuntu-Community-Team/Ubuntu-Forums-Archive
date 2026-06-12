---
title: "Sound issues (need help/advice)"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by amyg on 2008-08-29
Greetings,

I've been on ubuntu for a few months now, and enjoy using it.  That being said, it takes me awhile to understand how things work and how to go about fixing things.

Anyway -

A few weeks ago my daughter mangled my headset.  I use it primarily for World of Warcraft arenas and such.  It didn't seem like such a big deal since I could use my husband's headset, however this one was USB.

I did some searches on the forum and managed to get sound to work through the headset.  For one night.  The next morning when I turned on my computer the only sound I could hear was with skype, and through my headset.

I continued tinkering to no avail.  At one point I managed to get some sound back through the speakers, but none through WoW and any flash on firefox.  My friend who introduced me to linux tried to help.  Eventually we unplugged the headset, and he managed to get sound restored to the speakers.

Last night, I was doing arena's which is not great without voice.  I plugged in the headset thinking I could just use the mic without dealing with the sound (retarded I know).  As soon as I plugged it in (without messing with anything), I lost sound to World of Warcraft.  I unplugged, restarted, checked my mixers, and cannot get sound back on.

1)  Any idea how to get the sound back working?  (I'll see what I can do and/or hassle my poor friend.)

2)  I'm using Ubuntu 8.04 which uses pulse audio.  I've seen many threads of people hating it and some of people loving it.  It worked fine for me prior to the USB headset.

3)  Logitech USB headset - I've seen many people using these, but for the life of me I obviously cannot get it to work.  At this point, if I can get sound restored properly I'll probably just buy a new headset, however I'm willing to read/hear any pointers on how to get it to work.  It's all a learning experience for me.

4)  As I said, I'm new to doing any of this.  I get frustrated at myself pretty easily, and it doesn't help when I have everyone (but this one friend) telling me to just go back to Windows.  I don't particularly want to (though I run xp through VB on occasion).  My friend helps when he can, but he's a busy guy.  

5) Oh yeah, almost forgot, to get the firefox sound and WoW sound  back on he installed libflashplayer.  After he installed this certain websites will immediately close down firefox.  I cannot access paypal or even weather.com without it immediately closing down.  At this point I have to access them through XP on my VB.  Any idea about that?


So I'm sorry this is long, and I'd really appreciate any help that can be thrown at me.  

Please be kind :(

---

### Post by amyg on 2008-08-29
anyone?  :(  i'm searching threads but not finding anything that has worked so far.

---

### Post by hopkinsjeni on 2008-08-29
If it makes you feel better I had a logitech USB headset and used it on windows and ubuntu, one day it did the same thing and nothing could fix it, bought a new headset and have been fine since. 
It could just be tweaking on ubuntu but I can't think what would make it loose it's sound and come back again only to again shortly afterwards

---

### Post by Crafty Kisses on 2008-08-29
Post the output of > lspci

---

### Post by amyg on 2008-08-29
```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
05:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)

```

---

### Post by amyg on 2008-08-29
> **hopkinsjeni said:**
> If it makes you feel better I had a logitech USB headset and used it on windows and ubuntu, one day it did the same thing and nothing could fix it, bought a new headset and have been fine since. 
It could just be tweaking on ubuntu but I can't think what would make it loose it's sound and come back again only to again shortly afterwards

Any tips on how to get my world of warcraft sound to come back out of my normal speakers again?  I'll buy a different headset this weekend, but it sucks trying to raid/arena without any sound at all.

---

### Post by hopkinsjeni on 2008-08-30
Are you using a dual boot? I found that for some unbeknown reason when i went into windows and tweaked my settings there it suddenly worked in linux the next time I used it. Don't ask me why, I have no idea but it worked with for me when I had sound problems also.

---

### Post by Nepherte on 2008-08-30
If you intend on buying a new headset, you better take one with a 3,5 mm jack that plugs in your normal sound card.

---

### Post by eggdeng on 2008-08-30
May be a question of telling alsa to use the headphones as the default device, which you can do as follows
```
asoundconf list
```
to see how alsa identifies the available devices. Then run
```
asoundconf set-default-card xyz
```
where xyz is the name of the device you want to use, according to the output of the 1st command.
Reboot for changes to take effect.

---

### Post by amyg on 2008-08-30
Hop - I run WoW through Wine, never had any previous issues (if that's what you meant by dual boot).  I have a VB but I don't use it for WoW.

Neph - yeah, that's what I intend to do.

Eggdeng - I've tried that a few times =/  Everything but the sound in WoW is back.

---

