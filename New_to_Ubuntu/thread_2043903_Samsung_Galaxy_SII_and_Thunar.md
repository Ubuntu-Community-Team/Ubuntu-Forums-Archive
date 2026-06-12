---
title: "Samsung Galaxy SII and Thunar"
date: 2012-08-17
forum: New to Ubuntu
---

### Post by mtguy on 2012-08-17
I use Xubuntu 12.04.  I have searched the forum for answers regarding the Samsung Galaxy SII Android phone not being detected in Ubuntu and have applied every suggested solution that I thought might work.  The problem for me isn't Ubuntu, as I have the same OS on my desktop and using nautilus I can see my phone.  But on my laptop, I don't have nautilus installed and would prefer not to install it along with all the accompanying required files.

However, my phone doesn't show up in Thunar.  I'm not a complete novice, but not particularly proficient in Linux, either, but I cannot figure out how to make the phone show up in Thunar.  Any help?

---

### Post by spjackson on 2012-08-17
Are you connecting via USB? I have 32-bit Xubuntu 12.04 on my netbook. I don't have a S II but Thunar works just fine with the Galaxy S and an HTC Wildfire S connected via a USB cable.  Do you see anything in /var/log/syslog when you connect the phone?

---

### Post by mtguy on 2012-08-19
> **spjackson said:**
> Are you connecting via USB? I have 32-bit Xubuntu 12.04 on my netbook. I don't have a S II but Thunar works just fine with the Galaxy S and an HTC Wildfire S connected via a USB cable.  Do you see anything in /var/log/syslog when you connect the phone?

Sorry, just saw this.  Yes, I'm connecting via USB cable, and as I said, on my desktop, the phone shows up in nautilus, but not in thunar on either the desktop or laptop.  /var/log/syslog relative code below:
```
Aug 19 10:43:21 Xubuntu-lap kernel: [   65.680073] usb 2-1: new high-speed USB device number 3 using ehci_hcd
Aug 19 10:43:21 Xubuntu-lap kernel: [   65.812763] hub 2-1:1.0: USB hub found
Aug 19 10:43:21 Xubuntu-lap kernel: [   65.812846] hub 2-1:1.0: 2 ports detected
Aug 19 10:43:22 Xubuntu-lap kernel: [   66.084235] usb 2-1.2: new high-speed USB device number 4 using ehci_hcd
```

---

### Post by spjackson on 2012-08-19
The kernel sees the usb device but does not seem to recognise it as a mass storage device. Installing nautilus won't fix this.

When you connect the phone, make sure that you choose the mass storage device option on your phone.

With your phone attached, run
```

lsusb
lsmod

```on both the computer where it works and the one where it doesn't. Compare the two outputs (or post them here).

Maybe the relevant kernel module isn't installed on Xubuntu. However, I'd have expected that it would be.

---

### Post by mtguy on 2012-08-19
> **spjackson said:**
> 
When you connect the phone, make sure that you choose the mass storage device option on your phone.

I have ICS, and there is no option for "mass storage device" as there was in gingerbread.  Only options for USB device are media device (mtp) and camera (ptp).  I've tried both to no avail, and I have the relevant mtp tools and libs installed on both.
> With your phone attached, run
```

lsusb
lsmod

```on both the computer where it works and the one where it doesn't. Compare the two outputs (or post them here).

