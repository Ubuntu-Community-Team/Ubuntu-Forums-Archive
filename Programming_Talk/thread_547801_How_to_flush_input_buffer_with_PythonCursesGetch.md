---
title: "How to flush input buffer with Python/Curses/Getch?"
date: 2007-09-10
forum: Programming Talk
---

### Post by Torajima on 2007-09-10
I'm messing around with Curses programming, but I can't figure out how to clear the buffer when using getch to capture keystrokes. 

Basically, when you hold a key down it remembers multiple keystrokes, and I need to make sure it only reads the last key pressed.

sys.stdout.flush() doesn't seem to work...

---

### Post by Torajima on 2007-09-10
Anyone?

---

### Post by Torajima on 2007-09-12
Bump.

---

### Post by pmasiar on 2007-09-12
looks like no deep-level command-level Python hackers around - only web apps weenies like me :-)

You may have more luck at pytho.org mailing list - good luck!

---

### Post by Lux Perpetua on 2007-09-13
I don't know about python/curses, but I wrote a C program with curses a while ago that included this. It simply read characters (after calling nodelay) until a read resulted in ERR. I don't know how much it would help you, but from what I understand, curses in python simply wraps the C library.  If you want, I can post the C program. It's only 46 lines.

---

### Post by slavik on 2007-09-13
we did it the same way, the other way is to turn off buffering for input (meaning you get a key at a time, not a line), this way you can manage the input buffer yourself :)

but technically, IMO there is no such thing as "flushing" then input buffer, since you are not the one who is putting things in there ...

the user flushes the buffer (usually by pressing the Enter key)

---

### Post by Torajima on 2009-07-07
Sorry to respond to an old thread... but I wanted people who got here from google to have an answer.

curses.flushinp() apparently does what I need it to.

> Flush all input buffers. This throws away any typeahead that has been typed by the user and has not yet been processed by the program.

---

