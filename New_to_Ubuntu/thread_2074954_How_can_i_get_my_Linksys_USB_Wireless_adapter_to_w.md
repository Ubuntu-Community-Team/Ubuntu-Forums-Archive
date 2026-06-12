---
title: "How can i get my Linksys USB Wireless adapter to work?"
date: 2012-10-22
forum: New to Ubuntu
---

### Post by tobye on 2012-10-22
I recently loaded Ubuntu version 12.04 onto my computer, and I have a WUSB54G v4 USB wireless adapter. I first tried to get it to work by simply plugging my adapter into an open USB port. This seemed to work fine, it came up with a list of wireless adapters, so I clicked on the correct one and entered the security code. It looked like it was going to connect. It tried for about five minutes before I stopped it. I then decided to create a network as I also have one setup. I did this and it connected, only one problem, I couldn't get onto the internet.

Please help me, I am new to Ubuntu and am totally lost.

---

### Post by Sonsum on 2012-10-22
I actually have this exact USB device and it is the reason I initially came to Ubuntu many years ago because it was the first linux distribution I found that supported it out of the box.

I plugged my device in and it appeared to work, but oddly, I couldn't get internet once I connected to my router either.

Perhaps the instructions on the Debian wiki will be of some use? [Here's the link.]("http://wiki.debian.org/rt2500usb")

What kind of network encryption does your wireless use? I'm using WPA2.

---

### Post by squakie on 2012-10-22
Post the output back of:

lsusb

lsmod

---

### Post by tobye on 2012-10-23
Okay I went into the terminal, below is the output.
```
tobye@Bunny:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0b38:0010 Gear Head 107-Key Keyboard
Bus 004 Device 003: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 001 Device 004: ID 13b1:000d Linksys WUSB54G v4 802.11g Adapter [Ralink RT2500USB]
tobye@Bunny:~$ lsmod
Module                  Size  Used by
arc4                   12473  2 
rt2500usb              22652  0 
rt2x00usb              20061  1 rt2500usb
rt2x00lib              48805  2 rt2500usb,rt2x00usb
mac80211              436455  2 rt2x00usb,rt2x00lib
cfg80211              178679  2 rt2x00lib,mac80211
dcdbas                 14098  0 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0 
snd_hda_codec_idt      60251  1 
joydev                 17393  0 
psmouse                72919  0 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
serio_raw              13027  0 
parport_pc             32114  1 
snd_seq_midi_event     14475  1 snd_seq_midi
i915                  414739  3 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13077  0 
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
e100                   36289  0 
usbhid                 41906  0 
hid                    77367  1 usbhid


```

---

### Post by squakie on 2012-10-24
I've got to go looking for it, but I seem to remember a how-to somewhere for ubuntu and this adapter. If it was his adapter, in involved creating a shell script and running it at startup. I'll see if I can find it.
 
Update:  looks like what I was thinking was actually for the rt2800usb, but I sure thought I had seen the rt2800usb driver being used with the rt2500usb.
 
At any rate, I don't know if the driver supports wpa encryption or not.  So, if you can't connect to your router, you could try changing the router to wep and try connecting then (only temporary for testing - wep is so crackable that you need to be sure to set it back when you're done testing).

---

### Post by squakie on 2012-10-24
Just for grins (maybe more) you could try:

sudo rmmod rt2500usb

sudo modprobe rt2800usb

Then check to see if you can connect.  If not, just reboot and everything will be "undone".  If for some reason it does work,  perhaps we can find a way to make it permanent.

---

### Post by tobye on 2012-10-24
When I type 'sudo rmmod rt2500usb' is just shuts off my wifi. Is there anything else that I can do?

---

### Post by squakie on 2012-10-25
It will - it's removing the rt2500usb driver.  The idea is to try loading the rt2800usb driver and see if it works for you.  Both of these will only be for the current load of the system.  Since we did not make them permanent, a reboot will put everything back.  You could also do the reverse if it doesn't work:
 
sudo rmmod rt2800usb 
 
This will tell the kernel not to use the rt2800usb driver
 
sudo modprobe rt2500usb
 
This will tell the kernel to use the rt2500usb driver again.

---

### Post by tobye on 2012-10-27
Nothing happens with either, any more suggestions please?

---

