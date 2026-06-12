---
title: "Alsa help?"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by sandweng on 2008-05-27
So when I upgraded to 8.04, my sound in flash went out. I installed pulse because it worked for some people. Then I uninstalled pulse and I can't get in to alsamixer or use other audio programs, like Skype. How do I reset alsa to use my default sound chip? This is my error message:

<<

ALSA lib control.c:874:(snd_ctl_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_ctl_pulse.so

alsamixer: function snd_ctl_open failed for default: No such file or directory

>>

Thanks in advance

---

### Post by iaculallad on 2008-05-27
Had you tried doing it in the Sound Preferences?

System->Preferences->Sound and from the "Device" tab, change settings to use "Autodetect" or try selecting your sound chip from the drop-down list.

---

### Post by sandweng on 2008-05-27
thanks! that works for everything but sound capture. any ideas for that?

EDIT: also cant fire up alsamixer

---

