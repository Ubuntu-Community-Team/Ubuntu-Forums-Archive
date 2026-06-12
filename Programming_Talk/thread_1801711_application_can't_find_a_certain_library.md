---
title: "application can't find a certain library"
date: 2011-07-11
forum: Programming Talk
---

### Post by ahrimen on 2011-07-11
I'm new to linux and I just recently re-installed ubuntu 10.10 (11.04 was having problems that I didn't want to deal with).

I'm trying to use SFML in a program and using CMake to help out.

in CMakeLists.txt I'm linking sfml-system to the executable and cmake does not complain, and neither does make, in other words the program gets made just find. But, when it is ran it states it can't find libsfml-system.so.1.6 (which is what libsfml-system.so is linked to).

The error it throws is "error while loading shared libraries: libsmfl-system.so.1.6: cannot open shared object file: No such file or directory."

I do not understand why this is happening, the file does exist in /usr/local/lib.

Here are some misc comments about my system just in case it is meaningful, on this install my /home is on a seperate partition then /. All of my code and third party stuff is under /home. 

When I was using "make install" for SFML /usr/local/lib and /usr/local/include had to be made writable for everybody which is something I've never had to do before; is this because of using multiple partitions?

Back to the original question, why is it that make has no problem finding /usr/local/lib/libsfml-system.so but my little program can't?

thank you in advance.

---

