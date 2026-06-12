---
title: "Clear Screen(Python)"
date: 2007-10-31
forum: Programming Talk
---

### Post by Spike_UK on 2007-10-31
Afternoon People 

A question i have is if you have a menu like below: 

1. Hangman 
2. Packman 
3. Quit 

If you pressed how would you clear the screen and ran the hangman or packman on a clear screen 

Many Thanks

---

### Post by ghostdog74 on 2007-10-31
make a call to the clear command , using os.system() or equivalent
eg
os.system("clear")
or 
print many newlines until it fills the screen

eg
for n in range(128):
    print

---

### Post by dataw0lf on 2007-10-31
Or, use curses:
```

from sys import stdout
import curses
curses.setupterm()
stdout.write(curses.tigetstr("clear"))
stdout.flush()
```

---

