---
title: "How can I use konsole for output in Qt Creator?"
date: 2011-09-27
forum: Programming Talk
---

### Post by simpleblue on 2011-09-27
Currently when I compile and run a C++ program in Qt Creator it runs in xterm. I'd prefer the output be in konsole if possible. I like the way I can customize konsole, and the font in xterm is too small for me. I strain just to read it.

I have already searched the net for a solution and have seen bug reports pertaining to konsole not being able to be called to run programs but it just doesn't seem believable to me.

---

### Post by gmargo on 2011-09-27
Should be settable on the options page (at least on v2.0.1 from 10.10 Maverick)

Tools -> Options -> Environment -> General -> System -> Terminal

Change "x-terminal-emulator -e" (or perhaps you have "xterm -e") to "konsole -e".

(note: untested)

---

### Post by simpleblue on 2011-09-27
> **gmargo said:**
> Should be settable on the options page (at least on v2.0.1 from 10.10 Maverick)

Tools -> Options -> Environment -> General -> System -> Terminal

Change "x-terminal-emulator -e" (or perhaps you have "xterm -e") to "konsole -e".

(note: untested)

I put 'konsole -e' in the settings and it brings up a blank terminal.

---

### Post by Vaphell on 2011-09-27
xterm is fugly as hell but if you really have to use that you can increase the font size
just pick one of the least ugly fonts from the list that xlsfonts command gives you, eg.
```
xterm -bg black -fg white -fn lucidasanstypewriter-bold-12
```
bg and fg set colors, fn is fontname

---

### Post by simpleblue on 2011-09-28
> **Vaphell said:**
> xterm is fugly as hell but if you really have to use that you can increase the font size
just pick one of the least ugly fonts from the list that xlsfonts command gives you, eg.
```
xterm -bg black -fg white -fn lucidasanstypewriter-bold-12
```bg and fg set colors, fn is fontname
While this did not work it did set me in the right direction and I got it fixed by typing:

```
xterm -fa "dejavu sans mono" -e
```The strange part is that the '-fa "dejavu sans mono" needs to be inserted before the '-e' or it does not change the font.

Everything is fine now. Thanks. Time to start programming.

:popcorn:

---

