---
title: "Sound does not play at all in Firefox Flash/Pidgin/etc. (11.10)"
date: 2011-09-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by thenickperson on 2011-09-25
I'm on an eMachines E627 Series laptop, on Ubuntu 11.10 beta 2. I recently clean installed 11.04 and upgraded to this beta, and the sound has been working great.

However, as of a day or two ago, only some things will actually play audio. Flash in Chrome works. Flash in Firefox does not. HTML 5 video in Firefox works. Pidgin's sounds do not work. The GNOME login sound does not play. When I lower or raise my volume in Ubuntu, the pop sounds (new feature in 11.10) DO play properly, so I want to say that system sounds are working fine.

I followed this guide ([http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)). "aplay -l" worked, so I moved on to the alsamixer section. I ramped up all the voume bars, and turned off auto mute, but I still have the same problem. I also installed alsa-oss and reinstalled Flash, but nothing changed. I rebooted, same issues.

Can someone please help me out? I'm a Linux noob with a small amount of experience, and I'd REALLY appreciate some help.

Also, if this belongs somewhere else because it's a problem with a beta of Ubuntu, please let me know.

---

### Post by damianb on 2011-09-27
Hi,

I have also experienced losing the GNOME login sound after a recent update to my 11.10 Beta 2 system.

Occasionally I find Flash stops working also, but I usually just reinstall Adobe Flash from the software centre.

It's still Beta, so you can expect these intermittent problems

---

### Post by lidex on 2011-09-27
Please, if you want a stable system, do not use the development version. Any questions about 11.10 oneiric should go to the development forum - the answer may already be there:
[http://ubuntuforums.org/forumdisplay.php?f=403](http://ubuntuforums.org/forumdisplay.php?f=403)

---

### Post by mörgæs on 2011-09-27
Thread moved

---

### Post by thenickperson on 2011-10-08
Problem solved. I updated and upgraded packages through apt-get a bit after writing that post, and it updated a ton of audio drivers. I rebooted, and the problem was solved. Pidgin still wasn't playing sounds, but I realised I just had to change it sounds to ALSA in its sound settings.

---

