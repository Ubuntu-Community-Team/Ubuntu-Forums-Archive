---
title: "Ubunto 20.0.4 No sound at all, have tried many commandlines to no avail"
date: 2020-09-19
forum: New to Ubuntu
---

### Post by Eman1955 on 2020-09-19
added myself to the audio group but still cannot get any audio out of the speakers.  I've tried most every suggestion to no avail, updates, etc. I double checked all applications controlling audio and none were muted. I'm running a two year old OMEN laptop by HP.  Audio/sound works fine on the Windows side. I'm trying to quickly ween myself off Windows, but I have to have audio.  When I play music I can see that it is playing by activity on the horizontal meter under Settings – sound – output.  Any help is greatly appreciated.  Thanks in advance.  Scott

These system details might help
0:1f.3 Audio device: Intel Corporation CM238 HD Audio Controller (rev 31) 00:1f.4 SMBus: Intel Corporation 100 Series/C230 Series Chipset Family SMBus (rev 31) 01:00.0 3D controller: NVIDIA Corporation GP107M [GeForce GTX 1050 Mobile] (rev a1) 01:00.1 Audio device: NVIDIA Corporation GP107GL High Definition Audio Controller (rev a1) 03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS522A PCI Express Card Reader (rev 01)

---

### Post by ajgreeny on 2020-09-19
You say you have tried all sorts of things to get audio but give us no detail of what those things were.  Give us much more detail of what you've tried already and we may be able to give you better advice.

However, have you looked at the alsamixer screen in terminal simply by running command ```
alsamixer
```
You can show different sound cards using F6 and having chosen your required card use Tab to move from Playback to Capture to All.
Increase or decrease the levels using cursor keys and mute/unmute with the M keyboard key.
Once set as you want use Esc to exit

If that does not help have a look in **pulseaudio volume control** either from the volume icon in the panel or with command ```
pavucontrol
``` and see if you get any clues from that to any muted devices.

---

