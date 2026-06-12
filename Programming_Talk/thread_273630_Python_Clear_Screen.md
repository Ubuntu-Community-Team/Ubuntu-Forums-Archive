---
title: "Python Clear Screen"
date: 2006-10-08
forum: Programming Talk
---

### Post by thomasaaron on 2006-10-08
Other than defining a function that creates a crapload of carriage returns, is there a command to clear the screen in idle?

i.e. the equivalent of 'clear' in BASH?

I've googled it and checked several other forums, and I'm finding nothing helpful.

ALSO,

If I have to use the crapload of carriage returns method, is there a way to move the cursor back up to the top of the screen?

---

### Post by duff on 2006-10-08
> **thomasaaron said:**
> Other than defining a function that creates a crapload of carriage returns, is there a command to clear the screen in idle?

i.e. the equivalent of 'clear' in BASH?

I've googled it and checked several other forums, and I'm finding nothing helpful.

you can just use "clear"

import os
os.system("clear")

---

### Post by thomasaaron on 2006-10-08
I've tried that.
It just keeps returning "256"

---

### Post by duff on 2006-10-08
It may be an issue with idle then.  Try running your program from a a standard terminal.

---

### Post by thomasaaron on 2006-10-08
OK. That worked.
Thank you.
T

---

### Post by rebelDNS on 2008-12-22
In interactive mode can hit ^l (Ctrl+l) and it will do the exact same thing as clear does in bash.


Ctrl-A : go to line start
Ctrl-E : go to line end
Ctrl-K : clear line from cursor to end
Ctrl-L : clear

(These for for both lower and upper cases)

---

### Post by nvteighen on 2008-12-22
Keep in mind that "clear" will just output the sufficient whitespace needed to get the next line printed at the uppermost line.

If you want to clear the screen completely (at least during your script's execution), you'll need ncurses.

---

### Post by namegame on 2008-12-22
The necromancers are strong in this thread.

---

### Post by fiddler616 on 2008-12-22
> **namegame said:**
> The necromancers are strong in this thread.
And yet two years later the OP still hasn't marked it as solved...lame.

---

### Post by nvteighen on 2008-12-22
> **namegame said:**
> The necromancers are strong in this thread.
:p I just noticed that this thread was 2 years old...

---

### Post by fiddler616 on 2008-12-22
Well, I'm just as glad it came up since I learned something from it.

---

### Post by Swenghk on 2009-04-16
How do you use ncurses? Is that some command?

---

### Post by sujoy on 2009-04-16
> **Swenghk said:**
> How do you use ncurses? Is that some command?

a library rather,
see [here]("http://docs.python.org/library/curses.html")

---

### Post by nvteighen on 2009-04-16
> **Swenghk said:**
> How do you use ncurses? Is that some command?
It's a library used for character-based terminal handling written for C, though happily we've got a module for Python. Just do **import curses** and follow the link sujoy gave you.

The issue with ncurses ("New Curses") is that it has to comply to the old original "Curses" standard and therefore, uses a really outdated design. For example, it relies a lot on hidden global variables. The Python module is able to manage this in a better way, by encapsulating those "globals" into the "curses" namespace (Is that what a singleton is called?? I checked the Wikipedia and so it seems to me... :p), but if you in a future are forced to use the "real" C ncurses, you'll see what I mean...

...but, unfortunately, ncurses is the only library that does this kind of job and we have to live with it unless someone of us is clever enough (and not lazy) to develop a better library :)

---

### Post by ki4jgt on 2011-03-11
Not really solved. . . He asked for something which didn't put out a crap load of carriage returns. . . os.system("clear") does return a crapload of carriage returns. Is there anything which doesn't?
Sorry LOL didn't see the second page. . . I feel dumb :-(

---

