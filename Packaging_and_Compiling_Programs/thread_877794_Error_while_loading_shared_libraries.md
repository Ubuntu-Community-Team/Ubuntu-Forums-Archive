---
title: "Error while loading shared libraries"
date: 2008-08-02
forum: Packaging and Compiling Programs
---

### Post by sb01234 on 2008-08-02
When running a program I just built, I get the following error:

"error while loading shared libraries: libNxCharacter.so.1: cannot open shared object file: No such file or directory"

It's possible to start the program by first redirecting the LIB path in the terminal, but most professional applications don't require such commands before they can be started. How can I achieve this, while still having the paths being resolved correctly? I'm not yet familiar with how the mechanism for searching for shared libraries works in Ubuntu (in windows, I know that it works if I just put the .dll files in the same directory as the .exe file, but this doesn't seem to work here).

---

