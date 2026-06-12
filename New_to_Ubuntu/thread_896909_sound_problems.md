---
title: "sound problems"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by fignig on 2008-08-21
so i think i'm having sound problems. i can hear this very high pitched noise in my headphones and it's very constant. the sound from streaming site and my rhythmbox music player are kinda horrid. are there anyways to clean up sound for ubuntu? i'm using the alsa sound thing, is that the best? wat are ways to getting the best possible sound from my machine?

---

### Post by gobbles414 on 2008-08-21
ALSA should be fine. Which version of Ubuntu are you running?

It sounds like your speakers may be getting some feedback from an active microphone and/or microphone port. In Ubuntu, right click on the speaker icon and choose *Open Volume Control*. Now, go into *Edit => Preferences*. Put a checkmark in each checkbox, and then close the Preferences window. Mute anything having to do with capture, microphones, etc. Repeat the above steps for every device in the *File => Change Devices* area. Then, restart your computer.

If none of this works... From your Ubuntu desktop screen, go *System => Preferences => Sound*, and switch everything from ALSA to OSS. Then, restart your computer.

Did either of these ideas help?

---

### Post by skyttan on 2008-08-23
Well, it helped me thank you with my problems with alsa constantly stopp working! :)

---

### Post by gobbles414 on 2008-08-23
> **skyttan said:**
> Well, it helped me thank you with my problems with alsa constantly stopp working! :) I'm glad that you found the information helpful, skyttan. Fignig, has your problem been solved as well?

---

### Post by fignig on 2008-08-25
> **gobbles414 said:**
> I'm glad that you found the information helpful, skyttan. Fignig, has your problem been solved as well?

kinda. but the volume control still says alsa mixer? should i uninstall all of the alsa programs?

---

### Post by fignig on 2008-08-25
> **fignig said:**
> kinda. but the volume control still says alsa mixer? should i uninstall all of the alsa programs?

and now that i switched to the oss. when i switch songs this weird beep like i'm taking the pin off of a vinyl comes up. it's kinda weird especially when i'm wearing headphones and the volume is kinda loud the beep gets really loud. wtf is it and how do i stop it?

---

### Post by gobbles414 on 2008-08-25
Did muting all of ALSA's microphone/capture options fix your problem? If so, you don't need to use OSS. If ALSA still isn't functioning correctly for you, try the following changes...

> and now that i switched to the oss. when i switch songs this weird beep like i'm taking the pin off of a vinyl comes up. it's kinda weird especially when i'm wearing headphones and the volume is kinda loud the beep gets really loud. wtf is it and how do i stop it? ALSA is meant to replace OSS technology, OSS is older than ALSA. Since OSS is older, you may encounter some unexpected behaviors such as the noise that you get when switching from one song to another song. You might want to try switching from OSS to PulseAudio (playback) in *System => Preferences => Sound*. Be aware that Hardy is the first version of Ubuntu to provide a PulseAudio playback option.

> kinda. but the volume control still says alsa mixer? should i uninstall all of the alsa programs? Don't uninstall any ALSA programs, as your computer might automatically attempt to uninstall more crucial programs at the same time! Instead, Right-click on the speaker icon in Ubuntu's upper panel, and choose *Preferences*. Once you're in there select the OSS-related entry from the drop-down menu, and then "Volume" (or similar) from the list of OSS options. Close that window, then right-click on the speaker icon again an choose *Open Volume Control*. Finally, go *File => Change Device* and choose the OSS-related option. Now, whenever you use the volume keys on your keyboard and/or the slider in the speaker icon, you'll be controlling the main volume of OSS playback.

If you decided to switch from OSS to PulseAudio, do the following... Right-click on the speaker icon in Ubuntu's upper panel, and choose *Preferences*. Once you're in there select the PulseAudio-related entry from the drop-down menu, and then "Master" (or similar) from the list of PulseAudio options. Close that window, then right-click on the speaker icon again an choose *Open Volume Control*. Finally, go *File => Change Device* and choose the playback-related PulseAudio option. Now, whenever you use the volume keys on your keyboard and/or the slider in the speaker icon, you'll be controlling the main volume of PulseAudio playback.

Did any of these ideas help you?

---

### Post by fignig on 2008-08-29
> **gobbles414 said:**
> Did muting all of ALSA's microphone/capture options fix your problem? If so, you don't need to use OSS. If ALSA still isn't functioning correctly for you, try the following changes...

 ALSA is meant to replace OSS technology, OSS is older than ALSA. Since OSS is older, you may encounter some unexpected behaviors such as the noise that you get when switching from one song to another song. You might want to try switching from OSS to PulseAudio (playback) in *System => Preferences => Sound*. Be aware that Hardy is the first version of Ubuntu to provide a PulseAudio playback option.

 Don't uninstall any ALSA programs, as your computer might automatically attempt to uninstall more crucial programs at the same time! Instead, Right-click on the speaker icon in Ubuntu's upper panel, and choose *Preferences*. Once you're in there select the OSS-related entry from the drop-down menu, and then "Volume" (or similar) from the list of OSS options. Close that window, then right-click on the speaker icon again an choose *Open Volume Control*. Finally, go *File => Change Device* and choose the OSS-related option. Now, whenever you use the volume keys on your keyboard and/or the slider in the speaker icon, you'll be controlling the main volume of OSS playback.

If you decided to switch from OSS to PulseAudio, do the following... Right-click on the speaker icon in Ubuntu's upper panel, and choose *Preferences*. Once you're in there select the PulseAudio-related entry from the drop-down menu, and then "Master" (or similar) from the list of PulseAudio options. Close that window, then right-click on the speaker icon again an choose *Open Volume Control*. Finally, go *File => Change Device* and choose the playback-related PulseAudio option. Now, whenever you use the volume keys on your keyboard and/or the slider in the speaker icon, you'll be controlling the main volume of PulseAudio playback.

Did any of these ideas help you?


will pulse audio help me use more than 1 type of sound source?

---

### Post by markbuntu on 2008-08-29
Yes, it will. 

You can read my guide if you have a few spare hours (You can skip the beginning part and start at the Introduction, You can also skip all the links and just read it):


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Crafty Kisses on 2008-08-29
Post the results of > lspci

---

### Post by fignig on 2008-08-31
> **Codename said:**
> Post the results of > lspci

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
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
01:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
05:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)

i switched back to alsa. but i can't seem to open more than 1 source of sound or i'll have to restart. it's weird b/c if i want to use banshee i can't if i've already opened an online video. and the sound just isn't quite as good as i wanted it. is there an equalizer for constant sound on the terminal?

---

### Post by gobbles414 on 2008-09-01
> i switched back to alsa. but i can't seem to open more than 1 source of sound or i'll have to restart. I recently encountered a similar problem on my Ubuntu PC using while using ALSA. I eliminated the problem by switching from ALSA to PulseAudio. I recommend that you try PulseAudio, as it is the newest sound option in Ubuntu and the most likely to give you pleasing results.

---

