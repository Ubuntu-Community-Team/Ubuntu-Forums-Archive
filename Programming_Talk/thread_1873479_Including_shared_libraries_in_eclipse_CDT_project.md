---
title: "Including shared libraries in eclipse CDT project"
date: 2011-11-01
forum: Programming Talk
---

### Post by cwhittier on 2011-11-01
I hope I'm posting this in the correct section.

I have an eclipse project that includes webkit-1.0. It builds, links, and executes fine on my development machine. When I try an run it on another ubuntu machine, I get the error message "**cannot open shared object file webkit-1.0.so.2: No such file or directory**"

Shouldn't all required libraries be compiled into the executable at build time? How can I include this library so my executable will work on other machines without the libwebkit-1.0-dev files installed?

---

### Post by 11jmb on 2011-11-01
Shared libraries are linked against at runtime.

Go to Project>Properties and select "Settings" under "C/C++ Build"

From there you can make sure all of your required directories are included

---

### Post by cwhittier on 2011-11-01
So it's impossible then, to run my application on ubuntu systems that do not have libwebkit-1.0 installed?

Is there a way around this, or can it be converted into a static lib? I'm sort of unclear why I would need to have development libraries installed on every machine in order to run an executable.

---

### Post by 11jmb on 2011-11-01
Well yes, if its a dependency, you need to be able to link against it somehow. 

If you have the source code for libwebkit, you could compile it as a static library, and then when you build your executable, it will link at compile-time (your executable will be much larger though)

---

### Post by cwhittier on 2011-11-01
Size isn't an issue. I'm trying to download the source now. Thanks.

---

### Post by 11jmb on 2011-11-01
Good luck. Building a static library from somebody else's project is not always an easy process, so report back when you look at their build environment.

I have done this with smaller projects with hand-written makefiles, but never with Autotools projects. Hopefully we can work something out though. Libtool may make it easy for you

---

### Post by cwhittier on 2011-11-01
Thanks.. The source is still downloading from since before my last post.

Is it also possible to copy the .so files from my system, install them locally, and set the LD_LIBRARY environment variable on launch to point to the folder I put them in? I was told this is a possible solution, but have not tried it yet.

---

### Post by 11jmb on 2011-11-01
I don;t know the answer to that, you can certainly try it. This may prevent you from linking other libraries though.

---

### Post by cwhittier on 2011-11-02
I gave up trying to compile the lib statically. After 2 hours of checking out the source and not being finished, I also noticed that there was a whole bunch of other stuff for mac support and xcode, and I got nervous and cancelled. 

I did solve my problem though, by grabbing the so files off my system, and installing them with my application on the other machine, and launching my program with a script, setting the LD_LIBRARY_PATH variable to look at my custom libs folder. This took care of it for me, and since we control the entire OS for this application there's no harm in doing it this way.

Thanks for all your help.

---

