---
title: "Speaker Not Working"
date: 2016-07-30
forum: New to Ubuntu
---

### Post by pzaf on 2016-07-30
Hello. Just finished downloading and installing the latest ubuntu a week ago. Everything seems to work fine except for the speaker.

My speaker is working perfectly fine when booting to windows 7. I googled for fixes but all I found does not seem to work.

Can you help me? Thank you!

---

### Post by QIII on 2016-07-30
Hello!

What do you mean by "the latest Ubuntu"?

Which release are you using?

---

### Post by pzaf on 2016-07-30
16.04, according to the file I downloaded.

ubuntu-16.04-desktop-amd64.iso

---

### Post by smelheim85 on 2016-07-30
I would go through the basic checks for sound settings.  Check to make sure that the sound settings inside your system menu are not muted.  Also if you don't mind performing this code;


```
 lspci -v | grep -A7 -i "audio" 
```

someone here is bound to have the same trouble.  I haven't played with 16.04 but I've had trouble with this in previous Ubuntu before and sometimes it was a driver issue other times it was a settings issue.

---

### Post by pzaf on 2016-07-30
Here's what appeared in the terminal

```
paolo@paolo-PC:~$ lspci -v | grep -A7 -i "audio"
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
    Subsystem: Gigabyte Technology Co., Ltd FCH Azalia Controller
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at fe200000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

--
01:00.1 Audio device: NVIDIA Corporation GF108 High Definition Audio Controller (rev a1)
    Subsystem: NVIDIA Corporation GF108 High Definition Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at fe080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
paolo@paolo-PC:~$ 
```

---

### Post by smelheim85 on 2016-07-31
OK that looks good I don't see any problems with your audio drivers from what I'm seeing.  Have you had the time to check the sound setting in your desktop environment settings?  Depending on which desktop you chose and it's usually GNOME but I would check there to make sure it's not muted and the speakers aren't selected.  This sounds more like it's not turned on from the settings.

---

