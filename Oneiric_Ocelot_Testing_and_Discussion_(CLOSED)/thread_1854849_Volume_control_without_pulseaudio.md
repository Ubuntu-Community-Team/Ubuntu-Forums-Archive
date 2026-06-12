---
title: "Volume control without pulseaudio"
date: 2011-10-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by foxy123 on 2011-10-05
I have purged pulseaudio because it does not work well with Skype on my laptop. As a result the volume control applet on the panel is also gone. Is it possible to replace it with anything?

---

### Post by Harry33 on 2011-10-05
> **foxy123 said:**
> I have purged pulseaudio because it does not work well with Skype on my laptop. As a result the volume control applet on the panel is also gone. Is it possible to replace it with anything?

If you have alsa-utils installed, try this in terminal:

```
alsamixer
```

> alsa-utils Included tools:
  o amixer: command line mixer
  o alsamixer: curses mixer
  o amidi: read from and write to ALSA RawMIDI ports
  o aplay, arecord: command line playback and recording
  o aplaymidi, arecordmidi: command line MIDI playback and recording
  o aconnect, aseqnet, aseqdump: command line MIDI sequencer control

---

### Post by foxy123 on 2011-10-05
> **Harry33 said:**
> If you have alsa-utils installed, try this in terminal:

```
alsamixer
```

Thanks a lot, I know about it and use alsamixer quite often. I was hoping for something more user friendly for my wife. I wonder if there is a way to out an alternative volume control on the Unity panel. Also I tried gamix and it is a bit messy and gnome-alsamixer does not launch at all.

---

### Post by foxy123 on 2011-10-07
OK, I have just installed XFCE and moved my wife to it.

---

