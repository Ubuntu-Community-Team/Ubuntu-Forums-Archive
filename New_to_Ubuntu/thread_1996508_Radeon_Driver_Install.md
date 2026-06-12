---
title: "Radeon Driver Install"
date: 2012-06-04
forum: New to Ubuntu
---

### Post by buugiewuugie on 2012-06-04
Hello, I am completely new to Ubuntu. I just installed it this morning. And the first thing I tried to do was set up my resolution. I couldn't set it to the resolution I wanted because I apparently don't have the correct driver. I have a Radeon Xpress 200. From what I read that is a supported card and I found [this link]("https://help.ubuntu.com/community/RadeonDriver"). But it's not showing me how to install the driver. I typed  lshw -C video  into the terminal and it's saying UNCLAIMED.

What do I do from here?

---

### Post by sandyd on 2012-06-04
> **buugiewuugie said:**
> Hello, I am completely new to Ubuntu. I just installed it this morning. And the first thing I tried to do was set up my resolution. I couldn't set it to the resolution I wanted because I apparently don't have the correct driver. I have a Radeon Xpress 200. From what I read that is a supported card and I found [this link]("https://help.ubuntu.com/community/RadeonDriver"). But it's not showing me how to install the driver. I typed  lshw -C video  into the terminal and it's saying UNCLAIMED.

What do I do from here?

Post output of
```

lsmod
```

---

### Post by buugiewuugie on 2012-06-04
Thank you for your help. Here is what you asked for.

```
Module                  Size  Used by
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
lp                     17799  0 
snd_hda_codec_realtek   223867  1 
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
ppdev                  17113  0 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
radeon                804372  3 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
ttm                    76949  1 radeon
drm_kms_helper         46978  1 radeon
drm                   242038  5 radeon,ttm,drm_kms_helper
psmouse                87603  0 
wmi                    19256  1 hp_wmi
i2c_algo_bit           13423  1 radeon
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k8temp                 13057  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
serio_raw              13211  0 
edac_core              53746  0 
edac_mce_amd           23709  0 
sp5100_tco             13791  0 
i2c_piix4              13301  0 
parport_pc             32866  1 
parport                46562  3 lp,ppdev,parport_pc
mac_hid                13253  0 
shpchp                 37277  0 
usbhid                 47199  0 
hid                    99559  1 usbhid
pata_atiixp            13204  0 
floppy                 70365  0 
tg3                   152032  0 
usb_storage            49198  0 

```

---

### Post by ajgreeny on 2012-06-04
The radeon driver seems to be the one you already have.  There is no restricted driver for that card any more, so I think you are using the correct one.

What resolution do you want and what have you got so far?

---

### Post by inashdeen on 2012-06-04
AFAIK, I am using Radeon card and the open source driver works perfectly, I agree with ajgreeny, what resolution you would like to achieve?

---

### Post by buugiewuugie on 2012-06-04
I apologize. I am using a dual display. I turned off the second monitor and I was able to choose the res I wanted. It looks like while using dual display in 3d mode my card can not handle the res I want.

My Error
```
Requested size (2304, 1024) exceeds 3D hardware limit (2048, 2048).
You must either rearrange the displays so that they fit within a (2048, 2048) square
or select the Ubuntu 2D session at login.
```

---

### Post by sandyd on 2012-06-04
> **buugiewuugie said:**
> I apologize. I am using a dual display. I turned off the second monitor and I was able to choose the res I wanted. It looks like while using dual display in 3d mode my card can not handle the res I want.

My Error
```
Requested size (2304, 1024) exceeds 3D hardware limit (2048, 2048).
You must either rearrange the displays so that they fit within a (2048, 2048) square
or select the Ubuntu 2D session at login.
```

Xinerama, you must use, if you want dual monitors

---

### Post by Mark Phelps on 2012-06-04
Your card is NOT supported for the current AMD restricted drivers because it was relegated to "legacy" status by (then) ATI years ago.

The open-source radeon driver, which is automatically installed by Ubuntu, is the only driver available today that will work with recent versions of Ubuntu.

---

### Post by buugiewuugie on 2012-06-04
Good to know!

Thank you everyone for you help. And I'll check out xinerama.

---

