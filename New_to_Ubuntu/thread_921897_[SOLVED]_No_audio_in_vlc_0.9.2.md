---
title: "[SOLVED] No audio in vlc 0.9.2"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by t0p on 2008-09-16
I just installed vlc 0.9.2 following the instructions [here]("http://blog.jetienne.com/2008/09/vlc-092-on-ubuntu-804.html").  But there's no audio!

The audio works fine in my other music and video players.  So this is a vlc 0.9.2-specific problem, it would appear.  Anyone got any ideas what to do?

**EDIT:** The audio is not muted, and the volume is turned up.  But no sound! :(

---

### Post by shadowber on 2008-09-16
I had the same problem, but it started working when I reinstalled it... I am having a different problem though...... There's a green bar going down the screen about a quarter from the left, and I haven't the foggiest how to get rid of it... help!?!?

---

### Post by Tatty on 2008-09-16
Try going to Settings->Preferences->Audio->Output Modules,  then select the "Advanced Options" option.

Change the Audio Output Module to "ALSA audio output".

---

### Post by t0p on 2008-09-17
Okay, I got the audio working.

I went to **Tools > Preferences > Audio** and changed **Output Type** to ALSA, as recommended by Tatty.  No good.  I tried the other output types, and when I tried **Pulseaudio** it worked!!  *Frabjous day!!  Callooo!! Callay!!*

What I find strange is:  audio was originally set to Default.  As my system's default audio mode is Pulseaudio, why didn't it work then??

---

### Post by yellowbean on 2008-09-22
> Okay, I got the audio working.

I went to Tools > Preferences > Audio and changed Output Type to ALSA, as recommended by Tatty. No good. I tried the other output types, and when I tried Pulseaudio it worked!! Frabjous day!! Callooo!! Callay!!

What I find strange is: audio was originally set to Default. As my system's default audio mode is Pulseaudio, why didn't it work then??

I have the same problem (will have to test your fix when I get home from work). So far yours is the first post I've found on this issue. I don't get why it didn't pick up our default audio mode and why there aren't more people with this issue.

---

