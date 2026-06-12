---
title: "What on earth have I done to my audio?"
date: 2012-01-06
forum: New to Ubuntu
---

### Post by Strawberry Cheesecake on 2012-01-06
Ok, I have to be honest, I know next to nothing about Ubuntu. My brother installed it for me after Windows crashed on my pc about a year ago. So far I've really enjoyed it though, haven't had any problems. That was before I decided to try fiddling with it. The sound wasn't working for my mic, so I did some googling, messed about with terminal when I shouldn't have and now I have lost my volume control on everything and can't find my sound card. This is what it looks like when I do the aplay -l thing:

aplay -l
**** List of PLAYBACK Hardware Devices ****
ALSA lib conf.c:1645:(snd_config_load1) _toplevel_:16:7:Unexpected char
ALSA lib conf.c:3425:(snd_config_hook_load) /home/kristie/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:3286:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3671:(snd_config_update_r) hooks failed, removing configuration
aplay: device_list:232: control open (0): Invalid argument
ALSA lib conf.c:1645:(snd_config_load1) _toplevel_:16:7:Unexpected char
ALSA lib conf.c:3425:(snd_config_hook_load) /home/kristie/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:3286:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3671:(snd_config_update_r) hooks failed, removing configuration
aplay: device_list:232: control open (1): Invalid argument


It.. doesn't look healthy. Be honest, have I completely destroyed it? And can somebody please help me? What do I do? :( It's gnome 10.04 if that helps?

---

### Post by khelben1979 on 2012-01-06
Well.. since you're on a Linux system there isn't really any reason for worries. :popcorn:

Okay... You can start with typing **lspci** from a text terminal, then you copy and paste the text to this thread and I will be able to see what hardware you got inside your PC.

Next step is to determine what sound driver is needed for that specific hardware, and inside the [ALSA SoundCard Matrix]("http://www.alsa-project.org/main/index.php/Matrix:Main") is possible to do quick search.

---

### Post by Strawberry Cheesecake on 2012-01-06
Thank you so much! Here's what popped back:

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
02:00.0 VGA compatible controller: ATI Technologies Inc RV620 LE [Radeon HD 3450]

I do prefer linux, even if I do know barely anything about it ;)

---

### Post by khelben1979 on 2012-01-06
Okay, from that text output I can see that you got the sound hardware from nVidia, I quickly took a look over [here]("http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0"). Type this from a text terminal and copy and paste the output here once again: ```
modinfo soundcore
```

(it's very good to know what version of Ubuntu you're using)

---

### Post by Strawberry Cheesecake on 2012-01-06
filename:       /lib/modules/2.6.32-37-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     51925557ECF0F2838930862
depends:        
vermagic:       2.6.32-37-generic SMP mod_unload modversions 586 
parm:           preclaim_oss:int

Tada! Thanks for the websites as well, they're good places to start learning :) So.. I just double checked, it appears at some point I started using the Lucid Lynx, still 10.04. Does that change anything? It's still running through gnome as far as I know.

---

### Post by khelben1979 on 2012-01-06
Try this: 
```
sudo modprobe snd-intel8x0 
sudo modprobe snd-pcm-oss
sudo modprobe snd-mixer-oss
sudo modprobe snd-seq-oss
```

Then open up Gnome sound mixer and check what it says in there, if it finds your nVidia sound chip.

The sound driver is inside your Linux kernel, and depending on what version of Ubuntu, the kernel version changes and so does all the drivers which comes with it.

---

### Post by Strawberry Cheesecake on 2012-01-06
I'm really sorry, GNOME sound mixer isn't there! It's been vanished along with everything else since this all went wrong. Any way I can get at the kernel and check the drivers? Thank you again for helping me btw.

---

### Post by gsocker on 2012-01-06
Have you tried the suggestion from the error messages you are getting?

```

ALSA lib conf.c:1645:(snd_config_load1) _toplevel_:16:7:Unexpected char
ALSA lib conf.c:3425:(snd_config_hook_load) **/home/kristie/.asoundrc may be old or corrupted: consider to remove or fix it**
ALSA lib conf.c:3286:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3671:(snd_config_update_r) hooks failed, removing configuration

```

You appear to have a invalid ALSA user config file. Since this file should not be needed for normal use, try renaming it to something else and then logging out and back in.

lsmod will give you a list of loaded modules, so you can see if the kernel-level drivers are loaded.

---

### Post by khelben1979 on 2012-01-06
OK.
```

apt-get install alsamixer
```
[(Alsamixer - wiki)]("http://en.wikipedia.org/wiki/Alsamixer")

Then start that application and see how that looks like, you can navigate and press + and - to change the meters.

---

### Post by Strawberry Cheesecake on 2012-01-06
> **khelben1979 said:**
> OK.
```

apt-get install alsamixer
```[(Alsamixer - wiki)]("http://en.wikipedia.org/wiki/Alsamixer")

Then start that application and see how that looks like, you can navigate and press + and - to change the meters.

Ok, I tried that, and it gives me this message:

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I don't know if I'm root :( 

Also, with the lsmod.. It's giving me a lot of information, and I don't know what to do with any of it. I'm sorry, I'm really useless with this stuff, I'm a complete beginner. How do I go about replacing the .asoundrc?

---

### Post by gsocker on 2012-01-06
> **Strawberry Cheesecake said:**
> Ok, I tried that, and it gives me this message:

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I don't know if I'm root :( 

Also, with the lsmod.. It's giving me a lot of information, and I don't know what to do with any of it. I'm sorry, I'm really useless with this stuff, I'm a complete beginner. How do I go about replacing the .asoundrc?

A .asoundrc file is not needed normally. Just rename it to .asoundrc-old for now and see what happens. That files allows customization of ALSA for special cases, but since every ALSA program reads it on startup,  if it's invalid lots of stuff can break...

With the lsmod, post any results starting with "snd" - 
```
lsmod | grep snd
``` will get you a list.

This gives us a starting point. If the kernel modules are loaded, and sound worked before, then something in userspace is most likely the problem.

---

### Post by khelben1979 on 2012-01-06
Okay, try: ```
sudo apt-get install alsamixer
``` instead. 

The sudo command gives root permissions to the command apt-get so it can install the application to your Ubuntu system, it's also possible to search for it using Ubuntu Software Center and install graphically if that feels better. Later after that, you simply run the application without sudo to adjust it's settings if things looks OK from there.

B.t.w. no need to apologize for help in this support forum, just go slow. Unfortunately sleep time for me here in Sweden.. :)

---

