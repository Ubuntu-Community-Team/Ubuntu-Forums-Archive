---
title: "Chromebook WIFI fix"
date: 2014-05-29
forum: New to Ubuntu
---

### Post by bob82 on 2014-05-29
Successfully installed chrubuntu on Acer c720 16gb with dual boot option, but WIFI only works in Chrome OS, not Ubuntu.
I have seen fixes for this but from both initial crosh terminal and from shell I cannot execute sudo commands, and/or get nano not found. I AM an Absolute Beginner, so I may not be ebtering commands correctly. - In sum - I am looking for BOTH a fix to the WIFI issue, and to how I properly enter commands in terminal. Ever grateful/

---

### Post by Rob Sayer on 2014-05-29
I probably wouldn't be too much help with the specific problem, but for a start copy and paste the following into the terminal in ubuntu:

sudo lshw -C network

It'll take  a few seconds to complete.  Post the results  here, wrapped in [CODE] tags.

It's not easy to say whether you entered commands propoerly without knowing what you did exactly.

But nano is just a simple text editor, and while you should definitely have one of those it may be something else.  I prefer leafpad myself.

And you don't open a program like nano with sudo.  You use gksudo.  Some buntu versions don't come with that.  If not, install gksu.

But you may not need to edit a config file anyway.  I've done it plenty of times but never for a wireless issue.

---

### Post by tash2 on 2015-03-01
Hi, were you able to get this resolved? I'm having the same issue and have tried a bunch of stuff, but I can't get the wifi to turn on (and I can't install the iw files with no connectivity.

Any help would be greatly appreciated!

---

