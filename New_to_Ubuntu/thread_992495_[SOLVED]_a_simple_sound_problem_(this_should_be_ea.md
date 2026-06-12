---
title: "[SOLVED] a simple sound problem (this should be easy for you)"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by nakama85 on 2008-11-24
Ubuntu 8.10

So I can not get sound to my headphones via my front jack

I say this should be easy because I have 2 installs of 8.10
The sound works on one of them.

(This is the one the sound works on)
one install is on a separate Hard Drive(when I was still testing Ubuntu)

the other install is when I decided to get rid of windows.

I have looked at the config files of the original install and compared them to the new install but I don't see anything different.

I have an intel-hda-alc880 soundcard.

Note: one major difference I noticed but I don't know what it means.
when I run "alsamixer" on the new install it shows "pulse audio" and only a single sound slider.

when i ran the same command on the old install it showed "hda880 (alsa)"

---

### Post by a0u on 2008-11-24
Pulseaudio conflicts with ALSA and needs to be removed.

[http://ubuntuforums.org/showthread.php?t=973637](http://ubuntuforums.org/showthread.php?t=973637)

---

### Post by nakama85 on 2008-11-24
> **a0u said:**
> Pulseaudio conflicts with ALSA and needs to be removed.

[http://ubuntuforums.org/showthread.php?t=973637](http://ubuntuforums.org/showthread.php?t=973637)

thanks. I tried this it seemed to have no effect. Any other suggestions

---

### Post by nakama85 on 2008-11-25
bump

---

### Post by nakama85 on 2008-11-25
so i figured it out

I entered the following code into terminal
```
sudo gedit /etc/modprobe.d/alsa-base
```

and at the bottom of the page that opens I added this line
> options snd-hda-intel model=6stack
Clicked Save and then I rebooted.

The correct jack works now.

The only Problem I am having now is that when I plug in My headphones it does not automatically shut off my speakers. But it's not all that inconvenient to reach 1 1/2 feet to turn them off.

---

