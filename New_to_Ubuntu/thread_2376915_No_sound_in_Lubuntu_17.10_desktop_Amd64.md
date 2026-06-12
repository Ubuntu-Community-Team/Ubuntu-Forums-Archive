---
title: "No sound in Lubuntu 17.10 desktop Amd64"
date: 2017-11-07
forum: New to Ubuntu
---

### Post by technologys on 2017-11-07
Hi. 
Help me to install sound for Asus R209H.

My system has:
CPU:       Quad core Intel Atom x5-Z8350
Audio:     Card-1 Intel HDMI/DP LPE Audio driver: HdmiLpeAudio Sound: ALSA v: k4.13.0-16-generic
           Card-2 bytcht-nocodec driver: bytcht-nocodec

In Terminal write down
*alsamixer *
and hit F6 key 
choose "Intel" than choose "bytcht-nocodec" but no sound.

Also checked In Terminal
sudo apt-get install pulseaudio pavucontrol
sudo apt-get install alsa-base pulseaudio
sudo alsa force-reload

but still no sound.

Or help me choose another distro for processor Intel Atom.

---

### Post by ajgreeny on 2017-11-07
Having installed pavucontrol, the Pulseaudio-Volume-Control, did you use ut to check that all the settings in it were correct for your hardware.

There are five separate tabs to it each being self explanatory about what they do.  Check that your hardware in the Output Devices tab is not muted or the volume set too low.

---

### Post by technologys on 2017-11-08
I cheked again all tabs. No muted and volume set 100% but still no sound.

---

### Post by lawdow123 on 2017-11-08
I have the same problem

---

### Post by technologys on 2017-11-08
Still no sound. Install PulseAudio Manager. In Default Source: none. 
Run in terminal command:  **lspci **and no entry for audio device.

---

### Post by attobot on 2017-11-22
Does this output any sound? 
**aplay -D sysdefault /usr/share/sounds/alsa/Side_Right.wav -vv **

Is there any error when you start pulseaudio?
** start-pulseaudio-x11**

---

### Post by ChuangTzu on 2017-11-22
perhaps [https://askubuntu.com/questions/493738/no-sound-in-lubuntu-14-04](https://askubuntu.com/questions/493738/no-sound-in-lubuntu-14-04)

---

### Post by technologys on 2017-11-26
No time to solve this problem. I had to install Windows 10. Thank you all for your help, already return a laptop.

---

### Post by littlefoot505 on 2017-12-01
I had the same problem and I fixed it somehow, but I've since forgotten how. I want to say I reinstalled pulseaudio or something. I'm still having some trouble with the sound in Ubuntu, which I started a thread on, but I did get the sound to work.

---

### Post by newbie32 on 2017-12-15
I've sound but not in Firefox + *Sound & Video > PulseAudio Volume Control* (pavucontrol) doesn't work.
No problem for [non root]("https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/WhatIsWrongWithSystemWide/") users.


> **attobot said:**
> 
Is there any error when you start pulseaudio?
** start-pulseaudio-x11**

```
[FONT=lucida console]Connection failure: Connection refused
pa_context_connect() failed: Connection refused[/FONT]
```

---

### Post by retch100 on 2017-12-16
I've a z8300 and the same issue.

---

