---
title: "py2exe on Ubuntu, with Fortran extension module"
date: 2009-02-07
forum: Programming Talk
---

### Post by Asrai99 on 2009-02-07
Hello, all,

I'm working on a project at the moment which involves writing a stellar modelling code in Fortran90 and then writing a computational steering script for it in Python, so all the user gets to see in the end is a pretty GUI. I've used f2py for the Python/Fortran interface and when I've tried it out for a simple example, everything worked rather swimmingly - and if everyone in my department were to use Ubuntu, we could all live happily ever after.

Alas, most people are stuck with Windows, so I need to put the entire thing in an .exe file that your average user can just click on and off it goes. I know that py2exe can do this, however I'm also pretty sure it was designed for use on Windows only? Is there a way to make it work under Ubuntu?

There was a thread about this topic in this forum a couple of weeks ago (basically I got the feeling that it's possible to make .exe files on Ubuntu, but not exactly easy), however in my case there's the complication that I've got some Fortran code as well. Is it possible to compile it under Ubuntu, then use py2exe and everything will work on Windows?

Or should I give up right now and compile the program under Windows, including the Fortran bits? (Are there any free Fortran compilers for Windows...? It's not something I've had to think about before now.)

Any help would be appreciated! ;)

---

### Post by ahjulsta on 2010-06-24
I see this is an old thread, but I'm very interested in experiences other might have.

I have used f2py with the gfortran compiler with great success. It was actually surprisingly easy to do. (the only little snag was having to specify mingw32 as the default compiler, google "mingw32 vcvarsall" for other users experiences with this).

What is missing is py2exe on Windows, with a f2py extension module. Is this easy?

---

