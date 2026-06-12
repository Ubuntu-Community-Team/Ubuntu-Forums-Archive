---
title: "sound issues"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by melopsittacus on 2008-06-05
Hi, I have recently installed Hardy, and I noticed that sometimes sounds just stop working, that is all programs supposed to produce sound output are just mute. (None of them give error messages though.)
If I reboot the machine sound works correctly though. (Sound used to work well in Gutsy.)

As I read in the forums that only one program at a time can use the audio device, I suspect that some other process is actually blocking it.

My question is: how can I find out which program is using or blocking the audio?

My other question: which package is responsible for sound? (In case I'd want to submit a bug report to Launchpad)

The other, smaller problem related to sound is that I never get logout music when turning off the computer. I can live with this however :D

---

### Post by DezSP on 2008-06-05
The program used to manage sound is called ALSA, though it sounds like you might have it set to OSS, check your sound settings and make sure it's all set to ALSA.

---

### Post by melopsittacus on 2008-06-06
I checked System->Preferences->Sound. The entries were set to autodetect, now I have changed them to ALSA, lets see if the error persists...

And I've found out how to list programs using the audio device. Here it is, in case someone else needs it:

```

lsof | grep snd

```

---

### Post by kpkeerthi on 2008-06-06
> **melopsittacus said:**
> Hi, I have recently installed Hardy, and I noticed that sometimes sounds just stop working, that is all programs supposed to produce sound output are just mute. (None of them give error messages though.)
If I reboot the machine sound works correctly though. (Sound used to work well in Gutsy.)

As I read in the forums that only one program at a time can use the audio device, I suspect that some other process is actually blocking it.

My question is: how can I find out which program is using or blocking the audio?

My other question: which package is responsible for sound? (In case I'd want to submit a bug report to Launchpad)

The other, smaller problem related to sound is that I never get logout music when turning off the computer. I can live with this however :D

You may want to [tweak pulseaudio]("http://ubuntuforums.org/showthread.php?t=776739") a bit. Good luck.

---

### Post by Joshua Netterfield on 2008-06-06
> **melopsittacus said:**
> Hi, I have recently installed Hardy, and I noticed that sometimes sounds just stop working, that is all programs supposed to produce sound output are just mute. (None of them give error messages though.)
If I reboot the machine sound works correctly though. (Sound used to work well in Gutsy.)

As I read in the forums that only one program at a time can use the audio device, I suspect that some other process is actually blocking it.

My question is: how can I find out which program is using or blocking the audio?

My other question: which package is responsible for sound? (In case I'd want to submit a bug report to Launchpad)

The other, smaller problem related to sound is that I never get logout music when turning off the computer. I can live with this however :D

Is this, by any chance, when you are using flash (basically, when you are using firefox, or another web browser)?

If so, please see

[http://ubuntuforums.org/showthread.php?t=808710&highlight=flash](http://ubuntuforums.org/showthread.php?t=808710&highlight=flash)

Good luck!

---

