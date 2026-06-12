---
title: "No sound with new sound card - Creative Sound Blaster 5.1"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by MattThLinuxNewb on 2008-10-29
I just got a Creative Sound Blaster 5.1 PCI card and it's not working with Ubuntu 8.04. Clicking on the volume control icon in Gnome says no device was found or devices aren't configured correctly. From exhaustive searching it looks like the card is supported by ALSA ([http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)) yet it doesn't work.
lspci returns the following:
```

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
05:07.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X (rev 08)

```
Looks like the card is detected (last line of output).
Do I need to manually compile ALSA? Any help would be much appreciated.
Note: I've already disabled the onboard sound in the BIOS.
Cheers,
Matt

---

### Post by brandoncolorado on 2008-10-30
[http://hardware4linux.info/module/EMU10K1X/](http://hardware4linux.info/module/EMU10K1X/)

Strange.

Maybe post back tomorrow after 8.10.

---

### Post by brandoncolorado on 2008-10-30
[http://ubuntuforums.org/archive/index.php/t-846804.html](http://ubuntuforums.org/archive/index.php/t-846804.html)

"vrdabomb5717
August 27th, 2008, 03:30 AM
Yeah, I had that too. I finally got tired of the problems and updated my installation to the latest daily build of Intrepid Ibex, and lo and behold, that fixed the problem! The hardware recognition definitely got screwed up somewhere along the line, but a full reinstallation fixed that. Now I have music playing in Rhythmbox and I can finally move along to Ubuntu fulltime!"

---

### Post by Eisenwinter on 2008-10-30
You need to compile ALSA manually, in the configure command include the parameter --with-cards=emu10k1.

I have an EMU 1212m, from the EMU 1010 series, also.

---

### Post by MattThLinuxNewb on 2008-10-30
Thanks for the fast replies everyone. I'll definitely be upgrading to 8.10 when it's released, hope that fixes it.

I've noticed when starting Ubuntu, just before the login screen it says something along the lines of "unknown header 7f in PCI device, ignoring". Is that relevant?

Eisenwinter: Which ALSA package do I use that option with? Which packages should I download and compile from [http://www.alsa-project.org/](http://www.alsa-project.org/), looks there are quite a few.

Cheers,
Matt

Update: I compiled just the alsa-driver with the --with-cards=emu10k1 parameter. It doesn't work unfortunately, I'm still getting:
```

PCI: device 0000:05:08.0 has unknown header type 7f, ignoring.

```
From what I can see the card isn't being correctly detected at the kernel level. Is that right? Does this mean I need to compile the latest linux kernel with ALSA? :confused:

---

### Post by MattThLinuxNewb on 2008-10-31
Hey everyone,

Just finished downloading and burning an 8.10 image and ran the live-CD. It looks great but still no Sound Blaster 5.1 soundcard support...

I really don't know where to go from here.

Ordering this soundcard took long enough - don't think I could stomach another week (++) of listening to the radio while waiting for a new soundcard to arrive!

Any ideas?

The model name/number of the chip on the actual card is "CA0103-DBQ" if that helps. (I've tried looking it up with no success)

Cheers, Matt

---

