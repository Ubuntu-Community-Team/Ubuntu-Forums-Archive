---
title: "GCC 4.6 linker doesn't work anymore"
date: 2011-10-13
forum: Packaging and Compiling Programs
---

### Post by Pixel42 on 2011-10-13
I upgraded to Ubuntu 11.10. Since then GCC doesn't link anymore. I, for example, compiled a little C program:

```
#include <math.h>                                                                                                                    

int main ()
{
    return (int) fmod (2, 4);
}
```and compiled it with

```
gcc -c -o test.o test.c
```No problem. I got my test.o. Then I do:

```
gcc -lm -o test test.o
```and I get

```
test.o: In function `main':
test.c:(.text+0x44): undefined reference to `fmod'
collect2: ld returned 1 exit status

```This is beyond reason for me. Does this call for a completely new install of Ubuntu?

---

### Post by Bachstelze on 2011-10-13
You're doing it wrong, the command should be

```
gcc -o test test.o -lm
```

---

### Post by Pixel42 on 2011-10-13
Just to avoid some misunderstandings: I got a >10.000 lines project which doesn't compile anymore, either. Only libc symbols find their way in.

---

### Post by Pixel42 on 2011-10-13
Oh my! It works! :) Thank you so much! Live long and prosper, etc. *bow* :)

---

### Post by Bachstelze on 2011-10-13
:)

The new ld is much less tolerant of wrong flag ordering. You have no idea how many packages in the archive were broken because of that.

---

### Post by Pixel42 on 2011-10-13
This really saved my life. But... why is it like that now?

---

### Post by Pixel42 on 2011-10-13
> **Bachstelze said:**
> :)

The new ld is much less tolerant of wrong flag ordering. You have no idea how many packages in the archive were broken because of that.

Oh yes! Yes, I can imagine. :p

---

### Post by MadCow108 on 2011-10-15
> **Pixel42 said:**
> This really saved my life. But... why is it like that now?

11.10 uses the ld flag --as-needed by default now.
This requires the libraries beeing behind the objects needing their symbols on the command line.

---

### Post by chisser98 on 2011-10-15
Hey guys,

I'm happy I found this thread - I was trying to compile my wxWidgets project after upgrading to 11.10 and the linker kept giving me errors.

The only thing is, I use Autotools, and it doesn't put the object files before the library information by default..I had to change the ordering in the Makefiles manually.

Does anyone know how to get Autotools to generate the right order for the linker command(s) automatically???

Thanks :)

Jarrett

---

### Post by chisser98 on 2011-10-15
Post related to my question:
[http://osdir.com/ml/autoconf-gnu/2011-10/msg00024.html]("http://osdir.com/ml/autoconf-gnu/2011-10/msg00024.html")

A workaround is to add ```
CXXFLAGS="$CXXFLAGS -Wl,--no-as-needed"
``` to the configure.ac file.

However, it would be nice if there were a 'proper' way to do this...

Any ideas anyway?

---

### Post by MadCow108 on 2011-10-15
yes fix the build system. Autotools does the right thing, if used correctly.

for autotools its usually simple, put libraries in LIBS or LDADD (LIBADD for libtool) instead of LDFLAGS

---

### Post by chisser98 on 2011-10-15
Right, putting it in LIBS fixed it :)

Thanks MadCow108!

---

### Post by fat yak on 2011-11-28
Thank u soooo much, I have been tearing much hair out over this!!!!

The problem is that when I next have the issue I will have forgotten all about it....

---

