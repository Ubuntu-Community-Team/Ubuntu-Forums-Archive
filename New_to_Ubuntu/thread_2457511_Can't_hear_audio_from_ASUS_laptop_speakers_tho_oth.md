---
title: "Can't hear audio from ASUS laptop speakers tho other outputs work"
date: 2021-02-03
forum: New to Ubuntu
---

### Post by tinofbeans on 2021-02-03
Hello all,

Like it says ... I'm getting no audio output from my laptop's speakers. Sound worked fine in the live boot from USB and works in Windows, but with Ubuntu installed I get nothing from the speakers. Headphones work just fine. I've actually had this issue across a few distros now. (Linux Mint, Manjaro, and Ubuntu) I've been looking around the forums at similar issues but the solutions haven't helped so far.

I've opened alsamixer and ensured that I don't have my speakers or master volume muted. Tried pavucontrol as well to no avail. If I have audio playing, the system seems to act as if it's generating sound - but nothing actually comes out of the speakers. So it knows there are speakers and it thinks it's putting out sound, but ...? Huh?

I've tried purging and then reinstalling pulseaudio and alsa, to no avail. :confused: 

Here's my inxi output for system details:

```
[FONT=monospace][COLOR=#5454ff]**System:    Kernel:**[/COLOR][COLOR=#000000] 5.8.0-41-generic x86_64 [/COLOR][COLOR=#5454ff]**bits:**[/COLOR][COLOR=#000000] 64 [/COLOR][COLOR=#5454ff]**Desktop:**[/COLOR][COLOR=#000000] KDE Plasma 5.19.5 [/COLOR][COLOR=#5454ff]**Distro:**[/COLOR][COLOR=#000000] Ubuntu 20.10 (Groovy Gorilla)  [/COLOR]
[COLOR=#5454ff]**Machine:   Type:**[/COLOR][COLOR=#000000] Laptop [/COLOR][COLOR=#5454ff]**System:**[/COLOR][COLOR=#000000] ASUSTeK [/COLOR][COLOR=#5454ff]**product:**[/COLOR][COLOR=#000000] ROG Strix G732LWS_G732LWS [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] 1.0 [/COLOR][COLOR=#5454ff]**serial:**[/COLOR][COLOR=#000000] <filter>  [/COLOR]
           [COLOR=#5454ff]**Mobo:**[/COLOR][COLOR=#000000] ASUSTeK [/COLOR][COLOR=#5454ff]**model:**[/COLOR][COLOR=#000000] G732LWS [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] 1.0 [/COLOR][COLOR=#5454ff]**serial:**[/COLOR][COLOR=#000000] <filter> [/COLOR][COLOR=#5454ff]**UEFI:**[/COLOR][COLOR=#000000] American Megatrends [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] G732LWS.310 [/COLOR][COLOR=#5454ff]**date:**[/COLOR][COLOR=#000000] 07/14/2020  [/COLOR]
[COLOR=#5454ff]**Battery:   ID-1:**[/COLOR][COLOR=#000000] BAT0 [/COLOR][COLOR=#5454ff]**charge:**[/COLOR][COLOR=#000000] 62.6 Wh [/COLOR][COLOR=#5454ff]**condition:**[/COLOR][COLOR=#000000] 63.9/66.0 Wh (97%)  [/COLOR]
[COLOR=#5454ff]**CPU:       Info:**[/COLOR][COLOR=#000000] 8-Core [/COLOR][COLOR=#5454ff]**model:**[/COLOR][COLOR=#000000] Intel Core i7-10875H [/COLOR][COLOR=#5454ff]**bits:**[/COLOR][COLOR=#000000] 64 [/COLOR][COLOR=#5454ff]**type:**[/COLOR][COLOR=#000000] MT MCP [/COLOR][COLOR=#5454ff]**L2 cache:**[/COLOR][COLOR=#000000] 16.0 MiB  [/COLOR]
           [COLOR=#5454ff]**Speed:**[/COLOR][COLOR=#000000] 800 MHz [/COLOR][COLOR=#5454ff]**min/max:**[/COLOR][COLOR=#000000] 800/5100 MHz [/COLOR][COLOR=#5454ff]**Core speeds (MHz):**[/COLOR][COLOR=#5454ff]**1:**[/COLOR][COLOR=#000000] 800 [/COLOR][COLOR=#5454ff]**2:**[/COLOR][COLOR=#000000] 800 [/COLOR][COLOR=#5454ff]**3:**[/COLOR][COLOR=#000000] 800 [/COLOR][COLOR=#5454ff]**4:**[/COLOR][COLOR=#000000] 800 [/COLOR][COLOR=#5454ff]**5:**[/COLOR][COLOR=#000000] 800 [/COLOR][COLOR=#5454ff]**6:**[/COLOR][COLOR=#000000] 800 [/COLOR][COLOR=#5454ff]**7:**[/COLOR][COLOR=#000000] 800 [/COLOR][COLOR=#5454ff]**8:**[/COLOR][COLOR=#000000] 800  [/COLOR]
           [COLOR=#5454ff]**9:**[/COLOR][COLOR=#000000] 800 [/COLOR][COLOR=#5454ff]**10:**[/COLOR][COLOR=#000000] 800 [/COLOR][COLOR=#5454ff]**11:**[/COLOR][COLOR=#000000] 800 [/COLOR][COLOR=#5454ff]**12:**[/COLOR][COLOR=#000000] 800 [/COLOR][COLOR=#5454ff]**13:**[/COLOR][COLOR=#000000] 800 [/COLOR][COLOR=#5454ff]**14:**[/COLOR][COLOR=#000000] 800 [/COLOR][COLOR=#5454ff]**15:**[/COLOR][COLOR=#000000] 800 [/COLOR][COLOR=#5454ff]**16:**[/COLOR][COLOR=#000000] 800  [/COLOR]
[COLOR=#5454ff]**Graphics:  Device-1:**[/COLOR][COLOR=#000000] Intel UHD Graphics [/COLOR][COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] i915 [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] kernel  [/COLOR]
           [COLOR=#5454ff]**Device-2:**[/COLOR][COLOR=#000000] NVIDIA TU104M [GeForce RTX 2070 SUPER Mobile / Max-Q] [/COLOR][COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] nouveau [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] kernel  [/COLOR]
           [COLOR=#5454ff]**Display:**[/COLOR][COLOR=#000000] x11 [/COLOR][COLOR=#5454ff]**server:**[/COLOR][COLOR=#000000] X.Org 1.20.9 [/COLOR][COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] modesetting [/COLOR][COLOR=#5454ff]**unloaded:**[/COLOR][COLOR=#000000] fbdev,vesa [/COLOR][COLOR=#5454ff]**resolution:**[/COLOR][COLOR=#000000] 1920x1080~60Hz  [/COLOR]
           [COLOR=#5454ff]**OpenGL:**[/COLOR][COLOR=#5454ff]**renderer:**[/COLOR][COLOR=#000000] Mesa Intel UHD Graphics (CML GT2) [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] 4.6 Mesa 20.2.6  [/COLOR]
[COLOR=#5454ff]**Audio:     Device-1:**[/COLOR][COLOR=#000000] Intel Comet Lake PCH cAVS [/COLOR][COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] snd_hda_intel  [/COLOR]
           [COLOR=#5454ff]**Device-2:**[/COLOR][COLOR=#000000] NVIDIA TU104 HD Audio [/COLOR][COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] snd_hda_intel  [/COLOR]
           [COLOR=#5454ff]**Sound Server:**[/COLOR][COLOR=#000000] ALSA [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] k5.8.0-41-generic  [/COLOR]
[COLOR=#5454ff]**Network:   Device-1:**[/COLOR][COLOR=#000000] Intel Wi-Fi 6 AX201 [/COLOR][COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] iwlwifi  [/COLOR]
           [COLOR=#5454ff]**IF:**[/COLOR][COLOR=#000000] wlo1 [/COLOR][COLOR=#5454ff]**state:**[/COLOR][COLOR=#000000] up [/COLOR][COLOR=#5454ff]**mac:**[/COLOR][COLOR=#000000] <filter>  [/COLOR]
           [COLOR=#5454ff]**Device-2:**[/COLOR][COLOR=#000000] Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet [/COLOR][COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] r8169  [/COLOR]
           [COLOR=#5454ff]**IF:**[/COLOR][COLOR=#000000] eno2 [/COLOR][COLOR=#5454ff]**state:**[/COLOR][COLOR=#000000] down [/COLOR][COLOR=#5454ff]**mac:**[/COLOR][COLOR=#000000] <filter>  [/COLOR]
[COLOR=#5454ff]**Drives:    Local Storage:**[/COLOR][COLOR=#5454ff]**total:**[/COLOR][COLOR=#000000] 953.87 GiB [/COLOR][COLOR=#5454ff]**used:**[/COLOR][COLOR=#000000] 12.82 GiB (1.3%)  [/COLOR]
           [COLOR=#5454ff]**ID-1:**[/COLOR][COLOR=#000000] /dev/nvme0n1 [/COLOR][COLOR=#5454ff]**vendor:**[/COLOR][COLOR=#000000] Intel [/COLOR][COLOR=#5454ff]**model:**[/COLOR][COLOR=#000000] SSDPEKNW010T8 [/COLOR][COLOR=#5454ff]**size:**[/COLOR][COLOR=#000000] 953.87 GiB  [/COLOR]
[COLOR=#5454ff]**Partition: ID-1:**[/COLOR][COLOR=#000000] / [/COLOR][COLOR=#5454ff]**size:**[/COLOR][COLOR=#000000] 649.03 GiB [/COLOR][COLOR=#5454ff]**used:**[/COLOR][COLOR=#000000] 12.79 GiB (2.0%) [/COLOR][COLOR=#5454ff]**fs:**[/COLOR][COLOR=#000000] ext4 [/COLOR][COLOR=#5454ff]**dev:**[/COLOR][COLOR=#000000] /dev/nvme0n1p6  [/COLOR]
[COLOR=#5454ff]**Swap:      ID-1:**[/COLOR][COLOR=#000000] swap-1 [/COLOR][COLOR=#5454ff]**type:**[/COLOR][COLOR=#000000] file [/COLOR][COLOR=#5454ff]**size:**[/COLOR][COLOR=#000000] 2.00 GiB [/COLOR][COLOR=#5454ff]**used:**[/COLOR][COLOR=#000000] 0 KiB (0.0%) [/COLOR][COLOR=#5454ff]**file:**[/COLOR][COLOR=#000000] /swapfile  [/COLOR]
[COLOR=#5454ff]**Sensors:   System Temperatures:**[/COLOR][COLOR=#5454ff]**cpu:**[/COLOR][COLOR=#000000] 31.0 C [/COLOR][COLOR=#5454ff]**mobo:**[/COLOR][COLOR=#000000] N/A [/COLOR][COLOR=#5454ff]**gpu:**[/COLOR][COLOR=#000000] nouveau [/COLOR][COLOR=#5454ff]**temp:**[/COLOR][COLOR=#000000] 25.0 C  [/COLOR]
           [COLOR=#5454ff]**Fan Speeds (RPM):**[/COLOR][COLOR=#5454ff]**cpu:**[/COLOR][COLOR=#000000] 2600 [/COLOR][COLOR=#5454ff]**gpu:**[/COLOR][COLOR=#000000] nouveau [/COLOR][COLOR=#5454ff]**fan:**[/COLOR][COLOR=#000000] 0  [/COLOR]
[COLOR=#5454ff]**Info:      Processes:**[/COLOR][COLOR=#000000] 363 [/COLOR][COLOR=#5454ff]**Uptime:**[/COLOR][COLOR=#000000] 33m [/COLOR][COLOR=#5454ff]**Memory:**[/COLOR][COLOR=#000000] 15.42 GiB [/COLOR][COLOR=#5454ff]**used:**[/COLOR][COLOR=#000000] 2.47 GiB (16.0%) [/COLOR][COLOR=#5454ff]**Shell:**[/COLOR][COLOR=#000000] Bash [/COLOR][COLOR=#5454ff]**inxi:**[/COLOR][COLOR=#000000] 3.1.07 [/COLOR]
[/FONT]
```

I'm also attaching a couple screenshots of pavucontrol and alsamixer in case those help:
[ATTACH=CONFIG]287899[/ATTACH]
[ATTACH=CONFIG]287900[/ATTACH]

Let me know if there's other info I should provide. Thanks in advance for any assistance!

---

