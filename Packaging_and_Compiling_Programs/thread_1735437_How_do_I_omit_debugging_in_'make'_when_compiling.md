---
title: "How do I omit debugging in 'make' when compiling"
date: 2011-04-21
forum: Packaging and Compiling Programs
---

### Post by Grafens on 2011-04-21
What 'flags' should I add to 'make' to reduce the compiled file size. The man page mentions how to add debugging but not how to omit it.
The “read me” for the source file says:
“Octave requires approximately 1.4 GB of disk storage to unpack and compile from source (significantly less, 400 MB, if you don't compile with debugging symbols). Once installed, Octave requires approximately 350MB of disk space (again, considerably less, 70 MB, if you don't build shared libraries or the binaries and libraries do not include debugging symbols).”

My hard disk is only 8GB in total so I need all the space I can get.
TIA

---

### Post by sanderd17 on 2011-04-21
the default is without debugging, but why don't you take the version from the repo?

---

### Post by Grafens on 2011-04-21
> the default is without debugging
Yeah I thought so too but when the program builds using only the command 'make' with no flags it eats all of what's left of my hard drive (just over 1G). Any idea what could be wrong.
> but why don't you take the version from the repo?
Would do but another program I want to use depends on the latest release of octave3.4.0, which isn't in synaptic/apt-get.

Maybe you know where I can find a deb file for octave3.4.0
TIA

---

### Post by MadCow108 on 2011-04-21
> **sanderd17 said:**
> the default is without debugging, but why don't you take the version from the repo?

default is, as with almost all applications, with debugging.

to disable it by default do this:
```
CFLAGS="-O2" CXXFLAGS="-O2" ./configure --your-options
```

for a single build:
```
make CFLAGS="-O2" CXXFLAGS="-O2"
```

you could also use -pipe to reduce space requirements a little bit more

edit:
actually I just saw that the makefile is broken, it sometimes always uses -g no matter what you tell it...
either fix the makefiles or compile until your out of space and then do
```
find -name "*.o" | xargs strip
```
to remove all debugging symbols and continue

---

### Post by Grafens on 2011-04-22
@MadCow108
Thanks for the informative reply, I will give your suggestions a go and see how far I get.
Grafens

---

