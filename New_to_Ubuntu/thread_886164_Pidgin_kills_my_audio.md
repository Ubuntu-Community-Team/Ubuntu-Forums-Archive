---
title: "Pidgin kills my audio"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by VitaminBB on 2008-08-10
The original problem was that after I installed Pidgin I noticed the sounds for Pidgin wouldnt work, they worked for other apps and mp3 but sounds for pidgin wouldnt work, I managed to fix that problem which only created another problem.

When I run Pidgin now I can hear the sound effects for the chat client but all the other audio gets killed, no sound other then Pidgin at all and closing Pidgin doesnt help, it appears I have to restart Ubuntu before audio will work again.

Ive read a bunch of forums on this problem, obviously something lots of ppl are having trouble with but im not reading many solutions.

Also I half decided to say "screw it" and ditch Pidgin for Empathy, however I cant figure out how to get an msn protocol for Empathy so thats useless as well and theres noone out there that seems to know.

Im hoping someone here has an idea ...

---

### Post by freak42 on 2008-08-11
Hi,

which sound architecture are you using in System->Preferences->Sound 
(alsa or pulseaudio or esd, oss... etc)?

What sound method is set in pidgin, Tools->Preferences->Sound->[Sound Method]?

---

### Post by Crafty Kisses on 2008-08-11
That's weird, post the following output of:
```
lspci
```

---

### Post by Novus on 2008-08-11
it would help to know what you did to "solve" the first problem..
Assuming you have pulseaudio installed I suggest changing the pidgin sound method to command and   ```
paplay %s
```

---

### Post by VitaminBB on 2008-08-11
I went to sound under system and switched everything from "auto detect" to "alsa". I get sound from pidgin no problem but miros sound wont work now.

The way I "fixed" the original problem with pidgin was to add the line "aplay %s" to "command", it seemed to get the sound working again for pidgin.

Now im finding that sound for apps like VLC and Miro will die, even if pidgin is not running and even after I start pidgin and continue to get sounds from pidgin, nothing else seems to get sound until I restart and then after awhile things mysteriously lose sound again, wether or not pidgin is run.

Heres the results from lspci

> arghmonkey@Boontwo:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation MCP51 PCI-X GeForce Go 6100 (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:05.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
04:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
04:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

---

### Post by Novus on 2008-08-12
try changing command to ```
paplay %s
``` that is however just a workaround. if you haven't you should read the [_ALSA FAQ_]("http://alsa.opensrc.org/index.php/FAQ#Can_I_use_several_applications_at_once_without_the_second_one_blocking.3F")

---

### Post by VitaminBB on 2008-08-12
I already did that and it works fine.

Heres the problem.
[B]
I went to sound under system and switched everything from "auto detect" to "alsa". I get sound from pidgin no problem but miros sound wont work now.

The way I "fixed" the original problem with pidgin was to add the line "aplay %s" to "command", it seemed to get the sound working again for pidgin.

Now im finding that sound for apps like VLC and Miro will die, even if pidgin is not running and even after I start pidgin and continue to get sounds from pidgin, nothing else seems to get sound until I restart and then after awhile things mysteriously lose sound again, wether or not pidgin is run.[/B]

---

### Post by Fixman on 2008-08-12
Try doing this:

Open a terminal, and write:

```
sudo apt-get install --reinstall pulseaudio
```

then go to "system->preferences->sound" and change everything to pulseaudio.

Something like this:


[CENTER][IMG]http://24.232.227.106/img/inger/1.png[/IMG][/CENTER]

---

### Post by cool_penguin on 2008-08-12
Installing Pulse-audio screwed up my existing Skype installation. Now when I use Skype, my CPU usage is 100% and after a few minutes Skype freezes completely. I am considering switching back to ALSA completely.

---

### Post by VitaminBB on 2008-08-13
Tried the pulseaudio thing, didnt work ...

Still getting the same problem, I dont understand why because it doesnt happen immediately, I can play youtube videos with sound, pidgin with sound etc, but for example tonight everything seemed to be fine, i switch over to Miro to watch some video, everythings fine, I switch back to firefox to watch some video and the sound is gone.

The sound still works fine in miro and the sound for pidgin seems to be ok too but everything else is dead, no sound for youtube or any other videos, even vlc ...

Did the lspci info help anyone?

Any other ideas?

---

### Post by Novus on 2008-08-13
> **VitaminBB said:**
> Any other ideas?Have you installed the pulseaudio plugins for the programs you have problems with? like

```
gstreamer0.10-pulseaudio      #If you use gstreamer for rendering in miro
vlc-plugin-pulse              #VLC plugin for pulseaudio
libflashsupport               #Bugfix, soundproblems with flash 9 and pulse audio
```

---

### Post by VitaminBB on 2008-08-16
Pulseaudio is installed and works ...

The problem remains, if I have pidgin or some other program launched I can get sound through youtube etc but VLC or pidgin or miro or all or either etc wont work, I can then switch back and forth from alsa to pulse all I want without making any noticeable difference, sound will work on some things and not on others.

Keep in mind if I restart sound works everywhere but at some magical point it decides to stop working for some things, I have no idea why.

Other suggestions?

---

### Post by nhasian on 2008-10-12
you dont need to restart the pc.  just log out and log back in and the sound will work again.  i experienced the same thing and discovered it was due to the flash plugin in firefox.  i uninstalled flash 9 and installed the flash 10 beta and its working a lot better for me now.

---

