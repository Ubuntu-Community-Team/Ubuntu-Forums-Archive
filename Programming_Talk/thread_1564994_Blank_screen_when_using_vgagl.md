---
title: "Blank screen when using vgagl"
date: 2010-08-31
forum: Programming Talk
---

### Post by New00Folder on 2010-08-31
I'm learning to use gcc to compile simple C and C++ programs with 
 vga.h and vgagl.h. Programs using only vga.h are working out fine. But 
 whenever I use any vgagl function all I get is blank screen with 
 just.. 
 Using VESA driver, 65472KB. VBE3 
 svgalib 1.4.3 
 on the top. This happens even with the demo programs I got with the 
 svgalib package. The program probably hangs there and stays like that 
 until I press Ctrl+C either at the blank screen or at the terminal I 
 used to run the program. 
 Any help appreciated

---

### Post by Zugzwang on 2010-08-31
0. Try if the "glxgears" work by running them.

1. Try to switch off the desktop effects. They is known to cause trouble with OpenGL problems in Ubuntu. Search the forum for details.

2. If "1." does not fix the problem, after quitting your program, see if there occurred some kernel message stating problems. Use the "dmesg" command in the terminal for doing that.

---

### Post by New00Folder on 2010-09-01
Here's the output of glxgears:-
(while the gears were being displayed)
1798 frames in 5.0 seconds
1741 frames in 5.0 seconds
1706 frames in 5.0 seconds
(after ctrl+c)
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 18038 requests (18035 known processed) with 0 events remaining.

Disabling visual effects didn't help and I can't find anything about kernel message stating in dmesg output. Output (lower-most lines) is:
```

[ 1932.180365] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[ 1935.560117] hub 5-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[ 1935.560127] usb 5-1: USB disconnect, address 12
[ 1935.824091] usb 5-1: new low speed USB device using uhci_hcd and address 13
[ 1935.993260] usb 5-1: configuration #1 chosen from 1 choice
[ 1936.009685] input: USB+PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input19
[ 1936.009852] generic-usb 0003:04F3:0230.000A: input,hidraw0: USB HID v1.11 Mouse [USB+PS/2 Optical Mouse] on usb-0000:00:1d.0-1/input0
[ 1940.024359] hub 5-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[ 1940.024369] usb 5-1: USB disconnect, address 13
[ 1940.292102] usb 5-1: new low speed USB device using uhci_hcd and address 14
[ 1940.493261] usb 5-1: configuration #1 chosen from 1 choice
[ 1940.514678] input: USB+PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input20
[ 1940.514845] generic-usb 0003:04F3:0230.000B: input,hidraw0: USB HID v1.11 Mouse [USB+PS/2 Optical Mouse] on usb-0000:00:1d.0-1/input0
[ 1942.199015] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 1942.199346] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[ 1942.826687] CPU0 attaching NULL sched-domain.
[ 1942.826697] CPU1 attaching NULL sched-domain.
[ 1942.840638] CPU0 attaching sched-domain:
[ 1942.840644]  domain 0: span 0-1 level MC
[ 1942.840650]   groups: 0 1
[ 1942.840660] CPU1 attaching sched-domain:
[ 1942.840665]  domain 0: span 0-1 level MC
[ 1942.840670]   groups: 1 0
[ 1952.212582] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 1952.212928] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[ 1962.229357] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 1962.229689] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[ 1972.244091] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 1972.244429] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[ 1982.260834] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 1982.261053] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[ 1992.282339] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 1997.428087] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 1997.428414] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[ 2007.443421] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 2007.443743] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[ 2017.462504] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 2017.462833] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[ 2028.616624] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 2028.616965] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[ 2038.634855] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 2038.635196] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[ 2048.653471] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 2048.653816] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[ 2080.744031] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
[ 2108.620919] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 2208.621258] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 2308.620719] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 2408.620085] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 2508.621641] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 2608.620729] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 2708.621206] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 2808.620770] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 2880.168418] i2c-adapter i2c-2: unable to read EDID block.
[ 2880.168422] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[ 2880.173080] i2c-adapter i2c-2: unable to read EDID block.
[ 2880.173083] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[ 2880.308562] i2c-adapter i2c-2: unable to read EDID block.
[ 2880.308571] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[ 2880.313045] i2c-adapter i2c-2: unable to read EDID block.
[ 2880.313050] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[ 2881.644223] i2c-adapter i2c-2: unable to read EDID block.
[ 2881.644227] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[ 2881.648827] i2c-adapter i2c-2: unable to read EDID block.
[ 2881.648830] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[ 2881.796706] i2c-adapter i2c-2: unable to read EDID block.
[ 2881.796713] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[ 2881.801689] i2c-adapter i2c-2: unable to read EDID block.
[ 2881.801692] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[ 2908.620952] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 3008.620875] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 3108.621309] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 3208.621322] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 3308.619847] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 3408.620848] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 3508.620703] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 3608.620784] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 3708.620932] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 3734.988591] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 3734.988929] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[ 3808.633573] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 3848.624694] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 3908.627891] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 3988.627946] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 4088.626557] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 4208.627254] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 4304.056591] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x020c0000
[ 4328.624036] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86
[ 4448.629008] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 86

```

---

### Post by New00Folder on 2010-11-27
Anyone?

---

