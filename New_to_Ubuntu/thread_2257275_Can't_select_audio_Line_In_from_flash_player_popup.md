---
title: "Can't select audio Line In from flash player popup in firefox"
date: 2014-12-18
forum: New to Ubuntu
---

### Post by Alex_Bunt on 2014-12-18
I have a microphone plugged into a line in port on my linux machine. I can record in audacity and in the sound options it's detecting sound, but whenever I try to record sound in firefox nothing is detected in the flash player popup - only HDA intel.

Thank you,
Alex

---

### Post by ajgreeny on 2014-12-18
You have lost me.

Why a microphone plugged into a line-in port; why not into the microphone port?

Also why are you trying to record sound from a flash sound output with a microphone; that makes no sense at all. You need to set the sound-settings to use the sound card output for the recording.

Have a look at audio-recorder for simple recordings like that; it is so much simpler than audacity.
[https://launchpad.net/~osmoma/+archive/ubuntu/audio-recorder](https://launchpad.net/~osmoma/+archive/ubuntu/audio-recorder)

---

### Post by llamabr on 2014-12-19
Also, it would depend on the website.  What is an example of a website which is not accepting your audio input?

---

### Post by Yellow Pasque on 2014-12-19
> only HDA intel.

If you're using onboard sound, then that probably is your audio device.

---

