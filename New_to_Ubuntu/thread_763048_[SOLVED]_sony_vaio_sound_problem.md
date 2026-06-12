---
title: "[SOLVED] sony vaio sound problem"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by panosp on 2008-04-22
Hi all,

i have a sony vaio vgn-ar41l, gutsy installed and i'm quite a newbie. i had a problem with headphones but i kinda solved it following the instructions found [here]("http://ubuntuforums.org/showthread.php?p=4298894#post4298894") ...kinda! when i switch to the second user i'm using in the beginning it's all right, but then the sound disappears from the panel and there is no sound. And even worse, when i try to shut down the laptop hangs completely and i have to, well, force it to close. any ideas?

EDIT I uninstalled and reinstalled alsa following the instructions [here]("http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+mixer") and then:

sudo gedit /etc/modprobe.d/alsa-base
 and in the config file in the bottom i added

options snd-hda-intel model=vaio position_fix=0

thanx

---

### Post by ZabiGG on 2008-05-16
Hi there and thanks for your question...

Sorry it took so long. Posts pile up pretty fast in this section of the forum.

Are you still trying to solve this issue? If you have, we'd love to know the outcome.

If you still need help, I can help you find some, so just post back.

Thanks,

ZabiGG

---

### Post by panosp on 2008-05-16
thanx for the reply,
i have hardy installed now and i have the same problem as gutsy (no sound in headphones)., but i didn't dare doing the same again cause it caused so much instability to my system. 

i also found this [link]("http://ubuntuforums.org/showthread.php?t=677331"). Do you think it's better this way?

---

### Post by ZabiGG on 2008-05-16
I am really, really not an expert. But the advice in your link sounds OK. Did you try it?

---

### Post by panosp on 2008-05-18
well, tried it and now headphones work, but the sound is very low, master control doesn't seem to affect volume (whether it's high or low, sound is the same) and i don't get any sound from totem or the sound check on "hardware testing" section (system).

the info of my soundcards is 
**** List of PLAYBACK Hardware Devices ****
card 0: pcsp [pcsp], device 0: pcspeaker [pcsp]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 2: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

it might be something like adding the corect model of the soundcard at the alsa-base file, but either way i can't figure out the model myself.

how do i get it back as it was?

---

### Post by ZabiGG on 2008-05-18
The second post in this archive link should help

[http://ubuntuforums.org/showthread.php?t=539595](http://ubuntuforums.org/showthread.php?t=539595)

---

### Post by panosp on 2008-05-19
the issue is solved, thanx for the attention ZabiGG

I uninstalled and reinstalled alsa following the instructions [here]("http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+mixer") and then:

**sudo gedit /etc/modprobe.d/alsa-base**
and in the config file in the bottom i added

**options snd-hda-intel model=vaio position_fix=0**

thanx

---

### Post by ZabiGG on 2008-05-19
Happy I could help ;)

---

