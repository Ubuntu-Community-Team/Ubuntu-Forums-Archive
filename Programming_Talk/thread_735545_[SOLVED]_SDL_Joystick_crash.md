---
title: "[SOLVED] SDL Joystick crash"
date: 2008-03-25
forum: Programming Talk
---

### Post by Zeotronic on 2008-03-25
Recently, I tried to open joysticks for use in SDL code (on startup)... and then my application decided to crash (again, on startup). When I remove the code for opening joysticks, it works fine, but when its there it doesn't. This is the first time since my migration from Windows, a year ago, that I have decided to mess with joysticks in SDL... so you can understand if I'm worried about the fault being Ubuntu. I think it more likely my own coding is to blame... regardless, I submit my code with the hope that someone can tell me where I messed up.

I renamed the file .txt... but its really .cc... or .cpp.

---

### Post by Zeotronic on 2008-03-28
*Bump* (and this is the only one I'm giving it)

If it helps, I get the following error on program termination:
> *** stack smashing detected ***: ./main terminated
Aborted (core dumped)


--------------------
(program exited with code: 134)
Press return to continue
I get that error, though as far as I can tell, it should terminate normally.

---

### Post by VdeGrandpré on 2008-09-16
Hi, there is a Buffer Overflow possibility in your code. Check that all your arrays are checked with their length against the length of supplied input. Watch for sprintf function for example.

Supplying '12345678910' to an array a[10] affects the stack (you write the last position (the '0') over the stack. That is Buffer Overflow, or Stack Smashing.

For the rest, I have Hardy Heron on my Ubuntu-studio box and SDL is not working fine for the joysticks. As far as I can tell (I tested it last night) there is no bindings to the joystick native methodes. I use sdljava wich is the adapter Java for SDL wich is know to work fine. JRE tells me that there is native errors.

Also, trying to use this sample code located in parts at  [http://lovehateubuntu.blogspot.com/2008/09/rock-band-drums-in-linux.html?showComment=1220337900000](http://lovehateubuntu.blogspot.com/2008/09/rock-band-drums-in-linux.html?showComment=1220337900000) generates multiple errors with SDL.

My last assumption on this was that the bundled Hardy Heron SDL package (libsdl1.2debian) may be faultive. I'll try to install the sources of SDL tonight and see if it works on my side.

---

### Post by VdeGrandpré on 2008-09-16
Just to mention that to be sure about SDL defunctionnality I'll test first with this Perl script : [http://www.perlmonks.org/?node_id=679581](http://www.perlmonks.org/?node_id=679581)

Vincent

---

