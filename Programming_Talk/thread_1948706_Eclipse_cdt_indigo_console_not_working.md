---
title: "Eclipse cdt indigo console not working"
date: 2012-03-28
forum: Programming Talk
---

### Post by Hate on 2012-03-28
Hi all,

Recently I had to work on some C project for an homework and I've decided to install eclipse 3.7 cdt (I used that before so I'd like to stick with that ) from synaptic.
Everything went right but when I've started debugging my project, after successfully building, the eclipse console wasn't showing nothing. 
I've tried even basic printf followed by fflush(stdin) but it didn't work (ofc running the program in the terminal works properly).

(I'm running eclipse on ubuntu 11.10 x64)


EDIT: the console was actually returning ".gdbinit: No such file or directory" when I was killing the debug, so I've tried to fix the path of that file (that is actually a file with only  1 comment line ) in the debugger option as /etc/gdb/gdbinit and that solved the message showing up but still I couldn't get any console output while debugging

---

