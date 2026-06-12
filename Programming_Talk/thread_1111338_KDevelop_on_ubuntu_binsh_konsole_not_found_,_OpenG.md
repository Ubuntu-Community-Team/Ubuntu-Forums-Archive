---
title: "KDevelop on ubuntu /bin/sh: konsole: not found , OpenGL same as Windows ? , other"
date: 2009-03-30
forum: Programming Talk
---

### Post by ashour on 2009-03-30
Hi
i've installed KDevelop on my ubuntu 8.10 Interiped

but whenever i try to execute an application the following errors occur:

konsole --workdir '/home/ashour/helloword2/debug/./src' -e /bin/sh -c '/home/ashour/helloword2/debug/./src/helloword2 ; echo "Press Enter to continue!";read dummy'
/bin/sh: konsole: not found
*** Exited with status: 127 ***

i think the problem that am using gnome so can this be fixed
another question am newely mergin from windows and am a game developer in main i'd like to know if i can just use OpenGL as i use it in windows isn't it a lib that should be generic and have same function everywhere also whats
equivalent to MFC or Windows forms in .net is it GTK does when i create an application for gnome it works over KDE?

---

### Post by Coimbra on 2009-05-01
I've the same problem (first one).

Any help?

---

### Post by keep-on-smiling on 2009-05-01
Hi

I just installed konsole - kdevelop is a KDE app, so it is looking for the KDE version of terminal... 

cheers

---

### Post by skullmunky on 2009-05-01
and to your 2nd question, yes, opengl is a cross-platform open standard, so it should work the same.  there will be some minor differences in how you set up your projects and the supporting code: locations of headers, linker flags, supporting code like file and image loaders, etc.  but OpenGL itself is the same.

---

