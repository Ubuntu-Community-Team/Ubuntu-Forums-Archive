---
title: "makefile//Result directories"
date: 2008-06-09
forum: Packaging and Compiling Programs
---

### Post by abraxas334 on 2008-06-09
I could do with some help concerning the following problem.
I have written a c++ program, which creates various output files. Rather than spitting them out into the project file i would like to create a Results directory, to which all the output data files are moved.
for compiling the program i use a very very basic makefile, ie what you would normally type in command line: g++ something.cc -O3 -o something. I think i vaguely remember being told that u can specify target output files with a makefile, is that right? if not how else can i specify an output directory for all my data files??
Any help would be much appreciated.Ta

---

### Post by ibuclaw on 2008-06-16
You mean a directory to put the compiled binaries in before installation?

You can include "mkdir" in the Makefile, and then compile it with the **-o** option pointing to that directory.
```

all: srcfile.cc
        **mkdir outputdir**
        g++ srcfile.cc -O3 **-o outputdir/srcfile**

```

Regards
Iain

---

