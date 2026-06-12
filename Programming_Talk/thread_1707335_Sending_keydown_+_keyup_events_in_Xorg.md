---
title: "Sending keydown + keyup events in Xorg"
date: 2011-03-15
forum: Programming Talk
---

### Post by WitchCraft on 2011-03-15
I want to control JD-GUI (closed source) on Linux from another application to decompile a JAR file (one of my own).
The problem is, there is no command line version of JD.

The only option left it seems is to send fake keyboard events, to use the shortcuts to achieve this.

I used C#, but sendkeys doesn't seem to work...
Another thing is I need to activate the target window somehow.

Can somebody give me a simple C/C++ example of how to control the keyboard with XSendEvent? 

I can only find examples with xsendfakekey (or whatever it is called), which also requires the installation of an additional library, plus I would already have the C# code to interface with XSendEvent.

Another decompiler that can decompile jar files on the command line and that works well enough would also be fine. 
Note: Not JODE, it isn't good enough, I tried.


I also tried command line utilities (a command line tool that I could invoke would also be fine), but the problem there is how to find the target window to activate it 
(well, I guess also a problem when using XSendEvent).


Is there any way in C/C++ to activate a Xorg window by it's title and/or PID ?

Note: 
I can control the mouse position and mouse-click events from C#.
So if I know the rectangle position and size of the target window, the problem of getting the active window is solved.
(knowing the menu position would also do the trick, fully mouse-controlled then)

---

### Post by WitchCraft on 2011-03-15
Bump

---

### Post by WitchCraft on 2011-03-16
Bump.

---

