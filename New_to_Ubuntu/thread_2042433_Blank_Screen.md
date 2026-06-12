---
title: "Blank Screen"
date: 2012-08-14
forum: New to Ubuntu
---

### Post by DennisMesa on 2012-08-14
I have Ubuntu 12.04 64 bit installed on my desktop.I can boot up with no problem.
After a few minutes the screen goes blank for one or two seconds then back to normal. This happens the entire time I have my desktop running. I HAD Zorin 6 installed and had the same problem.I also tried Mint 13 with the same results. I thought switching OS's would fix the screen blanking but it did not. Any ideas?

---

### Post by sandyd on 2012-08-15
> **DennisMesa said:**
> I have Ubuntu 12.04 64 bit installed on my desktop.I can boot up with no problem.
After a few minutes the screen goes blank for one or two seconds then back to normal. This happens the entire time I have my desktop running. I HAD Zorin 6 installed and had the same problem.I also tried Mint 13 with the same results. I thought switching OS's would fix the screen blanking but it did not. Any ideas?
Go to the terminal (Unity Dash, type in "terminal"), and post the ouput of the following commands.

```

lspci | grep VGA
cat /etc/X11/xorg.conf
lsmod

```

---

### Post by DennisMesa on 2012-08-15
> **sandyd said:**
> Go to the terminal (Unity Dash, type in "terminal"), and post the ouput of the following commands.

```

lspci | grep VGA
cat /etc/X11/xorg.conf
lsmod

```
This is what I get:

dennis@Asus-Desktop ~ $ lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV610 video device [Radeon HD 2400 PRO]
dennis@Asus-Desktop ~ $ cat /etc/X11/xorg.conf

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

dennis@Asus-Desktop ~ $ lsmod
Module                  Size  Used by
fglrx                3263886  0 
snd_hda_codec_hdmi     32474  1 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
binfmt_misc            17540  1 
snd_hda_codec_realtek   223867  1 
ppdev                  17113  0 
snd_seq_midi           13324  0 
snd_hda_intel          33773  6 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_rawmidi            30748  1 snd_seq_midi
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
serio_raw              13211  0 
usblp                  18307  0 
snd_seq_midi_event     14899  1 snd_seq_midi
parport_pc             32866  1 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
radeon                804372  3 
snd                    78855  21 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
ttm                    76949  1 radeon
drm_kms_helper         46978  1 radeon
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
drm                   242038  5 radeon,ttm,drm_kms_helper
asus_atk0110           18078  0 
nv_tco                 13687  0 
i2c_nforce2            13058  0 
i2c_algo_bit           13423  1 radeon
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
usb_storage            49198  0 
crc_itu_t              12707  1 firewire_core
tulip                  57391  0 
sata_nv                32286  8 
floppy                 70365  0 
forcedeth              63460  0 
pata_amd               14118  0

Again, any help will be greatly appreciated.

---

### Post by sandyd on 2012-08-18
> **DennisMesa said:**
> This is what I get:

dennis@Asus-Desktop ~ $ lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV610 video device [Radeon HD 2400 PRO]
dennis@Asus-Desktop ~ $ cat /etc/X11/xorg.conf

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

dennis@Asus-Desktop ~ $ lsmod
Module                  Size  Used by
fglrx                3263886  0 
snd_hda_codec_hdmi     32474  1 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
binfmt_misc            17540  1 
snd_hda_codec_realtek   223867  1 
ppdev                  17113  0 
snd_seq_midi           13324  0 
snd_hda_intel          33773  6 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_rawmidi            30748  1 snd_seq_midi
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
serio_raw              13211  0 
usblp                  18307  0 
snd_seq_midi_event     14899  1 snd_seq_midi
parport_pc             32866  1 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
radeon                804372  3 
snd                    78855  21 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
ttm                    76949  1 radeon
drm_kms_helper         46978  1 radeon
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
drm                   242038  5 radeon,ttm,drm_kms_helper
asus_atk0110           18078  0 
nv_tco                 13687  0 
i2c_nforce2            13058  0 
i2c_algo_bit           13423  1 radeon
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
usb_storage            49198  0 
crc_itu_t              12707  1 firewire_core
tulip                  57391  0 
sata_nv                32286  8 
floppy                 70365  0 
forcedeth              63460  0 
pata_amd               14118  0

Again, any help will be greatly appreciated.
Sorry for the long wait - been busy

Everything looks fine from here, can you run
```

#install pastebinit
sudo apt-get -y install pastebinit
dmesg | pastebinit
```
after a blank, and post the output?

---

