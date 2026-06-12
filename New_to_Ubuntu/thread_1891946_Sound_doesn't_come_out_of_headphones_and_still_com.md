---
title: "Sound doesn't come out of headphones and still comes out of speakers"
date: 2011-12-06
forum: New to Ubuntu
---

### Post by thelastspud on 2011-12-06
After I plug in the headphones the sound keeps coming from the speakers and not the headphones 
I run 10.10, here is some sound info that I think might help.
anybody have any tips?
```
Manufacturer:      ASUSTeK Computer Inc.        
Product Name:      K52Je
Product Version:   1.0       


!!Kernel Information
!!------------------

Kernel release:    2.6.35-31-generic-pae
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------

snd_hda_intel
snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd5200000 irq 47
 1 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xd0040000 irq 48


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
 
```

---

### Post by ilikelinuxitisthebest on 2011-12-10
enter the code ```
sudo lspci -v
``` and paste the output

---

