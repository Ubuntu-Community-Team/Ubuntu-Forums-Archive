---
title: "Sound problems on Asus Eee"
date: 2012-03-13
forum: New to Ubuntu
---

### Post by CompBio on 2012-03-13
I've got an annoying problem with the sound on my Eee.  It seems that no matter what video player I use (VLC, mplayer, Totem) the sound through my headphones has extremely loud "background" music but voices are almost inaudible.  This has been with Ubuntu 11.04 and now 11.10 too.

Here's the information on my sound card:

> $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I've tried playing with Alsa mixers as recommended in various posts online, but I can't get them to work.

If anyone else has had this problem and solved it, I'd really like to know how you did it.

---

### Post by CompBio on 2012-03-14
I should mention that this happens with all audio, not just the audio portion of videos.  For example, if I listen to Pandora, I can hear the music just fine, but singers' voices are muted.  The sound coming from the little laptop speaker seems to be fine; it's only with headphones that I have this problem.

---

### Post by tbhatia4 on 2012-03-14
> **CompBio said:**
> I should mention that this happens with all audio, not just the audio portion of videos.  For example, if I listen to Pandora, I can hear the music just fine, but singers' voices are muted.  The sound coming from the little laptop speaker seems to be fine; it's only with headphones that I have this problem.

try installing additional drivers from system menu

---

### Post by CompBio on 2012-03-15
> **tbhatia4 said:**
> try installing additional drivers from system menu

I've got alsa-base 1.0.24 right now.  Any particular driver I should try to add?

---

### Post by sk8brding on 2012-03-15
Maybe this will help... DKMS - rebuilds automatically
[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

The start page for the info was at
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

The new source seems to be at
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)
[https://wiki.ubuntu.com/Audio](https://wiki.ubuntu.com/Audio)

Some people have had luck with this solution on other ASUS models for mic issues. Good luck.
[http://ubuntuforums.org/showthread.php?t=1805889&highlight=UL20FT](http://ubuntuforums.org/showthread.php?t=1805889&highlight=UL20FT)

The file I used was - alsa-hda-dkms_0.201202151440~oneiric1_all.deb

---

### Post by CompBio on 2012-03-16
Thanks!  I'll give those a try and report back.

---

