---
title: "[SOLVED] getting sound to work"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by JimmyJim on 2008-05-27
I just removed my Creative sound card (X-Fi) and I went in BIOS and switched on board sound on. I'm in Ubuntu and I'm not getting any sound. I'm using headphones. My motherboard is an Asus A8N SLi Premium.

What could be wrong? Is there something that I need to configure. I have no idea if its a hardware problem or software problem. If you need specific information, let me know. 

Thanks in advance

---

### Post by ethoxyethaan on 2008-05-27
try 

```
sudo apt-get install linux-backports-modules
```

you will need to reboot your system afterwards.

---

### Post by JimmyJim on 2008-05-27
> **ethoxyethaan said:**
> try 

```
sudo apt-get install linux-backports-modules
```

you will need to reboot your system afterwards.

I get this message: "E: Couldn't find package linux-backports-modules"

---

### Post by ethoxyethaan on 2008-05-27
> **JimmyJim said:**
> I get this message: "E: Couldn't find package linux-backports-modules"
try it via synaptic packet manager.

oh shi-

are you using ubuntu 7.10 or ubuntu 8.04.

because i noticed ubuntu 8.04 already had the back ports integrated.

---

### Post by JimmyJim on 2008-05-27
> **ethoxyethaan said:**
> try it via synaptic packet manager.

oh shi-

are you using ubuntu 7.10 or ubuntu 8.04.

because i noticed ubuntu 8.04 already had the back ports integrated.

8.04: I didn't install anything yet -- What should I do?

---

### Post by ethoxyethaan on 2008-05-27
> **JimmyJim said:**
> 8.04: I didn't install anything yet -- What should I do?
not sure i never did such a thing. i dident even know you can play sound without a sound card. (unless system beep).

and i never used 8.04 aswell.

---

### Post by JimmyJim on 2008-05-27
> **ethoxyethaan said:**
> not sure i never did such a thing. i dident even know you can play sound without a sound card. (unless system beep).

and i never used 8.04 aswell.

OK well thanks for trying. Hopefully someone will come along and save the day... :|

I believe my onboard sound is AC97 if that helps anyone.

---

### Post by Delever on 2008-05-28
To check if sound card is detected, use:

aplay -l

It will list detected sound cards. If it is detected, make sure it is not muted.

To check if ubuntu sees your sound card among devices, use:

lspci -v

If not,
try to install:

```

sudo apt-get install linux-ubuntu-modules-$(uname -r)
```

If it wasnt' already installed, restart.

Then, if it is still not working:

```

sudo dpkg-reconfigure pulseaudio
sudo dpkg-reconfigure alsa-base
asoundconf set-pulseaudio

```

Check again results with "aplay -l", and if it is not muted.

---

### Post by vlad1975 on 2008-05-28
Hi 

I am having similar problem and i did what said here. this is what i got

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Headset [Plantronics Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

NOw the problem is sound is playing on card 2: Headset [Plantronics Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1

How can i make it default play on card 0: Intel [HDA Intel], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1 ???

---

### Post by Delever on 2008-05-28
Applications->Add/Remove->PulseAudio Device Chooser

Start it, open volume control. You can probably choose default device there (i only have one sound card, integrated AC97 on intel chipset).

---

### Post by sayakb on 2008-05-28
> **JimmyJim said:**
> OK well thanks for trying. Hopefully someone will come along and save the day... :|

I believe my onboard sound is AC97 if that helps anyone.

Do you have your repositories enabled? Goto System->Administration->Software sources and enable all Ubuntu/3rd party software and the important and recommended updates.
Then press Reload on the next dialog. 
Then:
```
sudo apt-get install linux-backports-modules
```

---

### Post by JimmyJim on 2008-05-28
> **LinuxIsInnovation said:**
> Do you have your repositories enabled? Goto System->Administration->Software sources and enable all Ubuntu/3rd party software and the important and recommended updates.
Then press Reload on the next dialog. 
Then:
```
sudo apt-get install linux-backports-modules
```

I did the first step. I tried 'sudo apt-get install linux-backports-modules' but it said it wasn't found: 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules"

---

### Post by JimmyJim on 2008-05-28
> **Delever said:**
> To check if sound card is detected, use:

aplay -l

It will list detected sound cards. If it is detected, make sure it is not muted.

This came up, I think its detected: 

**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

> **Delever said:**
> To check if ubuntu sees your sound card among devices, use:

lspci -v

This showed, so I think Ubuntu sees my integrated sound:

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
	Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	I/O ports at dc00 [size=256]
	I/O ports at e000 [size=256]
	Memory at d5003000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

> **Delever said:**
> 
Then, if it is still not working:

```

sudo dpkg-reconfigure pulseaudio
sudo dpkg-reconfigure alsa-base
asoundconf set-pulseaudio

```

Check again results with "aplay -l", and if it is not muted.

I tried that and its still not working. Its not muted in my volume control panel. Can it be muted elsewhere?

---

### Post by JimmyJim on 2008-05-28
bump

---

### Post by JimmyJim on 2008-05-28
bump.. :|

---

