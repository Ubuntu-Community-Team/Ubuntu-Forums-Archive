---
title: "monodevelop 2.4 debug/breakpoints issue"
date: 2010-07-13
forum: Programming Talk
---

### Post by Mauri72 on 2010-07-13
Hi all, 
I was using Monodevelop 2.2 from the official repos and it worked well enough. When I saw that 2.4 had been released I added the Badgerports repo to my list and updated all there was to update on my system. Compiling and running projects still works well and I love a lot of the changes, but I cannot use the debugger. On a C# project the debugger seems to start but the breakpoints are never reached and nothing happens. On a C++ project it when I tried to debug, first monodevelop simply crashed and on successive attempts nothing happens at all.
Any idea what may be going wrong on my system or how to troubleshoot it?
Cheers,
Mauri

---

### Post by SKLP on 2010-07-15
That's odd, debugging works for me :/

You should probably make sure you are using the Mono 2.6 soft debugger rather than the old "hard" debugger. Soft debugger support is included in the core "monodevelop" package, whereas hard debugger is in "monodevelop-debugger-mdb", so I wouln't even have the latter installed, just to make sure

---

### Post by Mauri72 on 2010-07-30
Thanks, I switched to the soft debugger and it is now working beautifully on my C# projects. However, on C++ I am still unable to debug.

---

### Post by davoudi on 2010-08-20
I have the same problem. Debugs related windows pop up for a second and they disappear after I hit the debug bottom! I am using Ubuntu 10.04, MD 2.4 and I also put soft debug in higher priority. Thanks.

---

### Post by davoudi on 2010-08-24
The bug is under investigation: [http://go-mono.com/forums/#nabble-td2304192](http://go-mono.com/forums/#nabble-td2304192)

---

