---
title: "gcc-h8300-hms problem: multiply doesn't work?"
date: 2008-05-19
forum: Programming Talk
---

### Post by hvymtlsteve on 2008-05-19
I used apt-get to install the package gcc-h8300-hms, and I have successfully compiled programs for this target system, but I have a bit of a problem. 

Whenever I try to multiply two ints, I get:

main.o:main.c:(.text+0x1e): undefined reference to `___mulsi3'
collect2: ld returned 1 exit status

I don't seem to get an error if I multiply two chars, or an int with a constant.

Any ideas how to fix this?

---

