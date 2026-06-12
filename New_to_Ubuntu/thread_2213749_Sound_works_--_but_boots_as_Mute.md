---
title: "Sound works -- but boots as Mute"
date: 2014-03-28
forum: New to Ubuntu
---

### Post by zaivala on 2014-03-28
I'm sure someone has an easy fix for this. In fact, I'm sure I posted this a couple days ago, but the Forum seems to have lost it.

I'm running Precise Pangolin, plain vanilla form, on a Dell Optiplex 740.

I've squashed all the problems I have except two, and one is the subject of another thread.  Here's the other:

When I boot, my sound is set to Mute. I have to open System Setting - Sound and unclick the box every time.

What do I do to change this behavior?

---

### Post by MikRose on 2014-03-29
Type in terminal: pulseaudio -k && sudo alsa force-reload 
The first kills pulseaudio, the second reloads ALSA. You don't need to restart pulseaudio, because it auto-restarts.

---

### Post by zaivala on 2014-03-29
> **MikRose said:**
> Type in terminal: pulseaudio -k && sudo alsa force-reload 
The first kills pulseaudio, the second reloads ALSA. You don't need to restart pulseaudio, because it auto-restarts.

zaivala@zaivala-desktop:~$ pulseaudio -k && sudo alsa force-reload 
[sudo] password for zaivala: 
Unloading ALSA sound driver modules: snd-hda-codec-idt snd-usb-audio snd-usbmidi-lib snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-idt snd-usb-audio snd-usbmidi-lib snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-rawmidi snd-timer snd-seq-device snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-codec-idt snd-usb-audio snd-usbmidi-lib snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
zaivala@zaivala-desktop:~$ 

I did it, it ran... have to reboot to learn if it worked... I opened my Sound box and Mute was still checked...

Thanks for your help, hope it works.

Edited to add: Nope. No luck.

---

### Post by MikRose on 2014-03-31
Rat manure...I'm still thinking!

---

### Post by zaivala on 2014-04-12
Bump. Still an issue. But I don't have to go to settings, I can click the mute speaker at the top...

---

### Post by coldraven on 2014-04-13
Would it be something to do with the power management settings?
On my laptop if I boot up on battery power the sound is auto-muted.

---

### Post by zaivala on 2014-04-13
Shouldn't be. This is a desktop. But I'll check.

---

