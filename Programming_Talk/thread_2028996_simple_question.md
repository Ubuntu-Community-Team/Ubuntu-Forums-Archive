---
title: "simple question"
date: 2012-07-19
forum: Programming Talk
---

### Post by rockprincess on 2012-07-19
hi there,

i have a simple question, I just set up my new laptop with kubuntu 12.04 and installed the gcc.

a few weeks ago i wrote some simple c code for school, which I was able to run on the old laptop just fine.

now I have problems executing those files, saying I don't have enough permissions.

theresa@kubuntu:~/c$ ls -lha musik.c
-rwxrwxrwx 1 theresa theresa 349 Dez 25  2011 musik.c

here's the code snippet that i'm trying to run (see it's very simple)
```
#include <stdio.h>

int main()
{
  printf("****** Meine Musiktitel ******\n\n");
  
  printf("N = Neuen Eintrag hinzufügen \n");
  printf("L = Eintrag löschen \n");
  printf("F = Musiktitel finden \n");
  printf("A = Alle Einträge anzeigen \n");
  printf("B = Programm beenden \n\n");
  
  printf("Ihre Wahl:");
  
  printf("\n\n");
  return 0;
}
```


When I try to run it by ./musik
I'm getting a "can't execute this file."

earlier i did a gcc -o musik.c musik

this works fine on the old machine.

---

### Post by Lars Noodén on 2012-07-19
musik.c is the source code, it will not run itself but can be compiled using gcc into music.  It is the output of gcc that you want to pay attention to and to try to run, not the input (source code).

---

### Post by rockprincess on 2012-07-19
> **Lars Noodén said:**
> musik.c is the source code, it will not run itself but can be compiled using gcc into music.  It is the output of gcc that you want to pay attention to and to try to run, not the input (source code).

sorry, this was a typo, I meant I was trying to run ./musik

I still get the same error... :(

---

### Post by trent.josephsen on 2012-07-19
If you really did

```
gcc -o musik.c musik
```

you should have gotten an error, or musik.c should have been clobbered, or both. The argument following -o is the output file.

---

### Post by rockprincess on 2012-07-19
> **trent.josephsen said:**
> If you really did

```
gcc -o musik.c musik
```

you should have gotten an error, or musik.c should have been clobbered, or both. The argument following -o is the output file.

i didn't get an error....

should then the correct syntax be?
```
 gcc -c musik.c -o musik 
```

---

### Post by sudodus on 2012-07-19
If you run ```
gcc -o musik musik.c
``` the output file (that is the executable file) is ***musik***.

Then it works when you run ***./musik*** in the same directory (or if you move it to a directory in your path) you can run ***musik***.

It will work wherever you have compatible libraries (unless you compile it including the libraries into the program code).

---

### Post by rockprincess on 2012-07-19
Ok, I get tons of error messages (unfortunately there are only in german, so I won't post them here)....roughly translated they mean 

musik.c:18:582: Warning: Zero-Sign ignored (activated by default)

Could it be that I'm missing some important libraries? Because it's working without any problem on the other machine.

---

### Post by sudodus on 2012-07-19
> **rockprincess said:**
> Ok, I get tons of error messages (unfortunately there are only in german, so I won't post them here)....roughly translated they mean 

musik.c:18:582: Warning: Zero-Sign ignored (activated by default)

Could it be that I'm missing some important libraries? Because it's working without any problem on the other machine.

I think you may have different versions of the libraries. But what happens if you recompile from your source code? Or is your error output from when you compile from the source code?

---

### Post by rockprincess on 2012-07-19
> **sudodus said:**
> I think you may have different versions of the libraries. But what happens if you recompile from your source code? Or is your error output from when you compile from the source code?

yeah, it's the error output when i run
gcc -o musik musik.c

---

### Post by sudodus on 2012-07-19
> **rockprincess said:**
> yeah, it's the error output when i run
gcc -o musik musik.c

It works for me without warning messages.
```
$ gcc -o musik musik.c
$ ./musik
****** Meine Musiktitel ******

N = Neuen Eintrag hinzufügen 
L = Eintrag löschen 
F = Musiktitel finden 
A = Alle Einträge anzeigen 
B = Programm beenden 

Ihre Wahl:
```
Can you run the program afterwards? (If only warning messages, it might be possible to run the program. Error messages will probably stop the compile and link process.)

---

### Post by sudodus on 2012-07-19
Which version and flavour of Ubuntu are you running? And which version of gcc? Run the following commands and post the output in a reply

```
lsb_release -a
```
```
uname -a
```
```
gcc -v
```

---

### Post by sudodus on 2012-07-19
> **trent.josephsen said:**
> If you really did

```
gcc -o musik.c musik
```

you should have gotten an error, or musik.c should have been clobbered, or both. The argument following -o is the output file.
+1
Have you checked that the source file musik.c is OK? Maybe you have added some garbage to it? In that case, start with a clean source file :-)

---

### Post by trent.josephsen on 2012-07-19
sudodus has explained what the -o does, but I thought I'd just add that gcc is notoriously finicky about the order of its arguments, and sometimes the same invocation doesn't work exactly the same way even from one release to the next. I don't know whether or not this affects your invocation. FWIW, make puts the -o musik at the end, like so:

```
cc musik.c -o musik
```

---

### Post by rockprincess on 2012-07-19
lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04 LTS
Release:        12.04
Codename:       precise

Linux concave 3.5.0-5-generic #5-Ubuntu SMP Wed Jul 18 07:35:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Es werden eingebaute Spezifikationen verwendet.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/4.6/lto-wrapper
Ziel: x86_64-linux-gnu
Konfiguriert mit: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.6.3-1ubuntu5' --with-bugurl=file:///usr/share/doc/gcc-4.6/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.6 --enable-shared --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.6 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --enable-plugin --enable-objc-gc --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread-Modell: posix
gcc-Version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5)

---

### Post by rockprincess on 2012-07-19
> **sudodus said:**
> +1
Have you checked that the source file musik.c is OK? Maybe you have added some garbage to it? In that case, start with a clean source file :-)

HOLY SMOKES!!!
you are right! :-O

source file looked totally messed up, last time i checked it looked ok.

Sorry to all for wasting your time :(

---

### Post by sudodus on 2012-07-19
No worries,

We are here to help :-)

---

### Post by rockprincess on 2012-07-19
on the bright side, i have learned an important lesson.
always check the source file first ;)

---

