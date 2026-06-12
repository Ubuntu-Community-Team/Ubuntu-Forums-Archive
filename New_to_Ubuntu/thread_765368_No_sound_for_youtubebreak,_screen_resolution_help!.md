---
title: "No sound for youtube/break, screen resolution help!"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by tsnax4 on 2008-04-24
Hi,
I just updated to 8.04 last night and now I do not get sound on any internet videos, what happened? Do i need to reinstall a package or something of that sort.

My other/biggest problem is my inability to change my screen resolution, any time i go to system/preferences/screen resolution I get an error reading... The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available.
I already tried running the dpkg-reconfig xorg (not exact) command and that did not fix my problems.

Can anyone please help on these 2 issues? greatly appreciated.

---

### Post by macogw on 2008-04-24
libflashsupport is needed for sound on Flash with PulseAudio

---

### Post by 1440 on 2008-04-24
Yeah, I can confirm that this is indeed the solution to the "no sound in flash" problem.

---

### Post by fordp on 2008-04-24
This worked for me too.

Why does it not install that package automatically ??

Is this not a bug?

Thanks for the help !

---

### Post by tsnax4 on 2008-04-24
thanks for the help, anyone know whats up with the second issue?

---

### Post by psyke83 on 2008-04-24
Please see my post here: [http://ubuntuforums.org/showthread.php?p=4785624#post4785624](http://ubuntuforums.org/showthread.php?p=4785624#post4785624)

---

### Post by dasunsrule32 on 2008-04-25
This problem is based on whether you have esd, alsa or pulse installed. If you are doing a fresh install, then you will have pulse installed. If you have audio issues with alsa, make sure to have libesd-alsa0 loaded. That will take care of the same issues. Also, if your Firefox 3 starts taking a dive while you are playing, uninstall the libpulsesupport, that is what is causing it, and load libesd-alsa0. Coolio, good luck boys!

---

### Post by psyke83 on 2008-04-25
> **dasunsrule32 said:**
> This problem is based on whether you have esd, alsa or pulse installed. If you are doing a fresh install, then you will have pulse installed. If you have audio issues with alsa, make sure to have libesd-alsa0 loaded. That will take care of the same issues. Also, if your Firefox 3 starts taking a dive while you are playing, uninstall the libpulsesupport, that is what is causing it, and load libesd-alsa0. Coolio, good luck boys!

Everybody has ALSA installed, and both ESD and PulseAudio use the ALSA drivers.

PulseAudio now *replaces* ESD in Hardy, so there is no need to install libesd-alsa0; in fact it could probably cause conflicts.

The proper fix for Flash issues is being worked out here: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888)

A solution for now is to install libflashsupport to give PulseAudio support to flash, but it causes some instability (crashes in Firefox).

---

### Post by dasunsrule32 on 2008-04-28
> **psyke83 said:**
> Everybody has ALSA installed, and both ESD and PulseAudio use the ALSA drivers.

PulseAudio now *replaces* ESD in Hardy, so there is no need to install libesd-alsa0; in fact it could probably cause conflicts.

The proper fix for Flash issues is being worked out here: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888)

A solution for now is to install libflashsupport to give PulseAudio support to flash, but it causes some instability (crashes in Firefox).

Interesting, then why is when I unload the libesd-alsa0, I get no sound at all, even when I select the pulse audio sound and have the libflashsupport loaded. I checked aptitude and it is loaded. I guess I prefer using the aforementioned lib file because I have no issues using that file.

---

