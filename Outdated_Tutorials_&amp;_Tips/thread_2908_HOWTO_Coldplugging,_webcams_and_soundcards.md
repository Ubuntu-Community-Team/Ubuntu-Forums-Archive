---
title: "HOWTO: Coldplugging, webcams and soundcards"
date: 2004-11-01
forum: Outdated Tutorials &amp; Tips
---

### Post by Pustulo on 2004-11-01
I thought that I would share a solution to a problem that plagued me for a few nights during my ongoing migration to Ubuntu.

:confused: _The problem:_ 
The integrated soundcard on the motherboard does not appear to work under Gnome.

:neutral: _Observations:_ 
'dmesg' reveals the built-in soundcard is actually detected at one point in the boot process

The volume control applet shows multiple soundcards, the first of which only has one channel - a microphone.  The second, appears to be the real card.

Despite gdm startup sound, the gnome session does not use the real soundcard.

:idea: _Hypothesis:_ 
Hotplug system is configuring the webcam's sound capabilities before the motherboard's integrated soundcard.  The order of detection dictates which sound device the gnome session uses as it's sound output device.

:D _Solution:_
```

# /etc/modules: kernel modules to load at boot time.
#
# This file should contain the names of kernel modules that are
# to be loaded at boot time, one per line.  Comments begin with
# a "#", and everything on the line after them are ignored.

```

Append the name of the integrated soundcard's driver to the /etc/modules file.
e.g.  ```
# echo snd_intel8x0 >> /etc/modules
```

Hope this helps.

N.B.  This is not a problem specific to Ubuntu.  In fact, I encountered the same problem under RH9 (which I am migrating from).  My solution for that installation was to use the hotplug blacklist, although I find that answer awfully kludgy.

Colin.

---

