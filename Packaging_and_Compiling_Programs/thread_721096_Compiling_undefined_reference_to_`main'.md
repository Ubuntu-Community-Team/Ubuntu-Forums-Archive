---
title: "Compiling: undefined reference to `main'"
date: 2008-03-11
forum: Packaging and Compiling Programs
---

### Post by pacofvf on 2008-03-11
I've tried all in this posts:(here at ubuntu forums and at other forums, even in other languages, and i have not recieved a straight answer please , help me)
[http://forum.ubuntu-fr.org/viewtopic.php?pid=1437516](http://forum.ubuntu-fr.org/viewtopic.php?pid=1437516)
[http://computerhelpforum.org/forum/index.php?showtopic=15898&st=0&p=101878&#entry101878](http://computerhelpforum.org/forum/index.php?showtopic=15898&st=0&p=101878&#entry101878)
[http://www.ubuntu-es.org/index.php?q=node/27789](http://www.ubuntu-es.org/index.php?q=node/27789)
[http://www.ubuntu-es.org/index.php?q=node/27789](http://www.ubuntu-es.org/index.php?q=node/27789)
[http://ubuntuforums.org/showthread.php?t=205052](http://ubuntuforums.org/showthread.php?t=205052)
[http://ubuntuforums.org/showthread.php?t=60137](http://ubuntuforums.org/showthread.php?t=60137)
i get this message while compiling:
gcc -g -Wall -o ${1%%.c}.out $1 `pkg-config --cflags --libs gtk+-2.0`
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'.

It doesn't matter what i compile it gives me the same error.

---

### Post by jaddle on 2008-03-11
The -o switch to gcc tells it to try to link your source into an executable. If the file you are compiling is only part of a program though, the linking will fail, because it tries to link the .o file up to whatever file has main() in it - i.e. the starting point of the program - which isn't there.

If you just want to compile to .o object files to link later, just leave off the -o switch altogether, or specify the -c flag to turn off linking.

---

### Post by pacofvf on 2008-03-11
well actually i don't know what the problem is, maybe the newer versions of gcc or other compilers(g++ etc) have trouble with an specific order of the arguments but i solved the problem only changing the order of the arguments to this :
 gcc -Wall -g test.c -o outputfile `pkg-config gtk+-2.0 --libs --cflags`
:confused:

---

### Post by puttux on 2008-08-07
when compiling programs, the order of the arguments do matter. Arguments for linking libraries must come after the source. The compiler/linker searches for only those symbols (function definitions etc..) in the library for which it already doesn't have a definition. If the symbol itself comes after the library options, they won't be linked and you get a linker error.
(someone please improve what i've said above :) )

---

