---
title: "Tcl Expect - problem with expecting"
date: 2010-02-21
forum: Programming Talk
---

### Post by wy2k10 on 2010-02-21
Hello, 

I'm trying to create a gui for a Forth application, by linking Tcl/tk with Forth using Expect. The way it's setup now, i'm using tclsh with the script file to launch the gui, and in the script using Expect to spawn Forth, so i have the gui displayed and Forth running in the terminal.

What i want to do is for Expect to be aware of all commands typed in Forth while Forth is working normally, for example if i use expect "command1", all other Forth commands won't work  and when i type command1 in Forth it will work only once.

Ok, i hope i didn't make it more confusing than it already is, my question is, how do i make Expect expect a command to be typed again and again (loops don't work) without taking all focus and preventing Forth from working.

Thanks

---

