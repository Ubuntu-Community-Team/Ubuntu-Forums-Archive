---
title: "Problem with Gnat (Ada)"
date: 2011-01-27
forum: Packaging and Compiling Programs
---

### Post by Kaangaas on 2011-01-27
Hey!

Im not sure if this is the correct forum but if its not can someone please move it to the correct one.

Anyway I'v just installed Gnat on my computer to do some ada programming. But I've got a problem, I think the compilation of the program is running as it should, creating the three extra files as it should. But I cant run the program.

For instance if the program is named asdfg.adb I'll type: "gnatmake asdfg.adb" and the terminal will say:
gcc-4.4 -c asdfg.adb
gnatbind -x asdfg.ali
gnatlink asdfg.ali


When I try to run the program I'll type: asdfg (in the right directory of course).
But the onlything I get is Command not found, and a whole lot of suggestions.

Even tried to make the executable file executable myself.

Any one got an Idea whats wrong?

Sincerly
Kaangaas

---

### Post by bouncingwilf on 2011-01-27
If ADA compilation output (executable)  files follow the gcc "norm" then you either will have to add the path to the executable to your environment or usually just typing  ./asdfg will execute the file i.e it's a PATH thing.


 Bouncingwilf

---

### Post by Kaangaas on 2011-01-27
Thank you, that did it. Felling abit stupid for not thinking of that my self...

---

### Post by bouncingwilf on 2011-01-27
It took me hours to work that out in 198?  It was buried deep somewhere in the compiler/OS manuals of SCO Unix. Of course it's obvious now but back then I'd just installed a system (off 5.25" floppies) and was trying to work everything out from scratch and was too mean/busy to go on a Unix familiarization course so it was all guesswork on a new system. (No Google in those days!).

Please mark as solved.

Bouncingwilf

---

### Post by zacharia on 2011-01-27
any body know where to get full file of sun java for ubuntu10.10

---

