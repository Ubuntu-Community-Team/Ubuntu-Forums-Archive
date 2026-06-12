---
title: "amarok and rhythmbox stopped working"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by phread59 on 2008-08-09
I have a cd in the machine.  It is a copy of a cd I own.  It worked fine a few days ago but now neither Amarok nor rhythmbox will play it.  Keeps comming up with errors and incompatible file type or no plug in for this file type.  It worked last week but a few updates later no soap.  I did a reinstall of both but no soap.  I may try a total removal and reinstall later.  Any suggestions as to what happened?

Mark Shuman

---

### Post by Crafty Kisses on 2008-08-09
Weird, do you have all the codecs installed?

Post the following output: ```
lspci
```

---

### Post by bpowell2005 on 2008-08-09
> **phread59 said:**
> I have a cd in the machine.  It is a copy of a cd I own.  It worked fine a few days ago but now neither Amarok nor rhythmbox will play it.  Keeps comming up with errors and incompatible file type or no plug in for this file type.  It worked last week but a few updates later no soap.  I did a reinstall of both but no soap.  I may try a total removal and reinstall later.  Any suggestions as to what happened?

Mark Shuman

Is it possible the CD was corrupted or damaged? Does the original CD play okay?

---

### Post by phread59 on 2008-08-09
Here ya go lspci:00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
phread59@phread59-desktop:~$ 

don't know if that will help.  Checked another CD, a factory one and it will not play either.  Somehow something got broken in an update.

Mark Shuman

PS: it's 1:09 AM and I'm done in.  I'm heading to bed.  I'll check back in in the morning.  Thanks for the help.

---

### Post by Crafty Kisses on 2008-08-09
Have you tried if any music will run in VLC.

---

### Post by phread59 on 2008-08-09
VLC sees the disc and shows that it is playing, but no audio.  I'll see if I can find  some audio on the net and verify that I can play audio.

Mark Shuman

---

### Post by phread59 on 2008-08-09
I checked Youtube but no audio at all.  I'm going to reboot into an older kernel version and see if that helps.

Mark Shuman

---

### Post by phread59 on 2008-08-09
Using an older kernel, and still the same.  I have some music saved in MP3's they will not play either.  It almost appears I need some kind of codec or something similar.  Any thoughts on that?  I'm going to try one more thing and report back.

Mark Shuman

---

### Post by phread59 on 2008-08-09
Tried Frostwire and it is dead too.  I'm now officially at a loss.  Anyone out there have any idea?  

Mark Shuman

---

### Post by billgoldberg on 2008-08-09
Hmm.

Could it be that your speakers died?

--

Besides that, this command should install all the codecs you'll ever need:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
```

Give it a try to see if it works.

--

You could also try and go into "system -> preferences -> sound" (it could be system -> administration -> sound also, I'm in fluxbox right now).

And change everything to something else, like ALSA.

Then see if the audio files will play.

---

### Post by phread59 on 2008-08-09
Bill, it did not work.  I keep getting the red circle with a clear bar in the middle for each song.  It is like the stop sign only round.  There is an incompatability or something got changed in an update.  There is a possability that the speakers or the motherboard's onboard audio died.  I'm currently not sure.  It just seems that something vital was changed during an automatic update.  I'm going to try to uninstall rhythmbox and reinstall completely with synaptic and see what happens.

Mark Shuman

---

### Post by phread59 on 2008-08-09
OK clicked on the red ball and got the following message:

Failed to connect stream: invalid argument.

I get that message with some vidio streams as well.  But it is only a very few.  Not sure where I need to go on this one.  I'm hungry and gonna go get something to eat.  I'll be back later.

Mark Shuman

PS I've got Puppy on an USB stick.  I'll plug that in and try that and see what happens.  See if it is an Ubuntu thing or a hardware issue.  I'll try that later and give it a whirl.

---

### Post by phread59 on 2008-08-10
OK it is definatly an issue with Ubuntu.  I broke down and booted into Windoze and tried the CD I made.  It playes just fine.  so it is not a hardware issue.  Somehow I got a bad update and broke the audio.  Anyone have any suggestions on where to look?

Mark Shuman

---

### Post by phread59 on 2008-08-10
Bump for the Sunday evening crowd

---

