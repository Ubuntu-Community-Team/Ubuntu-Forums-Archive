---
title: "Sound Question regarding Alsa + Amarok."
date: 2008-08-02
forum: New to Ubuntu
---

### Post by Roasted on 2008-08-02
Sys - Pref - Sounds = everything Alsa.
Amarok = Alsa.

With this setup, YouTube + Amarok won't play at the same time. In fact, if I just got done watching a YouTube video, I have to reload firefox for Amarok to kick on without complaining. No big deal, saves my tabs, just gotta ALT F4 to close and F4 (assigned shortcut) to reopen.

Then...

Sys - Pref - Sounds = Everything Alsa.
Amarok = Auto Detect.

YouTube + Amarok works...

What audio pipeline is Amarok using to run if YouTube is using Alsa?

---

### Post by billgoldberg on 2008-08-02
> **Roasted said:**
> Sys - Pref - Sounds = everything Alsa.
Amarok = Alsa.

With this setup, YouTube + Amarok won't play at the same time. In fact, if I just got done watching a YouTube video, I have to reload firefox for Amarok to kick on without complaining. No big deal, saves my tabs, just gotta ALT F4 to close and F4 (assigned shortcut) to reopen.

Then...

Sys - Pref - Sounds = Everything Alsa.
Amarok = Auto Detect.

YouTube + Amarok works...

What audio pipeline is Amarok using to run if YouTube is using Alsa?

Try removing pulseaudio from your system.

```
sudo apt-get autoremove pulseaudio --purge
```

should do it.

--

I did it and have no problem playing multiple audio files at once.

I haven't done so with flash and amarok. But I tried with flash + banshee, exaile, bmpx, decibel, sonata, mpc, vlc, totem, mplayer and gxine.

---

### Post by Roasted on 2008-08-02
Didn't work.

Using Amarok (set to Alsa) and Flash, only one can play.

If Amarok is set to Auto Detect, both can play.

But I'm curious to know how that works... what is Amarok using to play??

---

