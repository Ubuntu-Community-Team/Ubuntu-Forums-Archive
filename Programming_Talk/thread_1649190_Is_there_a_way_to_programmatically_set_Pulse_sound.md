---
title: "Is there a way to programmatically set Pulse sound preferences?"
date: 2010-12-19
forum: Programming Talk
---

### Post by mdurham on 2010-12-19
Hi, As the title suggests, I need to set Pulse sound preferences before & after running Skype in order to use my USB phone.
A clue of how to do this (in any language) would be much appreciated.
Thanks, Mike

---

### Post by mdurham on 2010-12-21
anybody know anything about this?

---

### Post by Reiger on 2010-12-21
Well there's pulseaudio-utils which provides a bunch of commandline programs. I imagine you could try catting a bunch of commands and piping those into the STDIN of some pulseaudio util program to get what you want.

---

### Post by kostkon on 2010-12-21
PulseAudio supports input/output devices per application. Just install the *Pulseaudio Volume Control* utility.

---

### Post by mdurham on 2010-12-21
> **kostkon said:**
> PulseAudio supports input/output devices per application. Just install the *Pulseaudio Volume Control* utility.

Thanks for the feedback. Reiger, I'll look into pulseaudio-utils if I can find some documentation for it.

kostkon, I don't see how I do this with audio-out. I can do it with audio-in (usb microphone), but do you have any idea how I do it with the out (usb phone speaker) side of things? I can switch ALL sound out to the usb phone, but that's not what I want.
It seems a bit odd to be able to do it with one and not the other. Help!

Cheers, Mike

---

