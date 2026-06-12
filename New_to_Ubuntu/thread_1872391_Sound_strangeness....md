---
title: "Sound strangeness..."
date: 2011-10-30
forum: New to Ubuntu
---

### Post by ouija1979 on 2011-10-30
OK, I don't think this is a problem with the emulator itself, but on starting my computer, GFCE ULTRA NES EMULATOR works fine, but if I open any other program and close it, then open the emulator again it sounds all garbled. If I use movie player or play music it sounds fine, just with this one program. I dont understand, all the other emulators run fine just this one with the sound problem. Is there anyway to clear the sound cache or something? I dunno I am a newb.

---

### Post by Silent Warrior on 2011-10-30
I think I know what you mean about the sound being garbled, but I don't have a solution for you. I suspect this is a problem with the emulator, but there are several elements on the way: ALSA drivers, kernel, PulseAudio, what sound API the emulator was compiled to use, possibly a plug-in... All I think you can do is just wait for an update for either of those components and hope that solves it. As I said, my money's on the emulator being at fault, somehow.

For everyone's benefit, though: What sound hardware are you using?
```
lspci | grep Audio
```
(If that doesn't seem conclusive, see the specs from your computer/motherboard/soundcard manufacturer, or run 'lsmod' and look for any submodules to an entry mentioning 'snd' (lsmod | grep snd ?).)

You can, of course, also go look for the source code of each and compile them yourself, but 'newbs' shouldn't do that unsupervised. :) (YES, I do too speak from experience! I've even compiled the kernel maybe 2-5 times over the years, resulting in all of one that actually worked, and one I compiled while trying out Gentoo which I forgot the name for and then failed to add it to any bootloader configuration. Fail.)

---

### Post by ouija1979 on 2011-10-31
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

There you go :)

Module                  Size  Used by
hidp                   22351  0 
vesafb                 13489  1 
bnep                   17923  2 
rfcomm                 38408  8 
tda1004x               22894  0 
saa7134_dvb            33358  0 
videobuf_dvb           13867  1 saa7134_dvb
dvb_core               94826  1 videobuf_dvb
saa7134_alsa           18172  1 
tuner_simple           18151  1 
tuner_types            18998  1 tuner_simple
tea5767                13113  0 
tda9887                17874  1 
tda8290                22216  0 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
snd_hda_codec_hdmi     31426  4 
tuner                  26836  2 
ppdev                  12849  0 
nvidia              10390874  40 
ir_sony_decoder        12493  0 
ir_jvc_decoder         12490  0 
joydev                 17393  0 
ir_rc6_decoder         12490  0 
usb_storage            44173  1 
btusb                  18160  2 
saa7134               153846  2 saa7134_dvb,saa7134_alsa
ir_rc5_decoder         12490  0 
uas                    17699  0 
ir_nec_decoder         12490  0 
snd_seq_midi           13132  0 
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,saa7134,ir_rc5_decoder,ir_nec_decoder
videobuf_dma_sg        18786  3 saa7134_dvb,saa7134_alsa,saa7134
psmouse                73673  0 
bluetooth             148839  24 hidp,bnep,rfcomm,btusb
videobuf_core          25409  3 videobuf_dvb,saa7134,videobuf_dma_sg
snd_hda_codec_cmedia    13719  1 
v4l2_common            15793  2 tuner,saa7134
videodev               85626  3 tuner,saa7134,v4l2_common
snd_rawmidi            25241  1 snd_seq_midi
serio_raw              12990  0 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_cmedia,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
tveeprom               17009  1 saa7134
snd_pcm                80468  4 saa7134_alsa,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
parport_pc             32114  1 
binfmt_misc            17292  1 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  16 saa7134_alsa,snd_hda_codec_hdmi,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  2 hidp,usbhid
firewire_ohci          35854  0 
via_rhine              27413  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
floppy                 60310  0

---

