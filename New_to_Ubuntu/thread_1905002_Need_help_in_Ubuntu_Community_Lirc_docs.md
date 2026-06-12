---
title: "Need help in Ubuntu Community Lirc docs"
date: 2012-01-05
forum: New to Ubuntu
---

### Post by hopelessone on 2012-01-05
Asus P7131 Hybrid TV Card some buttons not working so:


Recording a Remote
Insert the module that you intend to record from.

Example:

$ sudo modprobe lirc_mceusb2 **[COLOR="Red"]<-- How to find it???[/COLOR]**
Record the remote using irrecord

$ sudo irrecord -d /dev/lirc0 lircd.conf
Once you have completed your configuration, move this lircd.conf to /etc/lirc/lircd.conf

$ sudo mv lircd.conf /etc/lirc
Add the modules for the remote to /etc/lirc/hardware.conf under MODULES

Whats the command to find out what the name of the module the remote is using?

---

### Post by hopelessone on 2012-01-06
lsmod

---

### Post by hopelessone on 2012-01-06
How can i find a list of available modules i would like to load but dont know the names?

---

### Post by hopelessone on 2012-01-06
modprobe --list

sudo modprobe rc-asus-pc39

Is my remote control...now what? do i stop lirc? to see it?

> blade@oneiric:~$ lsmod
Module                  Size  Used by
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
binfmt_misc            17540  1 
tda1004x               27416  1 
saa7134_dvb            38572  0 
videobuf_dvb           14092  1 saa7134_dvb
dvb_core              109744  1 videobuf_dvb
saa7134_alsa           18456  1 
snd_hda_codec_via      71209  1 
tda827x                18114  2 
tda8290                22429  1 
ppdev                  17113  0 
tuner                  27336  1 
snd_usb_audio         118064  1 
uvcvideo               72284  0 
ir_lirc_codec          12859  0 
lirc_dev               19166  1 ir_lirc_codec
ir_mce_kbd_decoder     12723  0 
videobuf2_core         32760  1 uvcvideo
snd_usbmidi_lib        25371  1 snd_usb_audio
videobuf2_vmalloc      12928  1 uvcvideo
videobuf2_memops       13230  1 videobuf2_vmalloc
ir_sanyo_decoder       12513  0 
usbhid                 47198  0 
hid                    95463  1 usbhid
rc_asus_pc39           12508  0 
ir_sony_decoder        12510  0 
ir_jvc_decoder         12507  0 
ir_rc6_decoder         12507  0 
saa7134               181166  2 saa7134_dvb,saa7134_alsa
ir_rc5_decoder         12507  0 
ir_nec_decoder         12507  0 
rc_core                26333  11 ir_lirc_codec,ir_mce_kbd_decoder,ir_sanyo_decoder,rc_asus_pc39,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,saa7134,ir_rc5_decoder,ir_nec_decoder
videobuf_dma_sg        19262  3 saa7134_dvb,saa7134_alsa,saa7134
videobuf_core          26022  3 videobuf_dvb,saa7134,videobuf_dma_sg
v4l2_common            16454  2 tuner,saa7134
videodev              101939  4 tuner,uvcvideo,saa7134,v4l2_common
psmouse                73882  0 
serio_raw              13166  0 
media                  21344  2 uvcvideo,videodev
parport_pc             36962  1 
asus_atk0110           18078  0 
v4l2_compat_ioctl32    16780  1 videodev
tveeprom               21249  1 saa7134
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd_pcm                96714  4 saa7134_alsa,snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  20 saa7134_alsa,snd_hda_codec_via,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  566827  3 
drm_kms_helper         42558  1 i915
drm                   236290  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
sata_sil               13542  6 
r8169                  52788  0 
blade@oneiric:~$ 

Confused on how to  get this remote working?

Anyone?

---

### Post by hopelessone on 2012-01-06
> sudo modprobe rc-asus-pc39
sudo irrecord -d /dev/lirc0 lircd.conf

Nothing is recorded...Is there another way?

---

### Post by hopelessone on 2012-01-06
Ive got this showing up:
> I: Bus=0001 Vendor=1043 Product=4876 Version=0001
N: Name="saa7134 IR (ASUSTeK P7131 Hybri"
P: Phys=pci-0000:03:01.0/ir0
S: Sysfs=/devices/pci0000:00/0000:00:1e.0/0000:03:01.0/rc/rc0/input6
U: Uniq=
H: Handlers=kbd event6 
B: PROP=0
B: EV=100013
B: KEY=108c0322 210400000000000 0 10000 418000000801 9f16c000000000 10000ffc
B: MSC=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="MCE IR Keyboard/Mouse (saa7134)"
P: Phys=/input0
S: Sysfs=/devices/virtual/input/input7
U: Uniq=
H: Handlers=sysrq kbd mouse2 event7 
B: PROP=0
B: EV=100017
B: KEY=30000 7 ff87207ac14057ff febeffdfffefffff fffffffffffffffe
B: REL=3


Which is what?

---

