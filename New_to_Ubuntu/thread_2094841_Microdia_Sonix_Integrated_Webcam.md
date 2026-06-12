---
title: "Microdia Sonix Integrated Webcam"
date: 2012-12-14
forum: New to Ubuntu
---

### Post by ArmyDad on 2012-12-14
Trying to get Skype running, and all I get is a message saying it can't find my webcam.

Running ubuntu 12.04.1 LTS on my laptop.

Ran lsusb, I got: 
Bus 001 Device 003: ID 0c45:6480 Microdia Sonix 1.3 MP Laptop Integrated Webcam

So I know it sees it, I guess I just need to the driver? Problem is, can't find one anywhere.

Anyone know of a universal for integrated webcams or a more direct solution? Thank you.

---

### Post by chadk5utc on 2012-12-14
there is an app built in called cheese have you tried it to see if it see's your cam?

---

### Post by ArmyDad on 2012-12-14
Cheese shows "No device found"

---

### Post by ArmyDad on 2012-12-14
I also tried using wxCam. Opening that app gave me 

"Error opening device

Cannot open /dev/video0.
Please check if your system has the correct driver for your webcam, or change the webcam device in settings->preferences."

An ls in /dev shows that video0 does not exist.

---

### Post by no2498 on 2012-12-15
if you have gstreamer installed
in a terminal type 

gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin

---

### Post by ArmyDad on 2012-12-15
v4l2 test shows: 
Video for Linux 2 (v4l2): Cannot identify device '/dev/video0'.

Which, as previously stated, does not exist in the dev/ directory.

There is no v4l1 on my list, only v4l2.

---

### Post by Rockstarever on 2012-12-15
well that helped me to. i just changed my video input device to usb 2.0 its strange but its gave me a test run.

---

### Post by ArmyDad on 2012-12-15
Mine is integrated. There isn't anything plugged into the USB.

My options for Default Input Plugin are Test Input, Video for Linux 2 (v4l2), and Custom.

Choosing Custom grays out the Device option and opens up the Pipeline input. It defaults to v4l2src. Testing Custom shows the same /dev/video0 device could not be found.

---

### Post by no2498 on 2012-12-15
in a terminal

lsmod

click enter

---

### Post by ArmyDad on 2012-12-15
Results from lsmod:


Module                  Size  Used by
joydev                 17393  0 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_realtek   174313  1 
binfmt_misc            17292  1 
bcma                   25651  0 
arc4                   12473  2 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
psmouse                86486  0 
snd_hwdep              13276  1 snd_hda_codec
dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
serio_raw              13027  0 
intel_ips              17822  0 
wmi                    18744  1 dell_wmi
brcmsmac              540875  0 
mac80211              436455  1 brcmsmac
i915                  419161  10 
mac_hid                13077  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
brcmutil               14675  1 brcmsmac
drm_kms_helper         45466  1 i915
drm                   197599  6 i915,drm_kms_helper
snd                    62064  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mei                    36570  0 
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
cfg80211              178679  2 brcmsmac,mac80211
crc8                   12781  1 brcmsmac
cordic                 12487  1 brcmsmac
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ums_realtek            17920  0 
uas                    17828  0 
usb_storage            39646  1 ums_realtek
atl1c                  36718  0

---

### Post by no2498 on 2012-12-15
odd mine comes up like this

lsmod
Module                  Size  Used by
isofs                  29250  0 
udf                    78785  0 
crc_itu_t               1371  1 udf
binfmt_misc             6587  1 
snd_via82xx            20058  2 
gameport                9089  1 snd_via82xx
snd_ac97_codec        100646  1 snd_via82xx
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          7076  2 snd_via82xx,snd_pcm
snd_mpu401_uart         5617  1 snd_via82xx
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  35102  71 
tileblit                2031  1 fbcon
snd                    54180  15 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
gspca_tv8532            4092  0 
gspca_main             21199  1 gspca_tv8532
psmouse                63245  0 
vga16fb                11385  1 
ppdev                   5259  0 
vgastate                8961  1 vga16fb
serio_raw               3978  0 
soundcore               6620  1 snd
videodev               34361  1 gspca_main
v4l1_compat            13251  1 videodev
i2c_viapro              5573  0 
parport_pc             25962  1 
via_agp                 5310  1 
agpgart                31724  1 via_agp
shpchp                 28820  0 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
8139too                18545  0 
8139cp                 16186  0 
mii                     4381  2 8139too,8139cp
pata_via                7272  0 
sata_via                7009  2 
floppy                 53016  0



videodev 34361 1 gspca_main
 v4l1_compat 13251 1 videodev

---

### Post by no2498 on 2012-12-15
ok lets try wxcam open it

click settings preferences
mine is set to mpeg video4linx2

video is set to xvid

---

### Post by no2498 on 2012-12-15
ok a few more things may be going on
if you have windows installed too
if you have had the cam program open in windows you may need to turn it off in msconfig
now if you turn it off in windows you need to reboot the computer
that will also close cheese and skipe on ubuntu
and if you have installed motion you need to turn it off in the terminal as it runs all the time till its turned off
as we can only run 1 cam program at a time

hope this helps

---

### Post by ArmyDad on 2012-12-15
wxCam can't find the device,  it isn't a video setting. It looks like it needs the drivers.

I do not have windows installed or any other programs using the webcam.

Does anyone know what driver goes to this webcam?

lsusb shows
Bus 001 Device 003: ID 0c45:6480 Microdia Sonix 1.3 MP Laptop Integrated Webcam

It is a Dell Inspiron n7010.

---

### Post by no2498 on 2012-12-15
the drivers for the cams are in the Cornell's
have you ask on the dell forms

it does not look like your going to have much fun
put this in google

ID 0c45:6480 Microdia Sonix 1.3 MP Laptop Integrated Webcam

---

### Post by mörgæs on 2012-12-16
Is there a particular reason that you are testing this in 12.04 and not in (a fresh install of) 12.10?

---

### Post by ArmyDad on 2012-12-16
It was just on a recommendation from a friend.

Is there a flavor that works better with laptops?

---

### Post by mörgæs on 2012-12-16
My favourite is Xubuntu 12.10, but any of the 12.10's are worth trying.

---

### Post by ArmyDad on 2012-12-19
I installed Kubuntu 12.10 and have had no issues so far.

Thanks for the tip to branch out.

---

