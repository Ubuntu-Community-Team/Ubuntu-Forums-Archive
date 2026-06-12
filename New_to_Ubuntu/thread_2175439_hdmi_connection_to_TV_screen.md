---
title: "hdmi connection to TV screen"
date: 2013-09-19
forum: New to Ubuntu
---

### Post by john_vaughan2 on 2013-09-19
Hello, I am running 13.04 and have just bought a hdmi lead so that I can use my TV screen as a monitor. I connected the laptop to the TV and told the TV to use hdmi1. The TV screen shows a blank desktop ( same colours and same design ) but no icons. I tried playing a video which ran fine on the laptop but the TV screen didn't change. Do I need some specific software? or do I need to change anything in my System Preferences? My laptop and TV also have a VGA socket. Would this be more likely to work? Any help would be much appreciated.
Thanks, John Vaughan

---

### Post by cmcanulty on 2013-09-19
I think you have to go into system settings-displays-and click in mirror displays box

---

### Post by newb85 on 2013-09-19
> **cmcanulty said:**
> I think you have to go into system settings-displays-and click in mirror displays box

That's correct, assuming the OP is using the generic video drivers.  If they're using nvidia drivers, they'll need to make the change in the nvidia settings.

---

### Post by TheFu on 2013-09-19
The specifics of your hardware and GPU will dictate how to make HDMI work. I know that with ATI-based GPUs, I had to take extra steps sometimes. Other times, the OS just did the right thing.

So, which laptop and which GPU does it have?

---

### Post by john_vaughan2 on 2013-09-19
Hello again and thanks for the replies. I went into settings and displays as suggested and then clicked Mirror Displays. After this I have a perfect copy of the laptop screen with all the same functions. The only problem is that the sound comes from the laptop and not the TV system. Do I need an extra cable perhaps?
The processor I have is an AMD E2-1800 APU with Radeon(tm) HD Graphics x2 and the Graphics are Gallium 0.4 AMD PALM. Presumably these and the TV ( which Ubuntu correctly identified as a Phillips ) are compatible as the picture is wonderful.
Any ideas for the sound problem would be useful but failing that I am going to try connecting some external speakers to the laptop.
JV

---

### Post by grahammechanical on 2013-09-19
HDMI does not necessarily include audio IN. My DTV/Monitor has a port for HDMI IN but a separate port for HDMI/PC/DVD-D Audio IN. A lot depends upon what the graphic adapter pushes out through the HDMI port. You may need to bring audio out from the Audio card.

Regards.

---

### Post by john_vaughan2 on 2013-09-19
Thanks for the idea Graham. Could you tell me what I need to do to " bring audio out from the Audio card. Sorry to ask but I am a genuine absolute beginner.
JV

---

### Post by TheFu on 2013-09-19
I have an AMD E350 APU with an ATI GPU built-in.  The audio and video work through HDMI.  The audio did not work by default. I don't know if this is the only way to get it working, just that is worked for my needs.
* use the proprietary ATI drivers for video/audio.
* after every new kernel, I'm forced to --reinstall those drivers to get video playback working without out-of-sync audio
* **aplay -l** will show the specific device you need to use.```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
On my system audio is at 0,3 (card 0, device 3) and I setup XBMC to use that.
Clear as mud?

I've got no idea how to tell stock Ubuntu to use a specific device, but some setting via **alsamixer** seems likely. I've never had anything but problems using pulse-audio, so I remove that completely from my systems.

---

### Post by john_vaughan2 on 2013-09-19
Hi Graham, don't worry. I've just discovered that I need to connect an Audio left/right cable to my Audio out adapter on the laptop.
Thanks to everyone. I'll now mark this as solved.
JV

---

### Post by john_vaughan2 on 2013-09-19
Thanks Fu also. I've only just seen your reply. Way beyond me I'm afraid but the cable does the trick.

---

