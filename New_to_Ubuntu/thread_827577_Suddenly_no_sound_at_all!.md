---
title: "Suddenly no sound at all!"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by oldrocker99 on 2008-06-12
I had no problem with sounds until today, when any app that plays sounds I've tried returns:

An error occorred
The audio device is busy. Is another application using it?

I used the PulseAudio installation instructions at

[http://ubuntuforums.org/showthread.php?t=776739&highlight=ekiga+pulseaudio](http://ubuntuforums.org/showthread.php?t=776739&highlight=ekiga+pulseaudio)

but when I try to test the sound in System/Preferences/Sound using PulseAudio, I get

audiotestsrc wave=sine freq=512 ! 
audioconvert ! audioresample ! 
gconfaudiosink: Failed to connect stream: 
Invalid argument

Weirdly enough, I get that sine tone setting the test to Open Sound System, but if I use ALSA I get exactly the same error message. I'm already having to live with the crappy motherboard stereo sound since I have been UNABLE to make the drivers for my X-Fi Extreme Music to work at all, and now to lose all sound is frustrating in the extreme.

Anyone have any ideas? 

:guitar:

---

