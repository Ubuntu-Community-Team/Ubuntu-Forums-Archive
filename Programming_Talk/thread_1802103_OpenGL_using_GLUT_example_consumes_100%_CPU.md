---
title: "OpenGL using GLUT: example consumes 100% CPU"
date: 2011-07-11
forum: Programming Talk
---

### Post by anche on 2011-07-11
Hello guys!

I am interested in learning openGL using C++ so I've tried this:
[http://www.ferdychristant.com/blog/articles/DOMM-72MPPE](http://www.ferdychristant.com/blog/articles/DOMM-72MPPE)

I picked the GLUT example and it compiled and ran but it consumed 100% CPU according to the "top" util.

I wonder if this is due to the video driver I am using, or if this because I am generally stupid, or both :)

Here is the output of lspci:
```
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:10.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:11.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation C68 [GeForce 7050 PV / nForce 630a] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:06.0 Network controller: Atheros Communications Inc. AR922X Wireless Network Adapter (rev 01)
```Here is the output of lsmod (just in case):
```
Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  2 
aes_generic            38023  1 aes_i586
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17335  0 
fat                    55505  1 vfat
binfmt_misc            13213  1 
dm_crypt               22463  0 
vesafb                 13449  1 
arc4                   12473  2 
snd_hda_codec_hdmi     27479  1 
snd_hda_codec_via      56765  1 
snd_usb_audio          91410  1 
snd_usbmidi_lib        24388  1 snd_usb_audio
ath9k                 103633  0 
mac80211              257001  1 ath9k
ath9k_common           13611  1 ath9k
ath9k_hw              300328  2 ath9k,ath9k_common
ath                    19141  2 ath9k,ath9k_hw
snd_hda_intel          24140  4 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep              13274  2 snd_usb_audio,snd_hda_codec
snd_pcm                80244  4 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
nvidia               7098106  68 
ppdev                  12849  0 
snd_timer              28659  2 snd_pcm,snd_seq
cfg80211              156212  3 ath9k,mac80211,ath
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               66851  0 
videodev               75143  1 uvcvideo
snd                    55295  22 snd_hda_codec_hdmi,snd_hda_codec_via,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
asus_atk0110           17664  0 
i2c_nforce2            12906  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
parport_pc             32111  1 
k10temp                12951  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
dm_raid45              88410  0 
xor                    21860  1 dm_raid45
btrfs                 527341  0 
zlib_deflate           26594  1 btrfs
libcrc32c              12543  1 btrfs
usbhid                 41704  0 
usb_storage            43946  2 
hid                    77084  1 usbhid
uas                    17676  0 
floppy                 60032  0 
ahci                   21591  4 
pata_amd               13762  0 
forcedeth              58190  0 
libahci                25548  1 ahci
ramzswap               13202  0 
xvmalloc               13453  1 ramzswap
```

Does anybody have any ideas what the problem might be?

Thanks in advance,
Anatoly.

---

### Post by Simian Man on 2011-07-11
That example uses 100% CPU because it constantly renders over and over.  If you wanted it to not use 100% CPU, you'd have to do the drawing and updating less frequently (with calls to sleep), or only when some event has occurred.  Generally games do use nearly 100% CPU, so if that's what you're doing, I wouldn't sweat it.

It's definitely nothing wrong with your hardware :).

---

### Post by PaulM1985 on 2011-07-11
> **Simian Man said:**
> That example uses 100% CPU because it constantly renders over and over.  If you wanted it to not use 100% CPU, you'd have to do the drawing and updating less frequently (with calls to sleep), or only when some event has occurred.  Generally games do use nearly 100% CPU, so if that's what you're doing, I wouldn't sweat it.

It's definitely nothing wrong with your hardware :).

+1

In game programming you are hoping to have > 20fps, leaving you 50ms between frames for processing.  I imagine if you put in a sleep of 30ms, you wouldn't recognise any real lag (your rotates will be slower, but not jerky) and you will use less CPU.

Paul

---

