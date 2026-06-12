---
title: "os.system(&quot;clear&quot;) and IDLE"
date: 2010-12-19
forum: Programming Talk
---

### Post by ki4jgt on 2010-12-19
Why does os.system("clear") not work in IDLE

---

### Post by rex_virtutis on 2010-12-19
I believe that os.system() opens a new shell each time it is called. This is why the shell doesn't retain it's state between calls to os.system() to see this in action try this. 
```

import os
os.system("export MYVAR=3")
os.system("echo $MYVAR")

```

---

### Post by ki4jgt on 2010-12-19
Is there a way to clear the screen without opening a new shell?

---

### Post by ki4jgt on 2010-12-19
```

V = 2011
os.system("clear")
print V

```

works fine in Gnome Terminal but IDLE doesn't clear screen. Just as long as I can clear the screen and keep the variables which have been previously defined, that's what I wanted.

---

### Post by Queue29 on 2010-12-19
> Is there a way to clear the screen without opening a new shell? 

You'll need to use the ncurses library:
[http://docs.python.org/library/curses.html](http://docs.python.org/library/curses.html)

Or, just make a function that prints a bunch of carriage returns:

```

def clearscrn():
    print("\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n")

```

Which is no where near as elegant (and doesn't truly clear the screen), but is much less complicated than using the library.

---

### Post by trent.josephsen on 2010-12-19
Don't use IDLE to run programs, especially terminal programs.  IDLE isn't a terminal and doesn't handle escapes properly.  Run your programs in xterm or some other terminal emulator of your choice.

---

### Post by ki4jgt on 2010-12-19
> **Queue29 said:**
> You'll need to use the ncurses library:
[http://docs.python.org/library/curses.html](http://docs.python.org/library/curses.html)

Or, just make a function that prints a bunch of carriage returns:

```

def clearscrn():
    print("\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n")

```

Which is no where near as elegant (and doesn't truly clear the screen), but is much less complicated than using the library.

Might as well use os.system it pretty much does the same thing as \n\n\n. . . without having to print. May look into the library, but would rather do os.system than to \n\n\n\n\n\n\n\n\n\n\n every time I needed to cls.

---

### Post by wmcbrine on 2010-12-20
Using os.system("clear") is *not* equivalent to printing out a bunch of '\n' -- not in effect, but especially not in overhead.

A closer (and shorter) equivalent to the behavior of "clear" would be:

```
import sys
sys.stdout.write('\x1b[2J\x1b[H')
```

but whether or not those are the right codes depends on the terminal type. It will work in most of the ones you're likely to encounter, anyway. (I used sys.stdout.write here instead of print merely to suppress the trailing newline.)

The right way to do it is to import curses, but using curses means adopting a whole new system for input and output.

---

### Post by ki4jgt on 2010-12-20
> **wmcbrine said:**
> Using os.system("clear") is *not* equivalent to printing out a bunch of '\n' -- not in effect, but especially not in overhead.

A closer (and shorter) equivalent to the behavior of "clear" would be:

```
import sys
sys.stdout.write('\x1b[2J\x1b[H')
```

but whether or not those are the right codes depends on the terminal type. It will work in most of the ones you're likely to encounter, anyway. (I used sys.stdout.write here instead of print merely to suppress the trailing newline.)

The right way to do it is to import curses, but using curses means adopting a whole new system for input and output.

OMGoodness :-) don't want to complain, (MUCH:-) ) but Just came from a Windows version of BASIC which simply used cls to clear the screen. There's no simpler way of clearing screen? I mean isn't Python supposed to be top of the line, I've had everyone tell me to stop coding in BASIC and how bad it was, they all reccomended me to Python and then I find out I can't even erase the screen :-O AAAAAHHHHHHHHHHHHHHHHHH!!!!

Rant finished LOL :-) I'm happy again :P

Thanks guys

---

### Post by bouncingwilf on 2010-12-20
In the old days we used to just send the escape code for whatever type of term the terminal was emulating or just issue a clear command ( clear is available at the terminal promt).

Sorry if I'm 100 years out of date but this never used to be an issue.


Bouncingwilf

---

### Post by wmcbrine on 2010-12-20
> **ki4jgt said:**
> Just came from a Windows version of BASIC which simply used cls to clear the screen. There's no simpler way of clearing screen?Your BASIC had a "CLS" because it was platform-specific. Python has no concept of a "screen", because it's written in (and to some extent, based on) portable C, which also has no such concept. Instead, they operate on stdin and  stdout (and stderr).

It's really not a big deal. Most programs don't get fancy with the terminal these days -- it's either a simple text dump, or full GUI. But if you *do* want to get fancy with the terminal, you use curses.

> **bouncingwilf said:**
> In the old days we used to just send the escape code for whatever type of term the terminal was emulatingI posted the escape sequence version in #8, if you'll notice. Of course, I didn't do a lookup, because I was trying to keep it simple... and because almost every terminal used these days is ANSI/VT100-compatible.

> *or just issue a clear command ( clear is available at the terminal promt).*That's how the thread started. That's what os.system("clear") *is*.

If you're working at the prompt, or writing a shell script where every step is calling an external program, then "clear" is more of the same, and it makes sense to use it. But Python, despite being called a "scripting language", is not oriented to running external programs the way the shell is -- you can do it, but it's less elegant, and less necessary. Most of the work in an average Python program is likely to be done internally. In that context, calling "clear" seems like overkill.

---

### Post by ki4jgt on 2010-12-21
> **bouncingwilf said:**
> In the old days we used to just send the escape code for whatever type of term the terminal was emulating or just issue a clear command ( clear is available at the terminal promt).

Sorry if I'm 100 years out of date but this never used to be an issue.


Bouncingwilf

I like old, it's better than new. :-) New just seems to skip things which old has already covered a million times before, but without new, there's no expansion.

---

### Post by ki4jgt on 2010-12-21
> **wmcbrine said:**
> .If you're working at the prompt, or writing a shell script where every step is calling an external program, then "clear" is more of the same, and it makes sense to use it. But Python, despite being called a "scripting language", is not oriented to running external programs the way the shell is -- you can do it, but it's less elegant, and less necessary. Most of the work in an average Python program is likely to be done internally. In that context, calling "clear" seems like overkill.

I'm more or less making the program terminal based like this [http://www.smashindex.com](http://www.smashindex.com) (SmashIndex Logger) run the exe from inside the main folder. Know this doesn't mean much but got an award from some kind of software company (Think it was Softpedia) for being virus and malware free. A lot of my users have ask me to stop using BASIC and move to Python. I don't know where to start really b/c BASIC's tutorial was included in the help file for the program it covered every function almost. Python's included documentation doesn't build on what the person knows it just shows you what all is available. I've read about three tutorials on Python and none of them go any farther into the language than If and while statements.

---

