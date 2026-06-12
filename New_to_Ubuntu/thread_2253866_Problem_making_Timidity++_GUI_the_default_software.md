---
title: "Problem making Timidity++ GUI the default software to run MIDI files"
date: 2014-11-23
forum: New to Ubuntu
---

### Post by Dactula on 2014-11-23
Hi,

I am using Ubuntu 14.04. I had installed Timididy++ MIDI sequencer from the Ubuntu Software Center and can still launch it from the DASH to play .RMI & .MID files. Unfortunately I can't make it the default application to open those files which when double clicked launches timidity CLI by default .The music can be heard but no GUI app appears on the desktop. If run I need to hear out the whole file, can't stop it midway. I also used VLC Media Player Fluidsynth codec which works fine but only shows elapsed time not total time or time remaining.

 I just can't find the location of the GUI app Timidity++ though timidity CLI app is shown.Tried Searchmonkey, no luck.

1. Is there a way to locate in which folder Timidity++ GUI software is located and/or make it the default launch application for the MIDI files ?

2. Any way to fix VLC's total time not shown problem?

3. When timidity CLI is running any way to Pause/Stop the playback ?

Thanks in advance

---

### Post by ajgreeny on 2014-11-23
Do you have the package **timidity-interfaces-extra** installed; that may be what you need, then you use timidity with command **timidity -ik** for the gtk interface.

See **man timidity** for the interface options, and choose the command you need according to the interface you prefer.

---

