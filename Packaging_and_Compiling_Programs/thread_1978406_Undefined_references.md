---
title: "Undefined references"
date: 2012-05-11
forum: Packaging and Compiling Programs
---

### Post by newport_j on 2012-05-11
I recently upgraded from Ubuntu 11.04 to Ubuntu 11.10. Everything went as planned execept for a few things. Now whenever I try to compile even the most basic of programs, I get an undefined reference to a trig function(s) and the compile fails.
 
I cannot understand and this simple square.c (attached) is only a small example. A large program produces many undefined references to trig function and log functions.
 
Please not that in the include file section I have placed
 
#include <math.h>
 
that should bring in the trig and math functions. I also use the command line compile options -lm -lrt, see attached screenshot.
 
I have uploaded a screenshot of the output and a copy of my square.c program. They are attached. 
 
What is wrong?
 
Thanks in advance.
 
Newport_j

---

### Post by steeldriver on 2012-05-11
This probably belongs in the Development and Programming subforum, but  I'll take a shot at it (worst case it is a free bump for you)

The error you are seeing is about a missing *definition* - that's a  linker error, it's basically saying it can't find the actual code module  (lib) containing the things declared in your included <math.h>.

Sometimes the link order is important, I would try -lrt -lm (although I'm not familiar with the librt library). If that doesn't work then it suggests a more fundamental problem with your libraries or their locations - you may be able to 'fix' it using LPATH or LD_LIBRARY_PATH but imo it would be better to find out why they aren't where they should be

I'm assuming you installed the build-essential package of course?

---

### Post by oldos2er on 2012-05-11
Moved to Packaging and Compiling Programs.

---

### Post by Bachstelze on 2012-05-11
[font=monospace]-l[/font] flags go at the end of the command line!

---

### Post by steeldriver on 2012-05-11
> **Bachstelze said:**
> [FONT=monospace]-l[/FONT] flags go at the end of the command line!

doh! yes, can't believe I missed that <hangs head in shame> - try

```
gcc square.c -lrt -lm
```or if you want your executable to be called something other than a.out (e.g. 'square')

```
gcc -o square square.c -lrt -lm
```

---

### Post by newport_j on 2012-05-12
That might be it. I upgraded from 11.04 to 11.10 and did not install the build-essential package.

Could that be it?

Thanks in advance.

Newport_j

---

### Post by steeldriver on 2012-05-12
> **newport_j said:**
> 
Could that be it?


it won't hurt, but like Bachstelze pointed out, your main problem is  that you have specified the libs BEFORE your source code file - they  need to go AFTER

---

### Post by newport_j on 2012-05-14
The build essential problem was not the solution. Build essential was already installed. However, I did move command line options  -lm and -lrt to the end of my shell script and it compiled.
 
I have always used (on Ubuntu 11.04 and earlier) the convention gcc -lrt -lm and put these command line options before the files to be compiled. It worked. In fact I have several legacy shell scripts to that effect.
 
Now it seems that I must put them at the end of the command line or shell script. Is this a new convention in Ubuntu 11.10. It sure seems like it was not here before.
 
It did compile.
 
Any help appreciated.
 
 
Newport_j

---

### Post by MadCow108 on 2012-05-14
its due to the new default linker flag --as-needed since ubuntu 11.10
you will have to fix your broken shell scripts.

placing the libraries before the objects was always kind of wrong, e.g. it never worked for static libraries.

---

### Post by roelforg on 2012-05-14
Putting
```

-Wl,--start-group <objects and libraries here, order not important> -Wl,--end-group

```
solves a lot.
It makes the linker search through each and every specified file (between those two flags) to resolve a reference, so the order doesn't really matter.

---

### Post by bregma on 2012-05-14
> **roelforg said:**
> Putting
```

-Wl,--start-group <objects and libraries here, order not important> -Wl,--end-group

```
solves a lot.
It makes the linker search through each and every specified file (between those two flags) to resolve a reference, so the order doesn't really matter.
Er, no.  It forces the entire contents of the library to be included in the final image, whether it's used or not.  For example, [FONT="Courier New"]-Wl,--start-group -lm -Wl,--end-group[/FONT] will add every single math function into the final executable, even if all you do is call sqrt().

It has always been the case that the order of libraries appearing on the liner command line has been important, the ld linker in every version of Unix I've seen, and in several other systems as well, only resolve undefined symbols from libraries appearing later in the list.  This is an important feature for binary formats that support weak linkage (like GNU/Linux does).

Previous versions of the GCC toolchain allowed a binary to be linked with undefined symbols, and often these resolved at run time because the libraries were already loaded for other reasons ... in other words, it just happened to work in most cases (but note: not always).  Unfortunately, this is also a major security hole and could conceivable result in privilege escalation and system compromise.  As a result, the default in the GCC toolchain in Ubuntu 12.04 is to disallow unresolved symbols at link time.

This is a feature, and if you are required to fix the potential security holes in your code as a result, it is a good thing.

---

### Post by roelforg on 2012-05-15
> **bregma said:**
> Er, no. It forces the entire contents of the library to be included in the final image, whether it's used or not. For example, [FONT=Courier New]-Wl,--start-group -lm -Wl,--end-group[/FONT] will add every single math function into the final executable, even if all you do is call sqrt().
 
It has always been the case that the order of libraries appearing on the liner command line has been important, the ld linker in every version of Unix I've seen, and in several other systems as well, only resolve undefined symbols from libraries appearing later in the list. This is an important feature for binary formats that support weak linkage (like GNU/Linux does).
 

 
 
man ld disagrees with you (i'm on oneiric):
[quote=man ld]
       **-(** _archives_ **-)**
       **--start-group** _archives_ **--end-group**
           The _archives_ should be a list of archive files.  They may be either
           explicit file names, or **-l** options.

           The specified archives are searched repeatedly until no new
           undefined references are created.  Normally, an archive is searched
           only once in the order that it is specified on the command line.
           If a symbol in that archive is needed to resolve an undefined
           symbol referred to by an object in an archive that appears later on
           the command line, the linker would not be able to resolve that
           reference.  By grouping the archives, they all be searched
           repeatedly until all possible references are resolved.

           Using this option has a significant performance cost.  It is best
           to use it only when there are unavoidable circular references
           between two or more archives.
[/quote]

---

### Post by MadCow108 on 2012-05-15
> **bregma said:**
> Er, no.  It forces the entire contents of the library to be included in the final image, whether it's used or not.  For example, [FONT="Courier New"]-Wl,--start-group -lm -Wl,--end-group[/FONT] will add every single math function into the final executable, even if all you do is call sqrt().

It has always been the case that the order of libraries appearing on the liner command line has been important, the ld linker in every version of Unix I've seen, and in several other systems as well, only resolve undefined symbols from libraries appearing later in the list.  This is an important feature for binary formats that support weak linkage (like GNU/Linux does).

Previous versions of the GCC toolchain allowed a binary to be linked with undefined symbols, and often these resolved at run time because the libraries were already loaded for other reasons ... in other words, it just happened to work in most cases (but note: not always).  Unfortunately, this is also a major security hole and could conceivable result in privilege escalation and system compromise.  As a result, the default in the GCC toolchain in Ubuntu 12.04 is to disallow unresolved symbols at link time.

This is a feature, and if you are required to fix the potential security holes in your code as a result, it is a good thing.

you are mixing up many things.
for one *--start-group* has nothing to do with static linking. That would be *-Bstatic*
*--start-group* is in principle just permutate the objects until everything is resolved. The result is still going to be a traditional shared library or dynamic executable

similar *--as-needed* has nothing to do with allowing undefined symbols and security.
flags which are relevant for that are *-z defs* for the former and *-PIC* and *-pie* for the latter (which again has little to do with dynamic loading and preloading).

*--as-needed* is just minimize the links placed into the library and imposes the same ordering restriction on shared libraries as it does for static ones (though the technical reason for this is unclear to me). It is just to decrease package interdependencies in the archive.
It is still perfectly legal to create libraries with undefined symbols, though that is only recommended for plugins.

undefined symbols are no security issue, on linux all symbols, even defined, ones can be overridden at runtime unless explicitly forbidden (e.g. setuid binaries to not make privledge escalation to easy)

---

