---
title: "Where's readline?"
date: 2013-11-23
forum: Packaging and Compiling Programs
---

### Post by llanitedave on 2013-11-23
I am attempting to install Postgresql 9.3.1 from source, since there is apparently no Ubuntu package for this version yet (I could only see 9.1).  I downloaded the source code and documentation, unpacked the tar file, and cd'd into the proper directory.  

Using the ./configure command started the process, but it ended with the following error:

"configure: error: readline library not found"

I used sudo apt-get install readline, thinking it was somehow missing from my Ubuntu installation but that failed with

"Unable to locate package readline"

Is there something I should know that I'm just clueless about?

---

### Post by steeldriver on 2013-11-23
Typically, whenever you're building packages from source you need the associated -dev package. In the case of readline, that would likely be **libreadline-dev** I think (which is itself probably a metapackage that currently pulls in libreadline**6**-dev).

---

### Post by llanitedave on 2013-11-23
That did it!  Thanks, this was the first time I'd tried to compile anything on this machine.  I still have a lot to learn!

---

