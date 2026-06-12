---
title: "Python GUI frontends for command-line tools and status monitoring"
date: 2009-07-24
forum: Programming Talk
---

### Post by kpkeerthi on 2009-07-24
I'm in the very early stages of learning python; so pardon me if it sounds so stupid.

I want to (eventually) write a GUI to some popular command-line tools (like mencoder, ffmpeg, rsync) using PyGTK/GtkBuilder/Glade. 

I understand it is possible to spawn an external tool using Python. But I'm wondering how do I track the progress of the spawned process? If I have to display a visual progress indicator I need to know the 'begin' and 'end' value. But this may not be possible with a spawned process as we have no control over it. 

I need to somehow determine how many 'steps' the spawned tool would take to complete the task and the number of steps it has completed so far. What are possible ways to achieve this. I'm not looking for a python code, just need some pointers. 

Should I read from the 'standard out' of the spawned process, parse and determine the progress somehow? Is there a better solution?

Thanks for any help.

---

### Post by jero3n on 2009-07-24
> **kpkeerthi said:**
> Should I read from the 'standard out' of the spawned process, parse and determine the progress somehow? Is there a better solution?

This is the only way in most cases. Give a look to each tool documentation if some of them could inform your program in another way.

---

### Post by pelle.k on 2009-07-24
> Should I read from the 'standard out' of the spawned process, parse and determine the progress somehow? Is there a better solution?
Yes that is how you do it. And there is no better solution i'm afraid.
Programming GUI wrappers to command line tools is unfortunately not and ideal solution. The end result is often "hacky" at best.
What you want to do, is to find a library that has the proper interface for interaction, what is called an API. Take apt-get or aptitude command line tools, they use libapt for their function. Synaptic doesn't parse output from apt-get, it uses libapt too. Many command line tools, are just CLI frontends to one/several libraries.

In apt's case, there's a python wrapper for the C library (libapt) called python-apt.
That's the ideal solution. Not all C/C++ libaries have python wrappers though, but many do. And there are also several conversion tools that produce a python wrapper from a pure C/C++ library, but it's nowhere as convenient as when someone has taken the time to do it properly.

EDIT: just take a look at some of the wrappers/"bindings"
```
aptitude search ^python-
```
There are guides for many of them on the internet, and when you install a library, it ends up in pydoc automatically.

---

### Post by jero3n on 2009-07-24
Wouldnt it be nice if there were a library that would provide a communication interface to various popular linux command line tools? :)
No?
I dont know..just a thought..

---

### Post by kpkeerthi on 2009-07-24
@pelle.k:
Yes, you are correct. I'm aware that using an appropriate python binding would the best approach. But I was looking for a proper/safe way to interface with tools like mencoder & ffmpeg, where there are no python bindings (atleast I'm not aware of any that exist). Thanks for your input. Much appreciated.

---

### Post by pelle.k on 2009-07-24
> Wouldnt it be nice if there were a library that would provide a communication interface to various popular linux command line tools?
It would! But many of the bash/sh builtins, and most third party "commands" such as diff/sort/sed have much more powerful eqvivalents already built in the standard python library.
However, as kpkeerthi pointed out, some have no eqvivalents or bindings to python, and that would be very nice indeed, with mencoder being a perfect example. To be honest, i haven't really looked into mencoder, maybe there are bindings. I guess preparing bindings to many of the low level C/C++ libaries isn't very glamorous or rewarding...
> Thanks for your input. Much appreciated. 
No problem. To be honest, i wish i had a "better" answer for you. The lack of good bindings for some libraries/applications is sometimes holding me back as well.

---

