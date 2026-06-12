---
title: "Sound Issues in Ubuntu"
date: 2012-08-20
forum: New to Ubuntu
---

### Post by Dacendaran on 2012-08-20
Hey everyone,

I'm very new to Ubuntu and Linux in general.  I'm having issues with getting the computer to play sound. I've looked around at various threads and tried numerous things to fix the problem; however, the problem has gotten worse, and I'm not sure what I did to make that happen!  I know that sound issues seem common, but because I'm having so much trouble, I decided to ask people who know more than I do.  I'll try to be as detailed as possible, but I'm not sure what info is important.

The problem:  It started out that I could get sound through the speakers, but plugging in headphones would not route the sound through the headphones or mute the speakers. 
After trying to fix it, I can no longer get sound through the speakers either.

System Details:
Computer: Alienware M14xR2
Operating System: Ubuntu 12.10 Quantal Quetzal (sound works on Windows Partition)
Sound Card: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)


```
aplay -l
```
```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CA0132 Analog [CA0132 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Also, using the 
```
alsamixer
```
command gives the error:
```
cannot load mixer controls: Invalid argument
```
Adding 
```
options snd-hda-intel model=generic
```
to /etc/modprobe.d/alsa-base.conf allows alsamixer to open; however, I only have one slider: PCM.  Adjusting this slider does not cause sound to output.  I have seen other places that there should be multiple sliders, is this the problem?  I have a picture attached that shows what the alsamixer looks like in the terminal.

Any help would be appreciated!

---

### Post by Daveth on 2012-08-20
I think i would start by running Precise Pangolin rather than an alpha of Quantal, as there will be far fewer changes, bugs and regressions to cope with. The chipset is in a number of Ubuntu certified systems, so should just plug and play.

---

### Post by Hadaka on 2012-08-20
Hi, I have zero experience with 12.10, but here is a couple things you might want
to try.

change model from generic to =auto
select F5 in alsamixer to see other sliders
in system settings..cogged wheel launcher bar, click SOUND,HARDWARE, then
select your card,or see if its even listed.
check the speaker icon..upper right, to see if its muted.
also google ...sudo apt-get alsamixer for 12.10 and reload it.
hope something here helps...good luck

---

### Post by Curtis6767 on 2012-08-20
> **Dacendaran said:**
> Hey everyone,

I'm very new to Ubuntu and Linux in general.  I'm having issues with getting the computer to play sound. I've looked around at various threads and tried numerous things to fix the problem; however, the problem has gotten worse, and I'm not sure what I did to make that happen!  I know that sound issues seem common, but because I'm having so much trouble, I decided to ask people who know more than I do.  I'll try to be as detailed as possible, but I'm not sure what info is important.

The problem:  It started out that I could get sound through the speakers, but plugging in headphones would not route the sound through the headphones or mute the speakers. 
After trying to fix it, I can no longer get sound through the speakers either.

System Details:
Computer: Alienware M14xR2
Operating System: Ubuntu 12.10 Quantal Quetzal (sound works on Windows Partition)
Sound Card: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)


```
aplay -l
``````
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CA0132 Analog [CA0132 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```Also, using the 
```
alsamixer
```command gives the error:
```
cannot load mixer controls: Invalid argument
```Adding 
```
options snd-hda-intel model=generic
```to /etc/modprobe.d/alsa-base.conf allows alsamixer to open; however, I only have one slider: PCM.  Adjusting this slider does not cause sound to output.  I have seen other places that there should be multiple sliders, is this the problem?  I have a picture attached that shows what the alsamixer looks like in the terminal.

Any help would be appreciated!

12.10 is in Alpha 3 stage and is currently extremely unstable. You can try and stick it out with 12.10 if you like, but you might be better off downloading and installing 12.04, which you can do right over the top of your 12.10 install. 

GL

---

### Post by Dacendaran on 2012-08-21
Thanks for the responses everyone!

I'm pretty new at this, and just installed what was given to me by a colleague at school. The issue is more of a minor annoyance, than a critical issue, but I'm trying to learn how to use ubuntu and fixing these things seems like a good way to do that! I didn't realize that 12.10 was still in alpha until I started looking up how to fix this bug. If I can fix this, then I'd like to stick it out. If I can't find a fix in 12.10, I'll look into trying 12.04.

> 
change model from generic to =auto


I have sound back! Through both the speakers and the headphones. The problem now is that the speakers do not mute when the headphones plug in (I get sound through both).  

Also, alsamixer will no longer load when I use the alsamixer command. It says "cannot load mixer controls: invalid argument".

---

### Post by Zvezdica27 on 2012-08-21
try 

sudo alsa --force-reload

it's sth like this (writing from memory).

This should reload and redetect all sound harware and software. So everytime it jams, try this. Ubuntu 12.04 is quite buggy in this regard, unfortunately.

---

### Post by rehseboy on 2012-08-22
I'm on 12.04 with the same machine (Alienware m14xR2), and I've been having the same issue with headphones not muting speakers, and the same invalid argument response when trying to open alsamixer.

pavucontrol doesn't seem to help, nor do any of the other fixes I've seen in any of the other threads.

Does anyone have any insight on why this card/machine is acting up?

---

### Post by Dacendaran on 2012-08-23
> 
try 

sudo alsa --force-reload


No luck I'm afraid. Tried looking it up to see if the syntax is wrong and none of those worked either.

> 
I'm on 12.04 with the same machine (Alienware m14xR2), and I've been having the same issue with headphones not muting speakers, and the same invalid argument response when trying to open alsamixer.

pavucontrol doesn't seem to help, nor do any of the other fixes I've seen in any of the other threads.

Does anyone have any insight on why this card/machine is acting up?


Sorry you're having trouble too, though I'm glad that it's not an issue with 12.10 necessarily.  From the googling that I've done, it seems like its a problem with more than just our machine (I've seen threads with other makes/models and earlier versions of ubuntu), but I haven't found a good fix either.

---

### Post by Dacendaran on 2012-09-06
Hey everyone, just figured I'd give a quick update.

I uninstalled 12.10 and am now running 12.04LTS. Still having the same problem: the speakers do not mute when the headphones are plugged in.

I have found a terminal command that (somewhat) alleviates this issue:
```

amixer -c 0 cset numid=1 off

```

If my headphones are already plugged in, this will mute the speakers, but allow sound through the headphones.  It's not a perfect fix, though. If the headphones are unplugged and plugged back in, the problem comes back and the command will not work again until the computer is restarted.

Don't know if that information helps to diagnose the problem, but I figured I'd post it just in case.

---

### Post by glenstewart on 2012-12-22
The proper command is: sudo /sbin/alsa force-reload

> **Zvezdica27 said:**
> try 

sudo alsa --force-reload

it's sth like this (writing from memory).

This should reload and redetect all sound harware and software. So everytime it jams, try this. Ubuntu 12.04 is quite buggy in this regard, unfortunately.

---

