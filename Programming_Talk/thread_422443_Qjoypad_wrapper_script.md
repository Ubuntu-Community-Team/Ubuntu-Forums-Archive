---
title: "Qjoypad wrapper script"
date: 2007-04-25
forum: Programming Talk
---

### Post by kingmob on 2007-04-25
I'm working on controlling mythtv and all its plugins with a gamepad.

Controlling mythtv with a gamepad works fine with builtin options, but i want more (ofcourse). The problem is that it will 'remember' the settings and so i cannot use my settings for mplayer when playing a movie, or for the various emulators i have setup.
Now in [this ](http://www.mythtv.org/wiki/index.php/Configuring_MythGame_Emulation#QJoyPad) mythgame howto Qjoypad is used and that is what i am using now. The program works excellent and i am able to create several layouts, so that mythtv, mplayer and all the emulators all have different kind of setups. The problem is that the howto talks about creating wrapper scripts, but that i have no idea how to create those myself.
I suspect it is very easy, so i hope someone can help me.

I now have this, based on the scummvm wrapper script. Here i try to create a script that will work just like
```

mplayer %s

``` in mythtv, but also loads a different gamepad layout. 

```

#!/bin/sh
/usr/local/bin/qjoypad --notray mplayer &
/usr/bin/mplayer -quiet $1 

```
(the "mplayer" in the first line is a layout name, not the program)
It seems to work for files without spaces, how do i get it to work normally for all files?

---

### Post by kingmob on 2007-04-25
I cannot test this out now, but would replacing $1 with $@ solve it?

---

### Post by WW on 2007-04-25
Try putting quotes around $1; i.e. replace $1 with "$1"

---

### Post by kingmob on 2007-04-25
I had already tried that, but that doesn't work. It only sees the first part of the filename as $1. 
I think $@ will work.

---

