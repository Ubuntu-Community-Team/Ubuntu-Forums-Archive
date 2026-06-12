---
title: "Complete linux newbie"
date: 2013-02-15
forum: New to Ubuntu
---

### Post by dannyd2134 on 2013-02-15
**Hi,

I have recently installed ubuntu 12.10, wifi works, i have graphics working but the driver isn't activated lol! :/

My main issue really is that i have no sound, which is quite frustrating. I installed from scratch and not through another os like windows or OSx.

My laptop is a hp g70-120ea, yes it has an nvidia graphics card but i really want my sound working. One weird thing i have to say is when my laptop reboots i get an nvidia splash screen. 

Also one last question, how do i check what things have drivers etc? 

thanks:mrgreen:

---

### Post by tgalati4 on 2013-02-15
Open a terminal and post the following:

```
aplay -l
lsmod
```

*aplay* with the "L" switch lists your sound hardware.  *lsmod* lists the modules (similar to drivers) you have currently loaded.

---

### Post by dannyd2134 on 2013-02-15
ok i have done that.

> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
dan-iel@dans-ubuntu:~$ lsmod
Module                  Size  Used by
bnep                   17708  2 
rfcomm                 37277  0 
bluetooth             183270  10 bnep,rfcomm
parport_pc             31969  0 
ppdev                  12818  0 
nvidia               8557169  51 
joydev                 17162  0 
arc4                   12474  2 
coretemp               13169  0 
snd_hda_codec_hdmi     31457  1 
snd_hda_codec_conexant    52203  1 
hp_wmi                 13617  0 
sparse_keymap          13659  1 hp_wmi
snd_hda_intel          32516  2 
snd_hda_codec         111548  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13273  1 snd_hda_codec
snd_pcm                80235  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
snd_rawmidi            25383  1 snd_seq_midi
ext2                   67205  1 
snd_seq_midi_event     14476  1 snd_seq_midi
mac_hid                13038  0 
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
snd_timer              24412  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    18591  1 hp_wmi
snd                    62146  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath5k                 135206  0 
ath                    19188  1 ath5k
mac80211              461203  1 ath5k
uvcvideo               71278  0 
psmouse                84878  0 
microcode              18210  0 
videobuf2_core         32071  1 uvcvideo
videodev               95842  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12757  1 uvcvideo
serio_raw              13032  0 
videobuf2_memops       13213  1 videobuf2_vmalloc
cfg80211              175574  3 ath5k,ath,mac80211
soundcore              14600  1 snd
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
lpc_ich                16926  0 
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
xts                    12750  4 
gf128mul               14504  1 xts
dm_crypt               22403  2 
r8169                  55977  0 
video                  18848  0 
ums_realtek            17670  0 
uas                    17557  0 
usb_storage            39351  1 ums_realte

Well i did as you said but then i went into the sound settings and digital out was selected](*,)

Also i am having this weird thing with my wifi, the colour changes from blue(on) to orange(off) but i don't lose any connection which is weird if you ask me lol!

---

### Post by grahammechanical on 2013-02-15
You must have video driver activated even if it is the default open source Nouveau driver. In 12.10 go to System Settings>Software Sources>Additional Drivers tab. There you will see a selection of video drivers and one of the will be activated.

The Nvidia splash ascreen at boot time is not connected to the video driver but down to some setting in BIOS. Those screens come up before the display server has activated.

Regards.

---

### Post by dannyd2134 on 2013-02-15
> **grahammechanical said:**
> You must have video driver activated even if it is the default open source Nouveau driver. In 12.10 go to System Settings>Software Sources>Additional Drivers tab. There you will see a selection of video drivers and one of the will be activated.

The Nvidia splash ascreen at boot time is not connected to the video driver but down to some setting in BIOS. Those screens come up before the display server has activated.

Regards.

Hi,

Well this is what i get when i go to additional drivers. 

When i actually go to additional drivers the app, I get the second picture. 

Any idea why my wifi button flickers between blue and orange? even though i am still connected. 

Wifi is atheros, not sure of which one.

---

