---
title: "what is the point of pulseaudio?"
date: 2009-11-19
forum: Recurring Discussions
---

### Post by nerdy_kid on 2009-11-19
hi all, i just increased a pcs performance by 200% by removing pulse.  I discovered that i can still use more then one app at a time, i can listen to music of firefox and use skype at the same time.  i always thought pulseaudio allowed more then one app at a time to use sound.

what does pulseaudio do???

---

### Post by phrostbyte on 2009-11-19
Break your audio. :p

But seriously Pulse shouldn't be taking much resources, usually for me it idles around ~1.2MB of RAM and no CPU. When playing music it goes up to ~1.4MB and 1-2% CPU.

They use pulse on cell phones. It's not exactly resource intensive. Pulse has a better mixer then ALSA (dmix), that lets you change the volume of any app playing audio. It also is network transparent, meaning you can play music from a computer and the sound could come out of another computer's speakers.

---

### Post by Regenweald on 2009-11-19
> **nerdy_kid said:**
> hi all, i just increased a pcs performance by 200% by removing pulse.  I discovered that i can still use more then one app at a time, i can listen to music of firefox and use skype at the same time.  i always thought pulseaudio allowed more then one app at a time to use sound.

what does pulseaudio do???

I do all that *with* pulseaudio. I can also individually manage sound in each app I have open, and thanks to pskye83, I now have a system wide 15band equalizer. How 'bout that ?

---

### Post by nerdy_kid on 2009-11-19
hmm yeah the networking stuff is really cool, i will say that.  I was working on a pc for a friend (old pc 1.5Ghz) when i logged on to skype and made a call pulseaudio was using 20% CPU, which renders his webcam useless as there is not enough CPU.  Ive tried the network thing with jaunty as server and karmic as client and the server (jaunty) would freeze solid (a push the button until it shuts off kinda freeze) as soon as karmic tried to access it.

As for the EQ -- i want it!!!! ill google around and find out how to do it...

---

### Post by DoktorSeven on 2009-11-20
> **Regenweald said:**
> I can also individually manage sound in each app I have open

I can do that using each of the applications I have open that make sound.  Any application that makes sound but cannot adjust its own volume is worthless.

---

### Post by RedSingularity on 2009-11-20
It also gives your sound card ability to play multiple streams of audio.  Without it you would only be able to listen to one application/media at a time.

---

### Post by nerdy_kid on 2009-11-20
> It also gives your sound card ability to play multiple streams of audio. Without it you would only be able to listen to one application/media at a time.


i removed pulseaudio and that functionality has not been removed...

---

### Post by RedSingularity on 2009-11-20
> **nerdy_kid said:**
> i removed pulseaudio and that functionality has not been removed...


Interesting......i removed it on mine but then i was only able to play one audio at a time.  Do you have 2 sound cards.?

---

### Post by SunnyRabbiera on 2009-11-21
Pulse is there to patch up weaknesses in the other sound systems, like multi sound support.

---

### Post by jdayrutherord on 2009-11-22
I upgraded to 9.10. Since then I have had problems with
memory slowly (over a few hours) being gobbled up until
the entire 4GB is in use according to the system
monitor. It seems the main culprit is pulseaudio. Even when not
playing music its ram usage grows. After 30 Minutes its
at about 450mb and just continues to grow. I have not
tried removing it yet. Audio does seem to work fine under
9.10.

Has anyone on 9.10 seen this? I am running it on a system76
laptop with 4gb of ram.

---

### Post by Psumi on 2009-11-23
The point of pulse is that it runs excellent on my machine. I had to tweak OSS a lot just to get noise from the input on the front off, among other volume changes, whereas in pulse, I have just to unmute some things, and then turn up the volume, then save the settings, then I'm good until the next release of Ubuntu.

Also, Sound Preferences no longer allows you to choose your sound base. Because ubuntu wants ALSA/Pulse for good.

---

