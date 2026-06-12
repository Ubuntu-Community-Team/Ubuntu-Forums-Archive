---
title: "Here's an INKEY$ equivalent for Python!"
date: 2007-02-13
forum: Programming Talk
---

### Post by thomasaaron on 2007-02-13
Hello, all.

Occasionally, folks familiar with old BASIC programming come around and ask if Python has an equivalent to BASIC's inkey$ command, which was used in text-mode programs to detect keystrokes.

Python, it seems never included an equivalent, as it's not really geared towards text-mode programming. (Python does have curses, but that is more complicated than the old text-mode programming I'm referring to.)

Now that I've gotten to be a decent python programmer, I do everything in GUI (and curses if I REALLY want text mode badly). But it's always ticked me off that Python didn't include the equivalent of inkey$.  Seems like it would have been simple enough to do. So, just so I could get over being irritated about it, I just finished writing a module to emulate inkey$.

All you have to do is put the attached module (inkey.py) in your home directory (or some other directory in python's search path), import it (import inkey), and then call it with something like keystroke = inkey.inkey()

Also attached is inkeyDemo.py which will demonstrate how it works.

Two notes:
1. This will NOT work via IDLE. It only works in the terminal or in a terminal emulator.
2. The module works because it creates and executes a BASH script that does the work. Therefore, it will only work on a linux system equipped with the BASH shell. (And maybe other shell variants, but I don't know for sure).

---

### Post by po0f on 2007-02-14
thomasaaron,

Is [this](http://effbot.org/pyfaq/how-do-i-get-a-single-keypress-at-a-time.htm) what you're talking about?  I've never used BASIC before, so I don't know what inkey$ does exactly.

---

### Post by thomasaaron on 2007-02-14
Yes, it appears that this is also a way to trap keystrokes.

But like every other way I've seen thus far, it is way more complicated and 'round-about' than BASIC's inkey$ command.

With my module, all you have to do is type:

keystroke = inkey.inkey()

I guess you could put together a similar module with the code you linked to. And it might operate better on other platforms too.

Best,
Tom Aaron

---

### Post by bunabattoir on 2007-02-14
What was wrong with raw_input() built-in function?

---

### Post by thomasaaron on 2007-02-14
Raw_input forces you to press enter.
Inkey$ allows you to just press one key.

---

### Post by johhnygat on 2012-05-23
The thing is tho, that while all these things provide the ability to read just
one char from the keyboard without pressing enter, they do not however
keep the program from waiting for the user to press a key.  I used inkey$
because it did not stop the program if the user did not enter a key, so i could
use it like this:

```

while 1
    x$ = inkey$
    if(x$ = "w") then move_forward()
    elif(a$ = "s") then move_backward()
    elif(a$ = "a") then move_left()
    elif(a$ = "d") then move_right()
    update_screen()
wend

```

As you can see, if the program paused for one key every time the call to inkey$
was made, the screen would only be updated every time you pressed the key.
And then what of the missile that is supposed to be barrelling down on the player's
ship?  Until you press a key, the missile will appear to be suspended in midair.  Time stops for you, when it should stop for no man!

inkey is useful because it checks for keyboard input without
stopping if there is none.

---

### Post by Tony Flury on 2012-05-24
> **thomasaaron said:**
> Hello, all.

Occasionally, folks familiar with old BASIC programming come around and ask if Python has an equivalent to BASIC's inkey$ command, which was used in text-mode programs to detect keystrokes.

Python, it seems never included an equivalent, as it's not really geared towards text-mode programming. (Python does have curses, but that is more complicated than the old text-mode programming I'm referring to.)

Now that I've gotten to be a decent python programmer, I do everything in GUI (and curses if I REALLY want text mode badly). But it's always ticked me off that Python didn't include the equivalent of inkey$.  Seems like it would have been simple enough to do. So, just so I could get over being irritated about it, I just finished writing a module to emulate inkey$.

All you have to do is put the attached module (inkey.py) in your home directory (or some other directory in python's search path), import it (import inkey), and then call it with something like keystroke = inkey.inkey()

Also attached is inkeyDemo.py which will demonstrate how it works.

Two notes:
1. This will NOT work via IDLE. It only works in the terminal or in a terminal emulator.
2. The module works because it creates and executes a BASH script that does the work. Therefore, it will only work on a linux system equipped with the BASH shell. (And maybe other shell variants, but I don't know for sure).

Instead of using a bash script - and re-creating that script eveytime - why not use curses to do that same - you do't need to go full screen etc, just turn off buffering - look for a key press and re-set the buffering.

---

