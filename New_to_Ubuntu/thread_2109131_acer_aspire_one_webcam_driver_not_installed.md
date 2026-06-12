---
title: "acer aspire one webcam driver not installed"
date: 2013-01-26
forum: New to Ubuntu
---

### Post by mcool on 2013-01-26
hello a great friend of mine has an acer aspire one d150 with intégrated crystal eye webcam i have read many forums but we just can't get the webcam to work 

she is using lubuntu 12.04

here is what lsmod ouputs

-thanks for your interest

Module                  Size  Used by
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
joydev                 17393  0 
snd_hda_codec_realtek   174313  1 
snd_hda_intel          32765  1 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
arc4                   12473  2 
snd_rawmidi            25424  1 snd_seq_midi
i915                  419326  2 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
psmouse                96718  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ath5k                 145127  0 
ath                    19387  1 ath5k
snd                    62218  11 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13027  0 
mac80211              436493  1 ath5k
drm_kms_helper         45466  1 i915
drm                   197641  3 i915,drm_kms_helper
cfg80211              178877  3 ath5k,ath,mac80211
soundcore              14635  1 snd
i2c_algo_bit           13199  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
acer_wmi               23612  0 
sparse_keymap          13658  1 acer_wmi
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  0 
bluetooth             158479  10 rfcomm,bnep
ppdev                  12849  0 
mac_hid                13077  0 
wmi                    18744  1 acer_wmi
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
atl1e                  32872  0 
usbhid                 41937  0 
hid                    77428  1 usbhid

---

### Post by linuxsyst on 2013-01-26
Type ```
lsusb
``` what does it return?

---

### Post by mcool on 2013-01-26
> Type
Code:
lsusb
what does it return?



```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04f3:0230 Elan Microelectronics Corp. 3D Optical Mouse
```

---

### Post by frank604 on 2013-01-26
Can you give us the output for 
```
 dmesg | grep "video"
```also
```
lsmod | grep "video"
```Oops, didn't read carefully, you already posted lsmod output, please disregard my 2nd code.  But do show us your dmesg.

Also, this appears to boil down to 2 reasons for failure:
1) the hardware died (many reports for this particular device in the acer aspire one of dying)
2) uvcvideo module error in loading in webcam

To test if it is a uvcvideo module error type in these codes
Unload the module: ```
sudo rmmod uvcvideo
```Reload the module: ```
sudo modprobe uvcvideo
```Then restart your web cam app and see if it detects.

---

### Post by mcool on 2013-01-26
> **frank604 said:**
> Can you give us the output for 
```
 dmesg | grep "video"
```also
```
lsmod | grep "video"
```Oops, didn't read carefully, you already posted lsmod output, please disregard my 2nd code.  But do show us your dmesg.

Also, this appears to boil down to 2 reasons for failure:
1) the hardware died (many reports for this particular device in the acer aspire one of dying)
2) uvcvideo module error in loading in webcam

To test if it is a uvcvideo module error type in these codes
Unload the module: ```
sudo rmmod uvcvideo
```Reload the module: ```
sudo modprobe uvcvideo
```Then restart your web cam app and see if it detects.
here is the output for  dmesg | grep "video"

:~$ dmesg | grep "video"
[    0.698128] pci 0000:00:02.0: Boot video device
[   11.272299] acer_wmi: Brightness must be controlled by generic video driver

---

### Post by mcool on 2013-01-26
sudo rmmod uvcvideo
gives me  
ERROR: Module uvcvideo does not exist in /proc/modules

---

### Post by mcool on 2013-01-26
tried 
sudo modprobe uvcvideo
it outputs nothing et when i relaunched guvcview to test the camera it outputs ; cannot find harware(or something like that) as a result

---

### Post by frank604 on 2013-01-26
I'm not sure there is a toggle to enable or disable the webcam in bios.  Can you boot the bios and check carefully for this toggle (if it exists)?

The reason why I say so is that the hardware doesn't seem to be detected at all.  lsusb should indicate your webcam.

like this:
Bus 002 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam

So the focus of this thread should be, "acer crystal eye webcam not recognized" 

According to [https://help.ubuntu.com/community/AspireOne/D150](https://help.ubuntu.com/community/AspireOne/D150) it should be working out of the box.  Perhaps make a liveusb of ubuntu 12.04 and boot it on the aspire one d150.  Test out webcam on cheese.  See how that goes?

---

### Post by mcool on 2013-01-26
> **frank604 said:**
> I'm not sure there is a toggle to enable or disable the webcam in bios.  Can you boot the bios and check carefully for this toggle (if it exists)?

The reason why I say so is that the hardware doesn't seem to be detected at all.  lsusb should indicate your webcam.

like this:
Bus 002 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam

So the focus of this thread should be, "acer crystal eye webcam not recognized" 

According to [https://help.ubuntu.com/community/AspireOne/D150](https://help.ubuntu.com/community/AspireOne/D150) it should be working out of the box.  Perhaps make a liveusb of ubuntu 12.04 and boot it on the aspire one d150.  Test out webcam on cheese.  See how that goes?
i have looked in the bios twice allready and nothing apears as for webcam toggle 

i think that the webcam should be reconize by native ucv drivers (out of the box) ... acording to this site
[http://www.ideasonboard.org/uvc/](http://www.ideasonboard.org/uvc/)

is it possible to change tread title

i never encountered a problem in lubuntu with webcam but i tought of trying ubuntu for this issue

thanks

---

### Post by frank604 on 2013-01-26
try to see if the liveusb of ubuntu 12.04 detects the webcam.  if it doesn't then perhaps the webcam is fried.  i'm not too knowledgeable about this product but there seems to be a lot of issues regarding this in both windows and linux.

If others have the webcam working OOB and yours doesn't on a clean environment (aka live usb of ubuntu), then perhaps a different approach needs to be done.  Keep us posted on what goes on after you try the live usb.

---

### Post by mcool on 2013-01-28
> **frank604 said:**
> try to see if the liveusb of ubuntu 12.04 detects the webcam.  if it doesn't then perhaps the webcam is fried.  i'm not too knowledgeable about this product but there seems to be a lot of issues regarding this in both windows and linux.

If others have the webcam working OOB and yours doesn't on a clean environment (aka live usb of ubuntu), then perhaps a different approach needs to be done.  Keep us posted on what goes on after you try the live usb.
unbuntu live usb didn't get the camera to work . 
i will try a few other test to know if it is the hardware or the sofware . i will update this post and thanks to you all !!!

---

### Post by mcool on 2013-02-08
finaly the device is probably fried ... tried with windows and manifacture drivers no webcam device was found thanks for everything anyway

---

