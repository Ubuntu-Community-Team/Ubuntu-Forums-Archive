---
title: "Launching in Another Virtual Terminal From C"
date: 2007-06-13
forum: Programming Talk
---

### Post by ankursethi on 2007-06-13
I'm building an app using ncurses (mostly for my own use) that will be useless if not run in fullscreen. Is it possible to launch a C program in a fullscreen terminal? Any way to launch it in another virtual terminal altogether?

Not wanting to create another thread, here's another question. How to launch an external program from C and read in it's output? I don't want to display it in the terminal, just read it into a buffer that I can later use.

---

### Post by the_unforgiven on 2007-06-13
> **ankursethi said:**
> I'm building an app using ncurses (mostly for my own use) that will be useless if not run in fullscreen. Is it possible to launch a C program in a fullscreen terminal? Any way to launch it in another virtual terminal altogether?
You could launch your terminal program with --geometry option which is understood by most console apps (I know of gnome-terminal; I guess konsole uses --vt_sz option). Just read the help.

By virtual terminal, do you mean tty or terminal emulator like gnome-terminal/konsole/rxvt/xterm?

> **ankursethi said:**
> 
Not wanting to create another thread, here's another question. How to launch an external program from C and read in it's output? I don't want to display it in the terminal, just read it into a buffer that I can later use.
2 ways:
1. dirty way - more control on the I/O to and from the process:
a. pipe()
b. fork()
c. exec()

2. easier way - far lesser control on the I/O to and from the process:
a. popen()
b. pclose()

Read the man pages of the functions for more details.
popen() internally does pipe(), fork() and exec() for you anyway, but it starts a proper child shell and executes the command you give inside this child shell - which means that the shell goes through all its initialization process (creating profile and environment etc.). This could be unnecessary and slow.

HTH ;)

---

### Post by ankursethi on 2007-06-13
I read the GNOME Terminal manpage. It points me to the X manpage to see the geometry option. The x manpage doesn't exist. The xorg manpage doesn't have the geometry option.

BTW, by virtual terminal I mean the terminals you access using CTRl-ALT-F(1-7). What are they called?

---

### Post by the_unforgiven on 2007-06-14
> **ankursethi said:**
> I read the GNOME Terminal manpage. It points me to the X manpage to see the geometry option. The x manpage doesn't exist. The xorg manpage doesn't have the geometry option.
Unfortunately, I use KDE - don't have GNOME installed at all :(
So, I cannot verify this :(

> **ankursethi said:**
> BTW, by virtual terminal I mean the terminals you access using CTRl-ALT-F(1-7). What are they called?
They're called TTYs - *T*ele*TY*pe terminals.
I don't know of a way to programmatically switch to the ttys.
But, I guess, nCurses should have some way of finding the geometry of the current console (be it tty or pty).
Need to read up on ncurses docs.

---

### Post by slavik on 2007-06-14
to find out the geometry of current terminal or even change lots of stuff, look up termios.h :)
don't think it will allow you to do "fullscreen" (that requires the window manager to do that)

what is this app supposed to do? (if not a secret)

---

### Post by ankursethi on 2007-06-14
It's not a secret.

At school we use the extremely outdated Turbo C++ IDE (v3.x) last seen in year 1992 (the one with the ugly VGA graphics). I personally don't like it. I prefer to use either a text editor (I installed SciTE on all PC's once when I got the chance) or Visual Studio. I just wanted, as a fun excercise, to build a clone of that IDE on Linux (using GCC, of course). It will become very difficult for me to resize all the menus and everything (considering I get somewhere with the project) to fit on the screen of the GNOME Terminal.

BTW, ncurses does provide a way to detect terminal geometry, but it will be tedious to resize the entire environment to fit on that tiny 80x24 screen. It will also be tough to switch between those teletype terminals each time I wanted to try out the app.

---

### Post by slavik on 2007-06-14
well, as part of documentation you could say "best run in 80x25" terminal ... or something.

---

### Post by ankursethi on 2007-06-14
> **slavik said:**
> well, as part of documentation you could say "best run in 80x25" terminal ... or something.
Looks like I have no other option. Thanks for the help :)

---

### Post by slavik on 2007-06-14
just aim for 80x25 terminal and you'll be fine

---