Maybe the relevant kernel module isn't installed on Xubuntu. However, I'd have expected that it would be.Laptop:
```
~:lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 192f:0416 Avago Technologies, Pte. 
Bus 002 Device 003: ID 0424:3803 Standard Microsystems Corp. 
Bus 002 Device 004: ID 04e8:6860 Samsung Electronics Co., Ltd GT-I9100 Phone [Galaxy S II]

``````
~:lsmod
Module                  Size  Used by
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
parport_pc             32866  0 
ppdev                  17113  0 
joydev                 17693  0 
snd_hda_codec_idt      70795  1 
snd_hda_intel          33773  4 
snd_hda_codec         127706  2 snd_hda_codec_idt,snd_hda_intel
lib80211_crypt_tkip    17390  0 
wl                   2568210  0 
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
psmouse                87692  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
dell_laptop            18119  0 
serio_raw              13211  0 
dcdbas                 14490  1 dell_laptop
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  17 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
lib80211               14381  2 lib80211_crypt_tkip,wl
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
sky2                   59043  0 
ums_realtek            18248  0 
uas                    18180  0 
i915                  472941  2 
drm_kms_helper         46978  1 i915
wmi                    19256  1 dell_wmi
drm                   242038  3 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
usb_storage            49198  1 ums_realtek

```I'll post the desktop code in a sec...

---

### Post by mtguy on 2012-08-19
Now desktop:
```
~:lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0458:0007 KYE Systems Corp. (Mouse Systems) 
Bus 004 Device 002: ID 0a48:3239 I/O Interconnect Multimedia Card Reader
Bus 001 Device 016: ID 0424:3803 Standard Microsystems Corp. 
Bus 001 Device 017: ID 04e8:6860 Samsung Electronics Co., Ltd GT-I9100 Phone [Galaxy S II]

```and

```
~:lsmod
Module                  Size  Used by
cdc_acm                22306  0 
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
nvidia              10962290  30 
snd_emu10k1_synth      12963  0 
snd_emux_synth         33455  1 snd_emu10k1_synth
snd_seq_virmidi        13309  1 snd_emux_synth
snd_seq_midi_emul      13526  1 snd_emux_synth
snd_emu10k1           133257  4 snd_emu10k1_synth
binfmt_misc            17292  1 
snd_ac97_codec        106082  1 snd_emu10k1
ac97_bus               12642  1 snd_ac97_codec
snd_hda_codec_realtek   174222  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_pcm                80845  4 snd_emu10k1,snd_ac97_codec,snd_hda_intel,snd_hda_codec
snd_util_mem           13786  2 snd_emux_synth,snd_emu10k1
snd_hwdep              13276  3 snd_emux_synth,snd_emu10k1,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event     14475  2 snd_seq_virmidi,snd_seq_midi
snd_seq                51567  5 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
snd_timer              28931  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         14172  5 snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  12849  0 
snd                    62064  25 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_pcm,snd_hwdep,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13027  0 
mac_hid                13077  0 
soundcore              14635  1 snd
snd_page_alloc         14115  3 snd_emu10k1,snd_hda_intel,snd_pcm
parport_pc             32114  1 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usb_storage            39646  0 
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77367  1 usbhid
floppy                 60310  0 
tulip                  52487  0 
firewire_ohci          40180  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sky2                   49545  0 

```As I indicated previously, thunar doesn't see the device on *either* computer.  Nautilus sees it on the desktop, but nautilus isn't installed on the laptop.  The only other difference is desktop is 32 bit, laptop is 64.

Thanks for the help :)

---

### Post by TenPlus1 on 2012-08-19
Go here:

[http://www.omgubuntu.co.uk/2012/07/android-sdk-installer-for-linux-debianubuntu](http://www.omgubuntu.co.uk/2012/07/android-sdk-installer-for-linux-debianubuntu)

and download the android sdk installation script and run it, only say yes to the steps which autodetect android phones and install mpt devices, skip all others and it should setup Ubuntu so that your phone will be recognised in any file manager...

---

### Post by mtguy on 2012-08-19
> **TenPlus1 said:**
> Go here:

[http://www.omgubuntu.co.uk/2012/07/android-sdk-installer-for-linux-debianubuntu](http://www.omgubuntu.co.uk/2012/07/android-sdk-installer-for-linux-debianubuntu)

and download the android sdk installation script and run it, only say yes to the steps which autodetect android phones and install mpt devices, skip all others and it should setup Ubuntu so that your phone will be recognised in any file manager...

Unfortunately, it neither worked on the laptop nor my desktop.  Tried rebooting both after running the script, but no dice...still no phone in thunar.

---

