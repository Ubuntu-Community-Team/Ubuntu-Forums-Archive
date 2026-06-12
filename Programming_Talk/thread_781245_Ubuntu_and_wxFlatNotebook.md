---
title: "Ubuntu and wxFlatNotebook?"
date: 2008-05-04
forum: Programming Talk
---

### Post by Maverick5x on 2008-05-04
Hello,
I am working on Ubuntu Hardy and developing a simple app using CodeBlocks in C++.
I included the wxFlatNotebook control to my frame but it didn't compile because the header files were not there. I managed to get the files from sourceforge, i knew where to place the header files for this control but not the cpp files. They are included in the src directory of wxFlatNotebook.
Even though headers are there CodeBlocks gives me:
```

Main.cpp|66|undefined reference to `wxFlatNotebook::wxFlatNotebook(wxWindow*, int, wxPoint const&, wxSize const&, long, wxString const&)'|
```
I know its because the cpp files are missing, but where am i supposed to put them on my Ubuntu?

Thanks,
Rakan

---

### Post by matja on 2008-05-04
Hi Rakan,

External source files are usually compiled into static/dynamic library files once and for all, so you don't need to recompile it every time you rebuild your program. I looked at wxFlatNotebook and they've made a makefile for this in build/wxFlatNotebook (see the README in the base directory). Running this should create one or more ".a" files in a newly created lib directory in the base directory. I didn't find an install target in the makefile however, so after the library files are built you need to move them to a place where your compiler searches for libraries, e.g. /usr/local/lib, or add the lib directory to your compiler's search path for library files. The latter can be achieved by adding a -L flag to g++:

```
g++ -L/path/to/wxflatnotebook/lib -lwxflatnotebook <your source files here>
```

The -l (lower case L) tells g++ to include the wxflatnotebook library when linking and the -L where to search for it first.

Good luck!

/Mattias

Edit: I just noticed you were using Codeblocks, so maybe the g++ pointers aren't that helpful ;) I'm sure there is some convenient function to include external libraries in CodeBlocks as well, but I've never used it myself.

---

