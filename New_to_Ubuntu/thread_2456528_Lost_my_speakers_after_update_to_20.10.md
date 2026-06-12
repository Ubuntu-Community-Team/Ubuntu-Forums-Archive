---
title: "Lost my speakers after update to 20.10"
date: 2021-01-13
forum: New to Ubuntu
---

### Post by joubqa on 2021-01-13
Soundbar attached with Digital to tv that is attached to laptop with HDMI. Can't see the speakers in Pulse anymore. Re-installed Pulse and alsa. In Pulse configuration it shows "(unplugged)(unavailable)" for Digital Stereo

inxi -SMA:
System:
  Host: Legion-Y530-15ICH-1060 Kernel: 5.8.0-36-generic x86_64 
  bits: 64 Desktop: N/A Distro: Ubuntu 20.10 (Groovy Gorilla) 
Machine:
  Type: Laptop System: LENOVO product: 81LB v: Lenovo Legion Y530-15ICH-1060 
  serial: <superuser/root required> 
  Mobo: LENOVO model: LNVNB161216 v: SDK0R32862 WIN 
  serial: <superuser/root required> UEFI: LENOVO v: 9VCN20WW 
  date: 06/15/2020 
Audio:
  Device-1: Intel Cannon Lake PCH cAVS driver: snd_hda_intel 
  Device-2: NVIDIA GP106 High Definition Audio driver: snd_hda_intel 
  Device-3: Licensed by Sony Entertainment America Wireless Stereo Headset 
  type: USB driver: hid-generic,snd-usb-audio,usbhid 
  Device-4: Sony DualShock 4 [CUH-ZCT2x] type: USB 
  driver: snd-usb-audio,sony,usbhid 
  Sound Server: ALSA v: k5.8.0-36-generic

---

### Post by ActionParsnip on 2021-01-13
Try rebooting the sound bar with it connected. Once it is started run:
```

dmesg | tail

```
Do you see anything about sound?

---

### Post by joubqa on 2021-01-13
[ 1996.339241] rtw_8822be 0000:07:00.0: firmware failed to restore hardware setting
[ 2196.325765] rtw_8822be 0000:07:00.0: timed out to flush queue 2
[ 2212.182658] rtw_8822be 0000:07:00.0: firmware failed to restore hardware setting
[ 2232.151768] rtw_8822be 0000:07:00.0: firmware failed to restore hardware setting
[ 2269.975755] input: Designer Keyboard as /devices/virtual/misc/uhid/0005:045E:0806.0008/input/input38
[ 2269.976026] input: Designer Keyboard Consumer Control as /devices/virtual/misc/uhid/0005:045E:0806.0008/input/input39
[ 2269.976118] hid-generic 0005:045E:0806.0008: input,hidraw4: BLUETOOTH HID v1.20 Keyboard [Designer Keyboard] on 28:3a:4d:7d:cb:56
[ 2458.179261] rtw_8822be 0000:07:00.0: firmware failed to restore hardware setting
[ 2498.085209] rtw_8822be 0000:07:00.0: firmware failed to restore hardware setting
[ 2527.998122] rtw_8822be 0000:07:00.0: failed to send h2c command

---

### Post by joubqa on 2021-01-17
something I could try?

---

### Post by joubqa on 2021-01-20
How do I check if it's a driver issue?

---

### Post by tea for one on 2021-01-20
> **joubqa said:**
> something I could try?

Your set up is intricate with laptop speaker, TV speakers, soundbar, headset etc.
Also, you did not mention which speakers have been lost?
Did you have sound before updating to 20.10?

In this situation, why not go back to basics?

Unplug [COLOR="#FF0000"]everything[/COLOR] that is attached to your laptop.
Do you have sound from the laptop speakers?

if you have sound, plug in your next important device and test - trial and error is the answer.

If not, boot up a [COLOR="#0000FF"]live[/COLOR] session with Ubuntu 20.04 and check sound?

---

### Post by joubqa on 2021-01-30
I lost the soundbar after updating from 20.04. I have unplugged soundbar and restarted it. I have sound from laptop speakers and headphones.

---

### Post by joubqa on 2021-02-03
Restoring back to 20.04 from Timeshift worked

---

