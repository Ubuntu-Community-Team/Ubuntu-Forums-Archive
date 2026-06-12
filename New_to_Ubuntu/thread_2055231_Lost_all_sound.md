---
title: "Lost all sound"
date: 2012-09-08
forum: New to Ubuntu
---

### Post by Hex9 on 2012-09-08
Hi all

I seem to have lost ALL sound on ubuntu 12.04 LTS
The sound isnt on mute and ive had a look though the options.
When i boot into windows everything works just fine

Thanks

---

### Post by shadedpixel on 2012-09-08
> **Hex9 said:**
> Hi all

I seem to have lost ALL sound on ubuntu 12.04 LTS
The sound isnt on mute and ive had a look though the options.
When i boot into windows everything works just fine

Thanks

Launch terminal and type
```
alsamixer
```check to make sure that the Master and PCM levels have a 0db gain.

I snagged this from the arch linux wiki, it may help you:

> 
The current version of ALSA installs with all channels **muted by default**. You will need to unmute the channels manually. 
It is easiest to use alsamixer ncurses UI to accomplish this (alternatively, use amixer from the commandline): 
 $ alsamixer The label MM below a channel indicates that the channel is muted, and 00 indicates that it is open. 
Scroll to the Master and PCM channels with the &#8592; and &#8594; keys and unmute them by pressing the m key. Use the &#8593; key to increase the volume and obtain a value of 0 dB gain. The gain can be found in the upper left next to the Item: field. Higher values of gain will produce distorted sound. 
To get full 5.1 or 7.1 surround sound you likely need to unmute  other channels such as Front, Surround, Center, LFE (subwoofer) and Side  (these are the names of the channels with Intel HD Audio, they may vary  with different hardware). Please take note that this will not  automatically upmix stereo sources (like most music). In order to  accomplish that, see [#Upmixing/Downmixing]("https://wiki.archlinux.org/index.php/Advanced_Linux_Sound_Architecture#Upmixing.2FDownmixing"). 
Leave alsamixer by pressing Esc.

---

### Post by Hex9 on 2012-09-08
> **shadedpixel said:**
> Launch terminal and type
```
alsamixer
```check to make sure that the Master and PCM levels have a 0db gain.

I snagged this from the arch linux wiki, it may help you:

Thanks, i had Master at -24 db. I made sure all were unmuted.

Yet the problem still exists...

---

### Post by pqwoerituytrueiwoq on 2012-09-08
hdmi or 3.5mm audio cable?
```
lspci | grep Audio
```

---

### Post by Hex9 on 2012-09-09
> **pqwoerituytrueiwoq said:**
> hdmi or 3.5mm audio cable?
```
lspci | grep Audio
```

3.5mm
The code out putted by ```
lspci | grep Audio
```

00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Cayman/Antilles HDMI Audio [Radeon HD 6900 Series]

---

### Post by pqwoerituytrueiwoq on 2012-09-09
could also use output of ```
aplay -l
```

take a look here
[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/194488](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/194488)

---

### Post by Hex9 on 2012-09-09
> **pqwoerituytrueiwoq said:**
> could also use output of ```
aplay -l
```take a look here
[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/194488](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/194488)

Output of ```
aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I read that article and am currently re-installing sound drivers, ill get a response when i reboot.
I appretiate your help, pqwoerituytrueiwoq

---

### Post by Hex9 on 2012-09-09
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa; sudo apt-get  update;sudo apt-get dist-upgrade; sudo apt-get install linux-sound-base  alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r`  libasound2; sudo apt-get -y --reinstall install linux-sound-base  alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r`  libasound2; killall pulseaudio; rm -r ~/.pulse*; sudo usermod -aG `cat  /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e  '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed  's:,$::g'` `whoami`

```

Fixed my problem, thanks!

---

### Post by shadedpixel on 2012-09-09
Great, Enjoy Ubuntu!

---

### Post by shadedpixel on 2012-09-11
> **Hex9 said:**
> ```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa; sudo apt-get  update;sudo apt-get dist-upgrade; sudo apt-get install linux-sound-base  alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r`  libasound2; sudo apt-get -y --reinstall install linux-sound-base  alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r`  libasound2; killall pulseaudio; rm -r ~/.pulse*; sudo usermod -aG `cat  /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e  '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed  's:,$::g'` `whoami`

```

Fixed my problem, thanks!

I actually just got this problem today, I shall try this once I get home :D

---

