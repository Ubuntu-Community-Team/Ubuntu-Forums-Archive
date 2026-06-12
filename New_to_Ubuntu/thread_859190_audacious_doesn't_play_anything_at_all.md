---
title: "audacious doesn't play anything at all"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by elliah on 2008-07-14
i was looking for a lightweight music player for use on xubuntu and found good reviews for audacious but i can't get it to play anything.
i have the audacious plugins installed.

---

### Post by cotcot on 2008-07-14
Have you installed enough codecs ?
```
sudo apt-get install xubuntu-restricted-extras
```

---

### Post by spydon on 2008-07-14
In which format is the file you are trying to play?

---

### Post by Andifferous on 2008-07-14
I have had the same problem. I have installed the w32codecs, and the xubuntu-restricted-extras packages. I try to play ogg, mp3, or flac and no sound comes out. Flac and ogg file types display the track information in the main player window. mp3 files do not. (just shows 0:00.

---

### Post by BGFG on 2008-07-14
Does your system have both ALSA and PULSEAUDIO ? 
Check your preferences, In the audio tab try adjusting your
'Current Output Plugin' and your 'Output bit depth'

I just changed my output bit depth form 16 to 24 and got the same problem. On my system my output plugin is PulesAudio and my output bit depth is 16. But Alsa works also.

---

### Post by Andifferous on 2008-07-14
Oh boy do I feel silly. It was set on PulseAudio, and changing it to ALSA fixed it, now it plays all 3 formats and displays the information properly.
Thanks

---

### Post by BGFG on 2008-07-14
No problem man... I personally prefer using pulse (richer sound) you can check out this thread if you like, to get optimimum PulseAudio response. I only really used option 'a' and now my sound is great.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by elliah on 2008-07-15
yep...that solved my problem too...thanks

---

