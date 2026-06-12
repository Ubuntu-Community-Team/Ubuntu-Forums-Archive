---
title: "Problem with Compiler"
date: 2005-04-11
forum: Programming Talk
---

### Post by ZetSabre on 2005-04-11
I did a search and couldn't find any other threads related to this; i've been getting an error while trying to compile a source file. It reads: _cc: installation problem, cannot exec `cc1plus': No such file or directory _. Can someone tell me what this means, and how I can get it to work?
Thanks

---

### Post by edubarr on 2005-04-11
Are you trying to compile a c++ file? If so then have you installed the g++ extensions to gcc? This could be your problem...

---

### Post by thePythonAlchemist on 2005-04-11
According to the gcc manpage, `cc1plus' is a program used to perform an additional pre-processing step after normal pre-processing but before compiling. It is specified using the -B flag after using the -no-integrated-cpp flag. Apparently, you normally don't have to worry about this and just let cpp do the work for you.

This type of problem can sometimes be fixed by installing the g++ package. By default it wasn't installed with my system, so maybe the problem is that you don't have g++.

---

### Post by toojays on 2005-04-12
If one of the above posts doesn't solve your problem, it will help if you post the command line which you are using to compile the file.

---

### Post by ZetSabre on 2005-04-12
[QUOTE=toojays]If one of the above posts doesn't solve your problem, it will help if you post the command line which you are using to compile the file.[/QUOTE]Oh, sorry: _cc prog1.cpp_

---

### Post by toojays on 2005-04-13
Does it work if you do "c++ prog1.cpp"?

---

### Post by ZetSabre on 2005-04-13
[QUOTE=toojays]Does it work if you do "c++ prog1.cpp"?[/QUOTE] Nope, the same problem occurs.

---

### Post by toojays on 2005-04-13
In that case, maybe something did go wrong during your installation. 

If you can, try reinstalling the g++-3.3 package. The cc1plus program belongs to that package.

If that doesn't help, post the output of "c++ -v prog1.cpp".

---

### Post by ZetSabre on 2005-04-13
[QUOTE=toojays]In that case, maybe something did go wrong during your installation. 

If you can, try reinstalling the g++-3.3 package. The cc1plus program belongs to that package.

If that doesn't help, post the output of "c++ -v prog1.cpp".[/QUOTE] I couldn't get it to re-install the package, this is what I got from c++ -v prog1.cpp:

c++ -v prog1.cpp
Reading specs from /usr/lib/gcc-lib/i486-linux/3.3.5/specs
Configured with: ../src/configure -v --enable-languages=c,c++,java,f77,pascal,objc,ada,treelang --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --with-gxx-include-dir=/usr/include/c++/3.3 --enable-shared --with-system-zlib --enable-nls --without-included-gettext --enable-__cxa_atexit --enable-clocale=gnu --enable-debug --enable-java-gc=boehm --enable-java-awt=xlib --enable-objc-gc i486-linux
Thread model: posix
gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)
 /usr/lib/gcc-lib/i486-linux/3.3.5/cc1plus -quiet -v -D__GNUC__=3 -D__GNUC_MINOR__=3 -D__GNUC_PATCHLEVEL__=5 -D_GNU_SOURCE prog1.cpp -D__GNUG__=3 -quiet -dumpbase prog1.cpp -auxbase prog1 -version -o /tmp/ccZ4jMxC.s
GNU C++ version 3.3.5 (Debian 1:3.3.5-8ubuntu2) (i486-linux)
        compiled by GNU C version 3.3.5 (Debian 1:3.3.5-8ubuntu2).
GGC heuristics: --param ggc-min-expand=44 --param ggc-min-heapsize=28053
ignoring nonexistent directory "/usr/i486-linux/include"
#include "..." search starts here:
#include <...> search starts here:
 /usr/include/c++/3.3
 /usr/include/c++/3.3/i486-linux
 /usr/include/c++/3.3/backward
 /usr/local/include
 /usr/lib/gcc-lib/i486-linux/3.3.5/include
 /usr/include
End of search list.
In file included from /usr/include/c++/3.3/backward/iostream.h:31,
                 from prog1.cpp:3:
/usr/include/c++/3.3/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <sstream> instead of the deprecated header <strstream.h>. To disable this warning use -Wno-deprecated.
prog1.cpp:6: error: `main' must return `int'

---

### Post by toojays on 2005-04-13
Okay, this is certainly a different problem to the one you described at the beginning of this thread.

The problem now is that the code you are compiling does not comply to the current C++ standard.

If you really need this code to compile, you can start with the following simple things:

1) Get rid of "prog1.cpp:6: error: `main' must return `int'". This usually is because your main function is declared like:```
void main(){
    ...
}
```
Change the beginning and end to be like:```
int main(){
    ...
    return 0;
}
```
2) Get rid of the warning about deprecated includes. At line 3 of your program, you have:```
#include <iostream.h>
```
This should probably be:```

#include <iostream>
using namespace std;
```
What is this code? If you are teaching yourself C++ from a book, I'm afraid your book is out of date.

---

### Post by ZetSabre on 2005-04-13
Oh, sorry, the original problem was fixed when I added the extensions, and then I started talking about the next problem that showed up (I should've said that they were different problems). But yeah, I suppose my c++ book is really out of date, looks like i'll be buying a new one (it was borrowed anyways). I still keep getting the same error for some reason, but i'll just give up untill I get a new book. Thanks a lot toojays, you really went out of your way to help me (you'll be getting a few rep. points from me :smile: ).

---

