---
title: "can't get alsamixer to open"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by fredfelter on 2008-08-20
Somehow I got tangled up in PulseAudio such that Skype stopped working. After a valiant attempt to get the two apps to coexist and reading about the issue I decided Skype was worth more to me so I uninstalled PA. Now I can't even find Alsamixer to try to reconfigure it for Skype.

Here is my terminal response:
fred@fred-laptop:~$ alsamixer
*** PULSEAUDIO: Unable to connect: Connection refused

alsamixer: function snd_ctl_open failed for default: Connection refused

I know my sound card works cause it did before I messed around with PA, including having a functional Skype. I think I loaded my sound card driver with modprobe snd-cs46xx as it now appears in the nano /etcmodules after I added it. I don't know what else to do now.

Thanks in advance. 
Thinkpad T22, Ubuntu 8.04. S3 Corp. SoundFusion cs46xx sound card, module snd-cs46xx.

---

### Post by picpak on 2008-08-20
Does

```
alsamixer -c 1
```

work?

---

### Post by fredfelter on 2008-08-22
> **picpak said:**
> Does

```
alsamixer -c 1
```

work?

Thanks for the response Picpak.
Here is the response:

fred@fred-laptop:~$ alsamixer -c 1
wrong -c argument '1'

fred@fred-laptop:~$

---

