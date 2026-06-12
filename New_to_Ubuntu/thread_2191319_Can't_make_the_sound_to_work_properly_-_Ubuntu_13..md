---
title: "Can't make the sound to work properly - Ubuntu 13.10"
date: 2013-12-02
forum: New to Ubuntu
---

### Post by lidija.ldo on 2013-12-02
Hi,

I can't seem to get my sound working on my Ubuntu. My current Ubuntu version is 13.10 saucy. It was upgraded from previous version 12.04 and I still have the same problems. 

When I freshly installed Ubuntu, the sound was being heard through speakers AND headphones. I don't even have external speakers so there have to be some internal speakers on the machine.
I played with some settings and now I have no idea what I did - the sound completely stopped working. Are there step by step instructions of what I have to have enabled / disabled in order for the sound to work?

I apologize if this question sounds stupid, but I really don't know what to do in order to make this work.

Some info about my system:

```
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

```


```
$ aplay /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono

```
I don't hear anything. Headphones are mute. With or without "sudo".

```
$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD1882 Analog [AD1882 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: AD1882 Alt Analog [AD1882 Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
$ find /lib/modules/`uname -r` | grep snd
```
This command gives me an output of almost 200 lines.
 
```
$ lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)
    Subsystem: Lenovo Device 3047
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at fc220000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel


00:1d.0 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])

```

I would really appreciate some help.

---

### Post by thatredbird on 2013-12-02
I had similer issues. On my system, the sounds mute every time I started. So you should double check that.
 alsamixer in the terminal will let you access the toggles.

another post suggested
```
 sudo alsa force-reload 
```
However that didn't work for me

I ended up downloading
```
 
sudo apt-get install xfce4-mixer gstreamer0.10
 
```
then adjusted volume, a d toggled auto mute off.  Turned off the external amplifier check box as well. Though this might vary

---

### Post by lidija.ldo on 2013-12-03
> **thatredbird said:**
> I had similer issues. On my system, the sounds mute every time I started. So you should double check that.
 alsamixer in the terminal will let you access the toggles.

Thank you for the suggestions. Nothing is mute, though. I tried all the mixers possible, but nothing I do has any effect.
The only thing muted is "Beep", but that's ok, I want it that way.

> **thatredbird said:**
> 
another post suggested
```
 sudo alsa force-reload 
```
However that didn't work for me


No, it doesn't work for me either.

> **thatredbird said:**
> 
I ended up downloading
```
 
sudo apt-get install xfce4-mixer gstreamer0.10
 
```
then adjusted volume, a d toggled auto mute off.  Turned off the external amplifier check box as well. Though this might vary

Ok, I installed these packages and ran xfce4-mixer. But I can't seem to find the external amplifier check box :-k

I believe I have all the mixers installed there are :neutral:: Audio Mixer, Gnome ALSA Mixer, PulseAudio Volume Control, Qas Mixer and now also xfce4-mixer.

---

### Post by thatredbird on 2013-12-03
Sorry about the not being fixed yet. In the gnome alsa mixer is there an option for external amp that's marked?

---

### Post by lidija.ldo on 2013-12-05
> **thatredbird said:**
> Sorry about the not being fixed yet. In the gnome alsa mixer is there an option for external amp that's marked?

No, I don't see that option.

Available options are:
- Headphone (CHECKED)
- Auto-Mute Mode
- Channel Mode
- Independent HP
- Input Source
- Input Source

Only Headphone option is enabled. I don't know why there are two options "Input Source" though.

---

### Post by lidija.ldo on 2013-12-10
I solved this issue. In case enyone else has the same problem - here's what I did:

In QasMixer I chose Mixer device "hw: Card"

I have my "Headphone" checkbox enabled.

There's a dropdown menu with 3 options: "Disabled / Speaker Only / Line Out + Speaker"

I had "Line Out + Speaker" selected. I changed this to "Speaker Only" and now my headphones are working properly again.

Kind regards,
Lidija

---

