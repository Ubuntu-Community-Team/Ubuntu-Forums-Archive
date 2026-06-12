---
title: "linking : selecting Symbols from 2 or more different dynamic librarie"
date: 2011-09-22
forum: Packaging and Compiling Programs
---

### Post by arkangel on 2011-09-22
Dear People,


I have the following question: 

in libA.so i have a symbol S or function S ,plus another functions. In libB.so I have a better implementation of S, but some basic implementation is not given by libB.so.

How can I tell the linker/compiler to use the symbol S in libB.so and the other functions from libA.so. The problem is that libA.so is given or distributed with no sources, all that i know is the interface 

Thanks in advacne

---

### Post by SevenMachines on 2011-09-22
The linker resolves symbols in order so if you had

* libA: containing function_one() and function_two()
* libB: containing function_two() only

Then if you linked in the order

* -lA -lB: then you get libA's versions of both function_one() and function_two() since the linker finds both in libA it resolves to them
* -lB -lA: then you get libA's version of function_one() but libB's version of function_two() since the linker finds it in libB but needs to search libA too to resolve function_one()

For more advanced switching in and out of functions from different libraries I only can think of using dlopen to retrieve symbols manually rather than some advanced command line options. Maybe someone else knows

---

### Post by MadCow108 on 2011-09-22
I don't think the ordering on the command line will determine the ordering of the library loading at runtime, but I have never tried something like this so I can  be wrong.

What I know is that you can force a library to be loaded before any other with LD_PRELOAD.
E.g. this will first resolve all possible symbols from libb and then continue with the ones in the dso:
```
LD_PRELOAD=libb ./your-executable
```
it will only print a warning message when libb is not found.

but relying on this is a very bad design, this functionality is usually only used in special cases like replacing malloc with a faster/debugging implementation (dmalloc,tcmalloc) or removing fsync calls when data security is not needed (libeatmydata).

---

### Post by SevenMachines on 2011-09-22
The linker ordering places the shared library details in the binary into different load orders so the symbols are resolved differently, using LD_PRELOAD will obviously change this order. It *does* work like this but I'd stress also that I really dont know much about the fine details why, and I certainly wouldnt want to rely on that method. Best avoided, maybe useful in very very special circumstances

Bear in mind, what follows is very much 'as I sort of understand it', and would not be surprised if its utter rubbish :) but anyway...

For example, 
* libtesta.so has funcone() functwo()
* libtestb.so has functwo() funthree()
* Now we have a binary, test, call funcone(), functwo(), and functhree()

With the linking order -ltesta -l testb
```
$ ./testa
A:funcone    A:functwo    B:functhree   
```The binary will show that we're loading libtesta first, resolving symbols from there, then getting functhree() from libtestb
```
Dynamic section at offset 0xe20 contains 23 entries:
  Tag        Type                         Name/Value
 0x0000000000000001 (NEEDED)             Shared library: [libtesta.so]
 0x0000000000000001 (NEEDED)             Shared library: [libtestb.so]
 0x0000000000000001 (NEEDED)             Shared library: [libc.so.6]
```With the order -ltestb -ltesta
```
$ ./testb
A:funcone    B:functwo    B:functhree
```Binary will show we're loading and resolving libtestb first, so we get functwo() from there first
```
Dynamic section at offset 0xe20 contains 23 entries:
  Tag        Type                         Name/Value
 0x0000000000000001 (NEEDED)             Shared library: [libtestb.so]
 0x0000000000000001 (NEEDED)             Shared library: [libtesta.so]
 0x0000000000000001 (NEEDED)             Shared library: [libc.so.6]
```Of course, we can force loading libtesta first and get back to getting functwo() from there instead
```
$ LD_PRELOAD=libtesta.so ./testb
A:funcone    A:functwo    B:functhree
```As I say though, not something I do and my understanding of the detail may be poor. Certainly seems at best very toolchain/architecture dependent I'd imagine.

---

