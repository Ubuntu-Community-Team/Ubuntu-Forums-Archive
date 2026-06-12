---
title: "Laptop speakers won't shut up!"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by Pirkiz on 2008-10-31
I've been googling this, and it seems to be a quite common problem, but I haven't been able to find a solution so I'm posting here. I'm running Xubuntu 8.10 on a Fujitsu Siemens Amilo Li 1818 laptop. When I have external speakers or headphones plugged in, they're working just fine, but the problem is that the sound *also* comes from the laptop speakers. How do I get them to shut up? :|

I have the latest version of ALSA installed.

**lspci** gives me:
 ```
description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
```Under "volume controls" I have the following options: Master, Headphone, PCM and Front. (and Mic, Mic boost, Capture and Capture,1 but I'm assuming those have nothing to do with the sound *output*. I tried moving them as well and nothing happened.)
Master, PCM and Front all adjust the volume in both the laptop speakers and the headphones/external speakers equally. The "headphones" option doesn't seem to have any effect on anything whatsoever, not even the headphones.

Any ideas?

---

### Post by reg4c on 2008-10-31
Aah, I had that problem on Hardy but it got solved after an update.

What I used to do was open alsamixer eveytime I wanted to use the headphones, and would mute the speakers. That was because I was a noob and could not find the solution.

```
alsamixer
```

and then with trial and error mute the speakers.
Cheers

---

### Post by Pirkiz on 2008-10-31
Tried that, but everything that mutes the laptop speakers also mutes the headphones/external speakers. Except when I set the "front" option to zero, then the laptop speakers are silent but i still hear a little sound from the headphones/external speakers. But it's really quiet. :( There must be a better way to fix this.

---

### Post by Pirkiz on 2008-11-02
Anyone? :(

---

### Post by detroit/zero on 2008-11-02
This works for me on a Toshiba Satellite a135 with Realtek sound.

In a terminal:```
sudo gedit /etc/modprobe.d/alsa-base
```Add the following line where you see the other options listed:```
options snd-hda-intel position_fix=1 model=lenovo
```If the line already exists (which it might) change the model to **lenovo**.

I don't know if you have to reboot or what to make it work. Probably shutting down and restarting ALSA will do the trick.

Getting the microphone to work is a different hassle, and one that I haven't yet gotten around to working on.

---

### Post by Pirkiz on 2008-11-02
I tried:
```
sudo gedit /etc/modprobe.d/alsa-base
```
It tells me:
```
sudo: gedit: command not found
```

---

### Post by detroit/zero on 2008-11-02
> **Pirkiz said:**
> I tried:
```
sudo gedit /etc/modprobe.d/alsa-base
```It tells me:
```
sudo: gedit: command not found
```
My bad.. It didn't register in my still-asleep brain that you were using Xubuntu. Just change *gedit* for the text editor that comes with XFCE.

(I never really used XFCE, so I don't know. A quick google search tells me it's something called "Mousepad"?)

---

### Post by Pirkiz on 2008-11-02
I added the line and rebooted, but it didn't seem to have any effect whatsoever. :confused:

---

### Post by detroit/zero on 2008-11-02
Maybe now try messing with the headphone option in the mixer gui?

That's what works for me, anyways. Beyond that I'm not sure what to tell you.

---

### Post by Pirkiz on 2008-11-02
Yeah, I've tried, but I just can't get the internal speakers to shut up entirely. However, if I turn the "front" volume down they're not that loud, and I can just turn the volume knob on the external speakers to max so it kinda drowns the sound from the crappy internal ones. So... yeah it's a bit weird but I guess I can live with it.

---

### Post by Nepherte on 2008-11-02
Replace lenovo with fujitsu.

---

### Post by Pirkiz on 2008-11-02
> **Nepherte said:**
> Replace lenovo with fujitsu.

Did that, rebooted... Still no change.

---

### Post by detroit/zero on 2008-11-02
About the only other thing I can do is give you the HDA Intel sound how-to from the community docs. I don't remember if this is specifically for Feisty or Gutsy, but it works for me on Hardy, and I don't see any good reason it wouldn't work on Intrepid, as well.

[HdaIntelSoundHowto - Community Ubuntu Documentation]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

It involves compiling a patched version of ALSA that works better with the Intel on-board audio hardware. This means you're going to have to follow the steps and re-compile ALSA every time a kernel update comes through.

---

### Post by gogetakame on 2009-11-04
i have an hp dv6-1353cl with ubuntu 9.10 full release now.
I was having trouble with the sound as well. i would plug in earphoens and sound would play from both earphones and speakers.
so i opened up alsamixer in terminal and i messed around with the settings
so with your earphones plugged in. all u hafta do is set Speaker to 0.
then sound should only come from the headphones. if the sound is soft, then change up the scales for Master, PCM, and Front till you find a suitable combo.
for me i hav PCM and Front at 100 and i adjust Master up and down to get it to increase volume.
this is a hassle but it does work for me at least...
hope this helps...

---

