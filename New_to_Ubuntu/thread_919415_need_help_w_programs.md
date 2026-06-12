---
title: "need help w/ programs"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by fignig on 2008-09-14
so i'm about to reinstall hardy heron, and i need a few suggestions as to which programs are superior than others such as cd burning, mp3 playing, sound eqalizers if that's possible, and all around favorite programs for all over use. just name your favorite programs for a category, however many, just list!

---

### Post by fignig on 2008-09-14
> **fignig said:**
> so i'm about to reinstall hardy heron, and i need a few suggestions as to which programs are superior than others such as cd burning, mp3 playing, sound eqalizers if that's possible, and all around favorite programs for all over use. just name your favorite programs for a category, however many, just list!

i also need to know how to switch to pulse audio, b/c i hear that's better than alsa.

---

### Post by fignig on 2008-09-14
and i need to know how to setup streaming video players. or what the names of the best ones or the best way to set them up. ty!

---

### Post by SunnyRabbiera on 2008-09-14
CD burning= K3B
MP3= in my opinion I like audacious
for sound equalizing, I am unsure.

---

### Post by fignig on 2008-09-14
btw, is there anyway to run xgl and nvidia x server at the same time? or how to resolve issues w/ them, b/c i wanted to install compiz and run the animations, but in order to do that you have to run xgl, and nvidia x server messed up when i did that and all hell broke loose. so i'm trying to avoid that.

---

### Post by fignig on 2008-09-14
> **SunnyRabbiera said:**
> CD burning= K3B
MP3= in my opinion I like audacious
for sound equalizing, I am unsure.

i wonder if you could have a sound equalizer for the entire system. like a universal one, so the sound is good all the time.

---

### Post by Corin-EU on 2008-09-14
> **fignig said:**
> i also need to know how to switch to pulse audio, b/c i hear that's better than alsa.
ALSA provides the driver interface and also a user interface to the hardware.

Pulse audio is a daemon which sits on top of the sound system.

So in order to use Pulse Audio you still need a hardware drivers (ALSA, or the deprecated OSS as an alternative example).

It is not a case of Pulse Audio being better than ALSA.

It is a case of whether or not you want to use a sound system daemon on top of ALSA, and use that simplified interface rather than the ALSA interface.

In terms of audio quality, it may sometimes be the case that Pulse Audio does not sound as good as if you were using the ALSA output directly.

---

### Post by fignig on 2008-09-14
> **Corin-EU said:**
> ALSA provides the driver interface and also a user interface to the hardware.

Pulse audio is a daemon which sits on top of the sound system.

So in order to use Pulse Audio you still need a hardware drivers (ALSA, or the deprecated OSS as an alternative example).

It is not a case of Pulse Audio being better than ALSA.

It is a case of whether or not you want to use a sound system daemon on top of ALSA, and use that simplified interface rather than the ALSA interface.

In terms of audio quality, it may sometimes be the case that Pulse Audio does not sound as good as if you were using the ALSA output directly.

so are u suggesting that i just stick w/ alsa?

---

### Post by Steveway on 2008-09-14
XGL is discontinued and not needed anymore.
You should be able to just use compiz if you install the restricted drivers.

---

### Post by Joeb454 on 2008-09-14
PulseAudio is installed by default as of Hardy (8.04)

---

### Post by markbuntu on 2008-09-14
Video- vlc

Streaming Radio, Rythmbox, Audacious w/Tunapie, Streamtuner w/xmms. (audacious and xmms have equalizers)

Stream recording -streamripper

Audio Porduction -ardour w/jackd


You can read my guide to get a handle on how sound works in Hardy Heron and how to set it up:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by fignig on 2008-09-15
anyone else?

---

### Post by fignig on 2008-09-16
how about a timer/alarm clock app?

---

