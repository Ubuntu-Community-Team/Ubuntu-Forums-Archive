---
title: "[SOLVED] No Sound in Xubuntu"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by Brightbelt on 2008-07-26
Hi,
  I'm trying out Xubuntu and I love the graphics. Other parts are coming much more slowly. 

I have no sound. I have an Intel HDA 82801G sound card and I'm on an HP dv9030us laptop. Here's what I've already tried:

- I downloaded the Gnome Alsamixer in Synaptic and made sure there were no mutes applied.
- I downloaded the alsamixergui and looked it over as well. 
- I've tried both the 'default' setting and the 'Hda:Intel' setting in the Sound section of the Settings Manager.
- I've rebooted multiple times to make sure these changes took.
 - I've tried editing the '/etc/modprobe.d/alsa-base' file and adding the line 'options snd-hda-intel model=hp' to that file.

Other posts that I've read on this don't show very good results for sound in Xubuntu. Hopefully we can iron this out.

I appreciate any help on this,...

Many Thanks, Frank B.

---

### Post by Brightbelt on 2008-07-26
Well, surprise here. I've got sound when I record and playback. AND, I get sound playback when I record in Ardour and in the gnome sound recorder.

Therefore, I am concluding that Xubuntu has no system sounds that it plays on booting and that this is one of the ways it works as a trimmed-down version of Ubuntu. Am I right??

Many Thanks, 
Frank B.

---

### Post by mali2297 on 2008-07-26
> **Brightbelt said:**
> 
Therefore, I am concluding that Xubuntu has no system sounds that it plays on booting and that this is one of the ways it works as a trimmed-down version of Ubuntu. Am I right??


Yes, you are absolutely right.

---

### Post by Brightbelt on 2008-07-26
Many Thanks, Mali. You've saved me a lot of needless effort. :)

---

