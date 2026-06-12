---
title: "[C++] Change Terminal font color"
date: 2009-07-15
forum: Programming Talk
---

### Post by wbest on 2009-07-15
Hey, I'm trying to change the font color (foreground color) in Ubuntu Linux terminal through C++.
Ideally, I'd like the code to look similar to this (Windows Console code):

RED       = FOREGROUND_RED, 
    GREEN     = FOREGROUND_GREEN, 
    BLUE      = FOREGROUND_BLUE, 
     
    GRAY      = RED   | GREEN | BLUE, 
    BROWN     = RED   | GREEN, 
    MAGENTA   = RED   | BLUE, 
    CYAN      = GREEN | BLUE, 
 
    YELLOW    = BROWN | FOREGROUND_INTENSITY, 
 
    B_RED     = RED     | FOREGROUND_INTENSITY, 
    B_GREEN   = GREEN   | FOREGROUND_INTENSITY, 
    B_BLUE    = BLUE    | FOREGROUND_INTENSITY, 
 
    WHITE     = GRAY    | FOREGROUND_INTENSITY, 
    B_YELLOW  = YELLOW  | FOREGROUND_INTENSITY, 
    B_MAGENTA = MAGENTA | FOREGROUND_INTENSITY, 
    B_CYAN    = CYAN    | FOREGROUND_INTENSITY



And then be able to use those elsewhere in my code.

How can I do this?  I've read I might be able to do this with ncurses, but I haven't tested yet as this is for work, and I can't download ncurses because of the network security.

---

### Post by supirman on 2009-07-15
This can be done via terminal escape sequences.  For an example, see [http://linuxgazette.net/issue65/padala.html](http://linuxgazette.net/issue65/padala.html).

---

### Post by wbest on 2009-07-16
Oh awesome.

I had seen stuff about the escape characters before, but nothing about using them in C/C++.

Its working great now, thanks a bundle.

---

