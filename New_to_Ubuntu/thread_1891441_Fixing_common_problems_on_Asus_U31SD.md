---
title: "Fixing common problems on Asus U31SD"
date: 2011-12-05
forum: New to Ubuntu
---

### Post by Lalaith on 2011-12-05
Hi, 

I recenlty bought an Asus U31SD and installed Ubuntu 11.10 (dual boot with W7). I've got some issues wich I tried to solve, like (for other newbies' info):
- the low battery life, wich will supposedly be better with [Jupiter app]("http://www.webupd8.org/2010/06/jupiter-take-advantage-of-asus-super.html") , 
- can't disable the  touchpad with the Fn keys, and I'll try[ this]("http://shuffleos.com/2753/touchpad-indicator-enable-disable-touchpad-ubuntu-panel/") app

but most important for me, the laptop won't  suspend nor hibernate correctly. Is it safe to apply[ this]("https://help.ubuntu.com/community/AsusZenbook#Suspend") solution to the suspend issue on my laptop even if it's not the same model? If you&I need to check some terminal-text just let me know.

I also have a more philosophical question: I understand that since this Ubuntu release is pretty new, this "minor problems" will take some time to get officially fixed. Do you think that will someday appear a package to solve this problems? And if so, could it be that all my newbie-fixing patches give me more problems?

---

### Post by michael37 on 2011-12-05
> **Lalaith said:**
> Hi, 

I recenlty bought an Asus U31SD and installed Ubuntu 11.10 (dual boot with W7). I've got some issues wich I tried to solve, like (for other newbies' info):
- the low battery life, wich will supposedly be better with [Jupiter app]("http://www.webupd8.org/2010/06/jupiter-take-advantage-of-asus-super.html") , 
- can't disable the  touchpad with the Fn keys, and I'll try[ this]("http://shuffleos.com/2753/touchpad-indicator-enable-disable-touchpad-ubuntu-panel/") app

but most important for me, the laptop won't  suspend nor hibernate correctly. Is it safe to apply[ this]("https://help.ubuntu.com/community/AsusZenbook#Suspend") solution to the suspend issue on my laptop even if it's not the same model? If you&I need to check some terminal-text just let me know.

I also have a more philosophical question: I understand that since this Ubuntu release is pretty new, this "minor problems" will take some time to get officially fixed. Do you think that will someday appear a package to solve this problems? And if so, could it be that all my newbie-fixing patches give me more problems?

You haven't told us which graphics driver you use (intel, nouveau or binary nvidia), and it's very important since it's likely your graphics driver preventing you from resuming from suspend.

In any case, try [this guide]("http://ubuntuforums.org/showthread.php?t=1763742&page=2") to help you -- I would start by just applying the "fix suspending" part of the guide.

---

### Post by Lalaith on 2011-12-07
Thank you, it is pretty useful but I couldn't get it working. 

In order to use the script described on the post for "Fix Suspending", it says to install Ironhide but I couldn't, since there was an error during the installation (couldn't see "the gears", and it says: "[SIZE=2]Error: couldn't get an RGB, Double-buffered visual")[/SIZE] 

Surfing here and there, I've seen that it may be because of the drivers installed on my graphic card. My laptop uses an NVIDIA GEFORCE GT520M, and as far as I know, I haven't installed anything weird, only the deffault updates that my Ubuntu Software Center suggests... Oh, and I installed Jupiter and Jupiter-support-eee, wich may be also doing something on those kind of cards :s

Could I get any suggestions?


[SIZE=1]I've searched on the forums how to show the drivers, so here I post what does "lsmod" gives as result. If you&I need more info just let me know
[/SIZE][B][SIZE=1]Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
snd_hda_codec_realtek   330769  1 
arc4                   12529  2 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
asus_nb_wmi            12517  0 
asus_wmi               20035  1 asus_nb_wmi
sparse_keymap          13890  1 asus_wmi
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
mxm_wmi                12979  0 
snd_seq_midi_event     14899  1 snd_seq_midi
nvidia              11713772  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
psmouse                73882  0 
serio_raw              13166  0 
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
iwlagn                314213  0 
mac80211              462092  1 iwlagn
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              199587  2 iwlagn,mac80211
i915                  566711  2 
drm_kms_helper         42558  1 i915
wmi                    19256  2 asus_wmi,mxm_wmi
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   236330  3 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
soundcore              12680  1 snd
mei                    41480  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
atl1c                  41643  0 
ahci                   26002  2 
libahci                26861  1 ahci
[/SIZE]
[/B]

---

### Post by michael37 on 2011-12-07
> **Lalaith said:**
> Thank you, it is pretty useful but I couldn't get it working. 
...
[SIZE=1]I've searched on the forums how to show the drivers, so here I post what does "lsmod" gives as result. If you&I need more info just let me know
[/SIZE][B][SIZE=1]Module                  Size  Used by
nvidia              11713772  0 
[/B]

It is useful indeed. I have a few bad news for you.

You are using [restricted driver]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia"). There are a few suggestions on that page for suspending problems.

Nouveau open source driver doesn't work *yet* on your hardware. It is expected to work much better in the next version 12.04.

---

### Post by Lalaith on 2011-12-08
Thank you very much. 

I would finally like to know how did you see on this line that I've got propietary drivers:
[B]nvidia              11713772  0 

[/B]

---

### Post by michael37 on 2011-12-08
> **Lalaith said:**
> Thank you very much. 

I would finally like to know how did you see on this line that I've got propietary drivers:
[B]nvidia              11713772  0 

[/B]

The open source one is called "nouveau" and it's much smaller in size :-)

---

