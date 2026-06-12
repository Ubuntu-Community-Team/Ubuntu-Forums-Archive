---
title: "Microphone has stopped working"
date: 2014-04-28
forum: New to Ubuntu
---

### Post by prathamesh2 on 2014-04-28
[COLOR=#000000]I am relatively new to Ubuntu. So, pardon me for my half baked knowledge. 
My microphone has suddenly stopped working. The last time I had tried using the voice recorder application it worked fine. But, today I wanted to use it with skype and there were issues. I thought this might have to do with skype and I tried using it with voice recorder, without any success.[/COLOR]
[COLOR=#000000]I tried different solutions posted on the internet and due to my lack of knowledge I also screwed up some other things. So, whenever I reboot the system, I have to manually start pulseaudio -D. [/COLOR]
[COLOR=#000000]I also tried various options in gstreamer-properties, but in vain. 
I need help with microphone and autostarting pulseaudio in background.

Thank,
PK

[/COLOR]Following are the details of my system:

**uname -a**
```
Linux PK-LAPTOP-UBUNTU 3.5.0-49-generic #73~precise1-Ubuntu SMP Wed Apr 2 18:35:12 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

**lsb_release -a**
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

```

**lspci -v | grep -A7 -i "audio"**
```
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 09)
    Subsystem: Dell Device 05ea
    Flags: bus master, fast devsel, latency 0, IRQ 63
    Memory at c0810000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel


--
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
    Subsystem: Dell Device 05ea
    Flags: bus master, fast devsel, latency 0, IRQ 59
    Memory at c0814000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
```

[IMG]http://s29.postimg.org/adu17ueuf/sound1.png[/IMG]

[IMG]http://s29.postimg.org/4odsnj8o7/sound2.png[/IMG]

---

