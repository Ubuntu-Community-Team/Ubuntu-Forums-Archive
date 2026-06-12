---
title: "LD_LIBRARY_PATH Question"
date: 2005-01-29
forum: Programming Talk
---

### Post by cwaldbieser on 2005-01-29
Does the LD_LIBRARY_PATH environment variable work in Ubuntu similar to how it does in other distros?  I have previously worked with both Debian an Mandrake 9.2, and exporting this variable would cause my programs to search the paths I gave for shared libraries.  I've tried the same trick with Warty, but it doesn't seem to work.  sym-linking the library into /usr/lib seems to work, but I hate to keep reaching for sudo all the time.  Any thoughts?

Thanks,
Carl Waldbieser

---

### Post by mendicant on 2005-01-30
It should.

I just tried ldd with a modified LD_LIBRARY_PATH, and it displays the expected thing, and strace reveals it opening the correct file in my LD_LIBRARY_PATH.  What evidence do you have that it doesn't work?

---

### Post by cwaldbieser on 2005-01-30
I downloaded and compiled a side scrolling game called "Holtz's Castle", which creates an executable and a library.  The library installs itself in /usr/local/lib.  I tried setting my LD_LIBRARY path to that directory, but kept getting an error that the library failed to load.

Dunno what I was doing wrong (maybe a typo?), but I tried it a couple times before posting.  Tried again after reading your reply, and it works fine now.  I must have just been doing something silly (maybe two different shells open and I didn't notice I exported in one and tried to run in the other.

Anyway, thanks for your help.

Carl Waldbieser

---

