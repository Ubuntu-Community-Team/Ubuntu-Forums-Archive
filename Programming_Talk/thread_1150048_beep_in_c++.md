---
title: "beep in c++"
date: 2009-05-05
forum: Programming Talk
---

### Post by marer907 on 2009-05-05
Is there a easy way to get a beep or to play a small soundfile with c++?

I have been searching on google for a answer but haven't found one.

/Martin

---

### Post by benj1 on 2009-05-05
the only way i know for a beep is ncurses

```

#include <ncurses.h>

initscr();
c = getch();
if ( c == KEY_F(1)){ beep();}
endwin();
```

should work i think (you will need to download ncurses, its in the repos)

edit: comile with the -lncurses flag

for a small sound file, have a look at the sdl library

depending on what you want it might just be easiest to use a system call to another program to play the file.

---

### Post by soltanis on 2009-05-05
If the terminal is configured for audible beeps, printing the ASCII 'bell' character ('\a') will elicit a beep in the console. This depends on user-defined settings (other actions can be configured; for example, it might cause the window to "flash", a visual cue, or it might not do anything at all).

If you want to play an actual sound file, you may want to look at how to use Linux sound via ALSA, or use a cross-platform media library, such as SDL.

EDIT.

If you don't want to mess with linux sound, and all you want to do is play a sound through the speakers with no bells or whistles, use the system() function to run a command such as

```

aplay sound_file.wav

```

In the background. You may use other similar command line tools to accomplish the job, and though this is an inefficient method (forking a console, replacing the process image, loading another program, then loading and playing the sound file, then exiting on every call), it will get the job done with minimal code interference.

---

### Post by M4rotku on 2009-05-05
The easiest thing to do is use the '\a' character.

> cout<<"\a";

---

### Post by benj1 on 2009-05-05
cout << "\a";

doh
should have remembered that one.

---

### Post by lensman3 on 2009-05-05
Do a "man ascii" and send the BEL character to the terminal.  Which in C/C++ is '/a' or octal 007.   The BEL character could be a visual bell if the terminal is setup that way.  As per M4rotku.

---

### Post by mkarnicki on 2009-06-11
Thanks, aplay was a really good suggestion.

---

### Post by Krupski on 2009-06-11
> **marer907 said:**
> Is there a easy way to get a beep or to play a small soundfile with c++?

I have been searching on google for a answer but haven't found one.

/Martin

You could open /dev/dsp and write sound data to it.

By default, /dev/dsp is set to 8000 hz, 8 bits signed (i.e. no sound is 0x80 and it ranges from 0x00 to 0xFF).

With system calls, you can change the sample rate, the bit depth, etc...

All you need to figure it all out is right [[COLOR="Blue"]**_HERE_**[/COLOR]]("http://www.oreilly.de/catalog/multilinux/excerpt/ch14-05.htm").

Have fun!

-- Roger

---

