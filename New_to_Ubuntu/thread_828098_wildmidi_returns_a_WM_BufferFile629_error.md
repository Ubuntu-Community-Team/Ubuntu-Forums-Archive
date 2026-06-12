---
title: "wildmidi returns a WM_BufferFile:629 error"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-06-13
Following the instructions for the WildMidi at:

[http://www.funnestra.org/ubuntu/hardy/](http://www.funnestra.org/ubuntu/hardy/)

I saw about 60 meg downloaded in total including the "high-quality" fonts.

When I ran wildmidi against a .mid file, I got the following:

mark@Lexington-19:~/Music$ wildmidi evita
WildMidi 0.2.2 Open Source Midi Sequencer
Copyright (C) 2001-2004 Chris Ison [email]wildcode@users.sourceforge.net[/email]

WildMidi comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under the terms and conditions of the GNU General Public License version 2.
For more information see COPYING

Initializing Sound System
Initializing WildMidi Processing Library 0.2.2

 +  Volume up       e  Better resampling     n  Next Midi
 -  Volume down     l  Linear volume         q  Quit

libWildMidi(WM_BufferFile:629): ERROR Unable to stat evita (No such file or directory)
      Shutting down Sound System
mark@Lexington-19:~/Music$

Any ideas on what to do?

---

### Post by joshsmith on 2008-06-13
..your link was to a local file

if you isntall the package freepats, you can play midi files in totem just by double clicking

---

### Post by Mark_in_Hollywood on 2008-06-14
Works, sortof.

Clicking a midi file brings up Totem. The "time:" bar moves, no sound, however. I checked the volume control in Totem and the panel volume, too.

---

