---
title: "C++: #include doesn't find file?"
date: 2005-08-29
forum: Programming Talk
---

### Post by Guest1234 on 2005-08-29
I have installed via the Synaptic Package Manager the ligbdome2-0 package,
it's a package for manipulating xml/html files using DOM.
I have a class called XMLSerializable, which does include to the following file:
```
#include <gdome.h>
``` 

but when I try to compile Person.cpp that uses this class I get this error message:
```
XMLSerializable.h:4:19: gdome.h: No such file or directory
``` 

I have added to $PATH:
/usr/lib

where the files: /usr/lib/libgdome.so.0 and /usr/lib/libgdome.so.0.8.1 are located,
but it didn't help.

I've also added to $PATH /usr/include/libgdome where the file gdome.h is located,
but id didn't help either.

How can I make #include to look for gdome.h in the right place?

---

### Post by varunus on 2005-08-29
You need to use package-config to compile libraries you install from synaptic.

An example:

gcc helloworld.c -o helloworld `pkg-config --cflags --libs gtk+-2.0`

Most likely, this library you installed had a ".pc" file included with it (you can check synaptic in the "installed files" section); simply replace "gtk+-2.0" in the above with the name of the .pc file (no extension there, though).

Most likely, you'll need to type the following (if the filename is libgdome-2.0.pc):

gcc filename.c `pkg-config --cflags --libs libgdome-2.0`

Or something like that.

---

### Post by thumper on 2005-08-29
[QUOTE=Guest1234]I have installed via the Synaptic Package Manager the ligbdome2-0 package,
it's a package for manipulating xml/html files using DOM.
I have a class called XMLSerializable, which does include to the following file:
```
#include <gdome.h>
``` 

but when I try to compile Person.cpp that uses this class I get this error message:
```
XMLSerializable.h:4:19: gdome.h: No such file or directory
``` 

I have added to $PATH:
/usr/lib

where the files: /usr/lib/libgdome.so.0 and /usr/lib/libgdome.so.0.8.1 are located,
but it didn't help.

I've also added to $PATH /usr/include/libgdome where the file gdome.h is located, but id didn't help either.[/QUOTE]

PATH is used to find executables not header files.  What you are looking for is the -I or -isystem directive for gcc/g++

[QUOTE=Guest1234]How can I make #include to look for gdome.h in the right place?[/QUOTE]
You might want to try something like this
```
g++ -isystem /usr/include/libgdome test.cpp -o test
```
Also LD_LIBRARY_PATH is used to find the shared object libraries, but /usr/lib is normally checked by default (at least I think it is).

---

### Post by mo_x on 2005-08-29
Maybe you can change the line to:
#include <libgdome/gdome.h>

---

### Post by thumper on 2005-08-29
[QUOTE=mo_x]Maybe you can change the line to:
#include <libgdome/gdome.h>[/QUOTE]
Yeah, I thought of that too, but then you have problems is gdome.h includes any other header files that it expects to be in the same directory (as often happens).

If gdome.h looks anything like this:
```
#ifndef GDOME_H_INCL_GUARD_THINGY
#define GDOME_H_INCL_GUARD_THINGY

#include <gdome_impl.h>
#include <gdome_other.h>

// lots of other stuff

#endif
```
Then if the directory that gdome.h lives in is not in the include path, then the compilation will stop by not finding the others.

That said, if it is a stand alone header file (ie doesn't include anything else), then this suggestion is the easiest and simplest solution.

---

### Post by mo_x on 2005-08-30
You can also add the directory to the gcc search path for inlcude files, I think it's the -I option. It would be something like:
gcc -I/usr/include/libgdome

---

### Post by Kimm on 2005-08-30
Probably a stupid question... but you do have the developement files installed I presume?

---

