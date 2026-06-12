---
title: "inclusion of header files in c/c++"
date: 2009-07-24
forum: Programming Talk
---

### Post by nipunreddevil on 2009-07-24
if i use only say one function in c or c++,say sqrt from math.h
is there anyway i do not have to import the entire header and import only the part i require.How much will that optimise my code in terms of memory and speed.

---

### Post by jero3n on 2009-07-24
> **nipunreddevil said:**
> if i use only say one function in c or c++,say sqrt from math.h
is there anyway i do not have to import the entire header and import only the part i require.How much will that optimise my code in terms of memory and speed.

You may add a line
```
double sqrt (double x);
```
in your program's body instead of including math.h, but there is absolutely no reason to do so (in fact it is dangerous). There will be no difference in any term. Include files usually contain definitions needed by the compiler at compile time and do not affect the program at runtime.

---

### Post by MindSz on 2009-07-24
Including extra libraries shouldn't make any difference in runtime but it will make your executables a little bigger.

---

### Post by MadCow108 on 2009-07-24
including headers (and the linking with the libraries) will only increase the binary size signicantly if you do static linking
linking dynamically will not have much impact on the size.

but the dynamically linked libraries will be loaded into ram at runtime increasing ram usage.
But also that will mostly not have much effect as programs using the same libraries will all use the same single copy in ram.

---

### Post by jero3n on 2009-07-24
> **MadCow108 said:**
> including headers (and the linking with the libraries) will only increase the binary size signicantly if you do static linking
linking dynamically will not have much impact on the size.


The question was related to including the whole header or not, however I write C for so long, and I did not know that there is size impact when including the whole header file. I am embarrassed :D

Assuming that a typical header file contains only function and structure declarations, does the compiler generate code for this?

---

### Post by CptPicard on 2009-07-24
Uhm... I was under the impression that even static linking pulls in only the stuff that is actually used?

---

### Post by tyfius on 2009-07-24
> **CptPicard said:**
> Uhm... I was under the impression that even static linking pulls in only the stuff that is actually used?True.

Including the header file is not a problem, when linked statically (which is normally done by default for things like that) the linker will only "extract" the required methods into the binary.

So there really isn't much to worry about...

---

### Post by MindSz on 2009-07-24
I don't remember why the size thing happens, but I do remember that the header file is literally included in your code.

So if you do a ```
#include <something.h>
```, the code for 'something.h' will be "written" above your own code at compile time. At least this is what I remember.

As MadCow108 points out, you can do dynamic linking, but if you are working on a system with limited resources (like an embedded system) then you might not want to overload the RAM.

...

Something nice I did while writing this post is to compile a small program and see what the size of my 'a.out' was and then re-compile with a bunch of libraries included (not using any other funcions). Here's what I got:

Program 1 code
```
#include <stdio.h>

int main() {
     printf("HelloWorld!\n");
    return 0;
}
```
Size of binary: 6365 bytes

Program 2 code
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <fcntl.h>
#include <unistd.h>
#include<sys/mman.h>

int main() {
     printf("HelloWorld!\n");
    return 0;
}
```
Size of binary: 6366 bytes

haha well, it's a really insignificant difference :)

---

### Post by jero3n on 2009-07-24
Where did that one byte go? :D

By the way,

> As MadCow108 points out, you can do dynamic linking, but if you are working on a system with limited resources (like an embedded system) then you might not want to overload the RAM.

Linking to a library and including a header file are two different things. I dont know how this linking story started :)

---

### Post by MadCow108 on 2009-07-24
when you include headers and don't link the libraries with the function definition nothing happens (except maybe compilation error "undefined reference")
so there is always linking involved if you seperate your code into several header/code chunks.

the header files are just signature lookups for the compiler. the code itself lies in compiled libraries.
That why there is no difference in Mindsz example. There are more headers included but the compiler actually ignores them as they are not used or the linking is dynamical by default (libm libstdc++ etc. see below).

if you explicitly tell the compiler to statically link the libraries it usally handels by default (g++ -static file.cpp) you will see dramatic changes in the binary size.

to see what your file all links use the ldd command:
```
g++ -static -static-libgcc test.c
$ ldd ./a.out 
	not a dynamic executable

```
compared to:
```

$ g++ test.c
$ ldd ./a.out 
	linux-gate.so.1 =>  (0xb7f6f000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7e68000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7e42000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7e32000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7ccf000)
	/lib/ld-linux.so.2 (0xb7f70000)

```
obviously the first variant will have a much larger binary size.
which headers you include does not matter (modulo linker errors)

---

### Post by jero3n on 2009-07-24
> I write C for so long, and I did not know that there is size impact when including the whole header file. I am embarrassed :D 

Seeing again this, it seems ironic, so I wish to clarify, as it was not my intention. In fact your post combined with OP's question, gave me for a while the impression I was wrong.

Anyway, of course you are absolutely correct about linking, but since you link, there is no difference if you declare only what you use or include the full header or irrelevant headers.

---

### Post by anudeep on 2009-08-21
Hi

I am a novice when coming to linking the C header files in Ubuntu( or anywhere for that matter). 

Can anyone suggest how to link the header files and library files????

I am trying to link hdf5.h

---

### Post by MindSz on 2009-08-21
In gcc you can use the -l swith and specigy a location you want to link.

```
gcc -Wall -l math.h mycode.c
```

---

### Post by anudeep on 2009-08-21
I'm sorry Can yoou be more specific

---

### Post by MindSz on 2009-08-21
when you type '-l' as a switch to the gcc compiler, it looks for the libraries at the path you give it.

hmmm, I don't know how much more specific I can be :P Try typing ```
man gcc
``` or whatever your compiler is and it should give you more information.

The example I posted earlier compiles a program called 'mycode.c' and links the math.h library to it.

---

### Post by dwhitney67 on 2009-08-21
> **MindSz said:**
> ...
hmmm, I don't know how much more specific I can be :P ...
You could try to be concise when you provide instructions and information.  It is just a thought, you know.  You have made two posts in this thread, and both state incorrect information.

The -l (ell) option is used to specify which library will be used during linking.  It is *not* used to specify the path where the library resides.  For that, one must use the -L option.

Also, a header file is not a library... it is a header file!  Generally the library implementation is done in a separate file, and when this is compiled, it is used to form either a shared-object library, or a static library, or both.  A library typically has a name with the format of either lib<name>.so or lib<name>.a, where <name> is the name of the library.

When linking the library with the application, the "lib" prefix and the ".so"/".a" extension are not specified.  Thus for libexample.so, one would compile with something similar to:

```

gcc -I/path/to/libheader SomeApp.c -L/path/to/library -lexample -o myapp

```

---

### Post by MindSz on 2009-08-21
I stand corrected :) Sorry if I confused you!

---

