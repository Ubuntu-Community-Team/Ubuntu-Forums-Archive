---
title: "gcc options for some libraries"
date: 2007-11-05
forum: Packaging and Compiling Programs
---

### Post by xboxbman on 2007-11-05
I'm trying to compile a program using the libraries 
<stdio.h>
 <math.h>
 <ctype.h>
 <string.h>
 <stdlib.h>

the first 2 are easy. I know for math.h type ```
gcc -lm
``` but i can't figure out which options to use to get the other libraries included when I compile.  Can anyone help?  Is there a list I can bookmark so I don't have to keep coming to ask this?  I looked in man, but there is a lot of info to get lost in.

---

### Post by Noodels on 2007-11-07
I thought you just put a '#include <myspeciallibrary.h>' at the start of the source. No matter, isn't there some sort of command like 'gcc --?' (tried it and doesn't work but I thought there'd be something) ? If not I'd look on the gcc website.

---

### Post by oberg on 2007-11-09
Like noodels said, you will need the #include in front of each library file.  If you're getting some weird linker error with a bunch of crap shooting onto the terminal, try using g++ instead of gcc.  I have an issue with gcc when trying to compile c++ programs.  If you don't have it installed you can easily get it from the package manager at:

system > administration > synaptic package manager.

Hope that helps.

---

