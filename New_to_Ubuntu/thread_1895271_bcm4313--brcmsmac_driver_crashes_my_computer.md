---
title: "bcm4313--brcmsmac driver crashes my computer"
date: 2011-12-14
forum: New to Ubuntu
---

### Post by Goat Engine on 2011-12-14
Hello, I am currently using Ubuntu 11.10.
The broadcom-sta driver in the additional drivers manager is disabled. My wireless driver is brmsmac.
Whenever I try to use my wireless network, my computer crashes. If it's on a wired connection it's fine. 

Information that might be important:

> 07:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
    Subsystem: Broadcom Corporation Device 0510
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f0100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: brcmsmac
    Kernel modules: bcma, brcmsmac

> probe@System01:~$ lsmod
Module                  Size  Used by
joydev                 17393  0 
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
bcma                   19571  0 
arc4                   12473  2 
sparse_keymap          13658  0 
snd_hda_codec_conexant    52418  1 
snd_hda_codec_hdmi     31426  1 
snd_hda_intel          28358  2 
snd_hda_codec          91754  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
uvcvideo               67271  0 
snd_seq_midi_event     14475  1 snd_seq_midi
videodev               85626  1 uvcvideo
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
brcmsmac              591864  0 
brcmutil               16885  1 brcmsmac
mac80211              393459  1 brcmsmac
psmouse                63474  0 
serio_raw              12990  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              172392  2 brcmsmac,mac80211
k10temp                12990  0 
snd                    55902  14 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
crc_ccitt              12595  1 brcmsmac
sp5100_tco             13495  0 
i2c_piix4              13093  0 
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
binfmt_misc            17292  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
radeon                961834  3 
ums_realtek            13096  0 
usb_storage            44173  1 ums_realtek
ttm                    65224  1 radeon
drm_kms_helper         32889  1 radeon
uas                    17699  0 
drm                   196290  5 radeon,ttm,drm_kms_helper
atl1c                  36638  0 
ahci                   21634  2 
i2c_algo_bit           13199  1 radeon
libahci                25761  1 ahci
vesafb                 13489  0 
wmi                    18744  0 
video                  18908  0 
I find this strange as I have seen solutions to similar problems online and they say brmsmac works. Maybe something other than the driver is causing the crash? It's definitely something to do with my wireless connection...

---

