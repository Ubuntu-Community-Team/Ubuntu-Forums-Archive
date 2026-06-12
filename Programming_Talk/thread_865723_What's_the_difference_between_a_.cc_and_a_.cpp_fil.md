---
title: "What's the difference between a .cc and a .cpp file?"
date: 2008-07-20
forum: Programming Talk
---

### Post by SNYP40A1 on 2008-07-20
What's the difference between a .cc and a .cpp file?  From man g++:

        file.cc
        file.cp
        file.cxx
        file.cpp
        file.c++
        file.C
            C++ source code which must be preprocessed.  Note that
            in .cxx, the last two letters must both be literally
            x.  Likewise, .C refers to a literal capital C.

They appear to be the same.

---

### Post by damis648 on 2008-07-20
They probably are. They are probably just all common extensions of the same file type, and are interchangeable.

---

### Post by dribeas on 2008-07-21
> **SNYP40A1 said:**
> What's the difference between a .cc and a .cpp file?  From man g++:

        file.cc
        file.cp
        file.cxx
        file.cpp
        file.c++
        file.C
            C++ source code which must be preprocessed.  Note that
            in .cxx, the last two letters must both be literally
            x.  Likewise, .C refers to a literal capital C.

They appear to be the same.

They are common extensions for the same file type: C++ code. Just decide on the one you like most and stick to it. I would not recomend .C or .c++ as you might have problems with some filesystems not handling it correctly or confusing with plain .c (C) files.

---

### Post by nvteighen on 2008-07-21
They are all files that have to undergo preprocessing, so they'll start the compiling process from the very beginning. Conclusion: they all are source code files, so they're the same.

The "standard" extension seems to be .cpp, though.

---

### Post by Kadrus on 2008-07-21
Header Files: .h, .hh, .hpp
Source Files: .C, .cpp, .cc

---

### Post by SNYP40A1 on 2008-07-22
Ok, I'll use .cpp for now.  Thanks for the clarification.

---

### Post by KingTermite on 2008-07-22
> **SNYP40A1 said:**
> What's the difference between a .cc and a .cpp file?  From man g++:

        file.cc
        file.cp
        file.cxx
        file.cpp
        file.c++
        file.C
            C++ source code which must be preprocessed.  Note that
            in .cxx, the last two letters must both be literally
            x.  Likewise, .C refers to a literal capital C.

They appear to be the same.

As others have stated, they are the commonly allowed extensions, and are interchangeable.

I will note though, that in seeing much C++ code of over the years, I have almost never seen anything but ".cpp" for source and ".h" for header files (.hpp is also allowed).

Its best to stick with convention.

Definitely avoid .C as some compilers may interpret as a regular .c file and screw things up. I remember getting totally screwed up once years ago when I tried doing "c++" code, but kept the file extension as ".c". The compiler had no idea what to do and gave some bizarre errors that took me a while to figure out.

---

