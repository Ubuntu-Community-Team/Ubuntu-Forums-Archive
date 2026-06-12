---
title: "ALSA does not work but OSS works"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by edwinlin88 on 2008-11-16
Hi guys,

Just wondering why I cant seem to choose HDA Intel ALC885 ALSA device for sound playback (as in I can select it doesnt work (no sound)). I am using HDA Intel ALC885 Analog OSS and sound works but the quality is very bad. My sound card is onboard Realtek ALC889a but I also have a Sounblaster Live5.1 installed in a PCi slot. Also why can't I use digital device? The analog sound really is horrible.
Hope someone can enlighten me.

Thanks!

---

### Post by SunnyRabbiera on 2008-11-16
did you try pulseaudio?

---

### Post by edwinlin88 on 2008-11-16
Yes I tried Pulse Audio Sound Server but no sound with that.

---

### Post by SunnyRabbiera on 2008-11-16
> **edwinlin88 said:**
> Yes I tried Pulse Audio Sound Server but no sound with that.

did you switch to alsa and then log out?
when you switch sound servers lit that you devote your audio device to that sound server and sometimes it wont work unless you log out or restart.
Try log out first though.
But did alsa work before might I ask?
were you running multiple sound applications at the same time?

---

### Post by edwinlin88 on 2008-11-16
I tried to switch to alsa then restarted my computer but still no sound. When I try to test sound with alsa selected, I get the error "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback."

I believe Alsa did work before I installed my Soundblaster and the drivers.  

I was not running multiple sound apps at the same time.

---

### Post by edwinlin88 on 2008-11-16
I have discovered in alsamixer, it says my card and chip is PulseAudio. Is this related to my problem?

---

