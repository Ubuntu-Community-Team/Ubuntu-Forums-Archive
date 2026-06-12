---
title: "how to compile SDL?"
date: 2010-06-29
forum: Packaging and Compiling Programs
---

### Post by baxzius on 2010-06-29
configuring SDL package leads to a error that states that ** lack of /lib/cpp sanity....**
whats thats mean?
i have installed **build-essential**,**LIBC6** and **kernel-header files.**
why is this error?

---

### Post by mc4man on 2010-06-30
Considering the error should be early in the configure maybe post the complete terminal output and mention what sdl source you're trying to build. (why is your business I guess

Am assuming the error occurs right after something like this

checking how to run the C++ preprocessor...

Even though build-essential should have installed, ck. that g++ is installed (dependency package) and note which version # of g++-X.X is installed (the actual compiler package

---

