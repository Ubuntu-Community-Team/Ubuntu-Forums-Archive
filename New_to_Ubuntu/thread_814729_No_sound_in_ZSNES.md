---
title: "No sound in ZSNES"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by Famicommander on 2008-06-01
My copy of Lufia II for SNES broke, and as it's a very expensive game I figured it would save me a lot of time and trouble to emulate it. The problem is, I don't seem to be getting any sound. Here is the output:
```
jason@jason-desktop:~$ zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.

Audio Opened.
Driver: Advanced Linux Sound Architecture (ALSA) output
Channels: 2
Rate: 32000

Device 0 HID 6666:0667
  4 axis, 16 buttons, 0 hats, 0 balls

```

Any ideas?

---

### Post by Famicommander on 2008-06-01
I probably should have mentioned that I'm running Xubuntu 8.04 Hardy Heron.

---

### Post by doorknob60 on 2008-06-01
I don't have zsnes on this computer, so I can't tell you if this will work for sure, but I can figure it out. Try starting zsnes with this command:
```
zsnes -ad:sdl
```

If that gives an error, post this because I probably gave the wrong command :P
```
zsnes --help
```

---

### Post by angry_johnnie on 2008-06-01
I'd been cursing Zsnes, too, until I found [this]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=649678").

Sound isn't very good, though, but there's sound, at least. :-)

Edit:  that's post #8 you want to be looking at.

---

### Post by Famicommander on 2008-06-01
> **angry_johnnie said:**
> I'd been cursing Zsnes, too, until I found [this]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=649678").

Sound isn't very good, though, but there's sound, at least. :-)

Edit:  that's post #8 you want to be looking at.

That's even worse than having no sound... The sound track is one of this game's best features, and I need to have full quality.

---

### Post by SunnyRabbiera on 2008-06-01
> **Famicommander said:**
> That's even worse than having no sound... The sound track is one of this game's best features, and I need to have full quality.

you may want to play around with Zsnes's sound settings, I had to play around a bit with sound before I got it where I wanted it.
You do know how to edit the sound in zsnes right?

---

