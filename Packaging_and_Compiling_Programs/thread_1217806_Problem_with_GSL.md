---
title: "Problem with GSL"
date: 2009-07-20
forum: Packaging and Compiling Programs
---

### Post by TableChair on 2009-07-20
The program compiled with no errors using the command:

g++ example.cpp $(pkg-config --cflags --libs gsl) -o example

However when I tried to run it I got the error message:

./example: error while loading shared libraries: libgsl.so.0: cannot open shared object file: No such file or directory

I was wondering what I did wrong?

Thanks in advance, I'm relatively new to linux and it took me ages to even get it to compile.

---

### Post by MadCow108 on 2009-07-20
how did you install the library?

sudo apt-get install libgsl0ldbl libgsl0-dev
should install the library and development files and also create the libgsl.so.0 link in /usr/lib (which you are missing)

---

### Post by TableChair on 2009-07-21
> **MadCow108 said:**
> how did you install the library?

sudo apt-get install libgsl0ldbl libgsl0-dev
should install the library and development files and also create the libgsl.so.0 link in /usr/lib (which you are missing)

I just downloaded a tar.gz

Unzipped it, then installed it normally (using the whole make install etc), I think the install readme said it would be installed to the default location which I assumed would be right.

It seems to have installed it all to usr/local and libgsl.so.0 is in usr/local/lib

---

### Post by TableChair on 2009-07-21
> **MadCow108 said:**
> how did you install the library?

sudo apt-get install libgsl0ldbl libgsl0-dev
should install the library and development files and also create the libgsl.so.0 link in /usr/lib (which you are missing)

For future reference is that all I'd need to type?

Previously when I've done stuff like that I had to edit an apt sources file and then apt-get update first

---

### Post by MadCow108 on 2009-07-21
the gsl library is in the main ubuntu repository so you don't have to change anything in the sources list. You usally only need to do that to add new repositories like PPA's.
You can also install it over synaptic if you wish. The posted line was just a console version of installing a package.

Installing stuff over a packet manager is recommended as it is easy to update and deinstall it again. Also the installed files usually land in the right places.

your manual install installed it in /usr/local/lib which by default isn't in the library search path of ubuntu (no idea why).
Thats why it failed to find it.
you could add the path by following these steps:
[http://ubuntuforums.org/showthread.php?t=420008](http://ubuntuforums.org/showthread.php?t=420008)

or you could just create a link to the library in /usr/lib with:
sudo ln -s /usr/local/lib/libgsl.so.0 /usr/lib/libgsl.so.0

you can avoid misplaced files by changing the default installation path in the configure step (if necessary).
Mostly: --prefix=DIR or/and --libdir=DIR

---

### Post by TableChair on 2009-07-21
> **MadCow108 said:**
> the gsl library is in the main ubuntu repository so you don't have to change anything in the sources list. You usally only need to do that to add new repositories like PPA's.
You can also install it over synaptic if you wish. The posted line was just a console version of installing a package.

Installing stuff over a packet manager is recommended as it is easy to update and deinstall it again. Also the installed files usually land in the right places.

your manual install installed it in /usr/local/lib which by default isn't in the library search path of ubuntu (no idea why).
Thats why it failed to find it.
you could add the path by following these steps:
[http://ubuntuforums.org/showthread.php?t=420008](http://ubuntuforums.org/showthread.php?t=420008)

or you could just create a link to the library in /usr/lib with:
sudo ln -s /usr/local/lib/libgsl.so.0 /usr/lib/libgsl.so.0

you can avoid misplaced files by changing the default installation path in the configure step (if necessary).
Mostly: --prefix=DIR or/and --libdir=DIR

For some reason (mostly being an idiot), I forgot to say I'm not actually using ubuntu, but xandros. I'm doing this on an eeepc.

That worked though, thanks so much! I'm finally starting to work out how linux works!

Also, in the Install readme thing, it says the default location is /usr/local, why would they do that when /usr seems a much more natural place for it?

Out of interest what source would I have to use for gsl so apt-get would find it?

---

### Post by iding on 2009-10-01
hi all,

i just install gsl using
sudo apt-get install libgsl0ldbl libgsl0-dev

i have a "test.cpp" which only contains:
#include <gsl/gsl_matrix.h>

i tried to compile using: 
g++ test.cpp

i then get the error message:
/usr/lib/gcc/i486-linux-gnu/4.2.4/../../../../lib/crt1.o: In function `_start':
(.text+0x18 ): undefined reference to `main'
collect2: ld returned 1 exit status

does anyone know why is that?? thanks a lot in advance

---

### Post by MadCow108 on 2009-10-02
you need to link with the gsl libraries.
the easiest way is to use pkg-config (if available)
g++ `pkg-config --libs --cflags gsl` test.cpp

this expands to:
g++ -lgsl -lgslcblas -lm test.cpp

and also a standalone c/c++ program always needs a main function.
so add this to your file
```

int main (int argc, char *argv[])
{
 return 0
}

```

if you want to compile a library give gcc the -c flag which tells it not to invoke the linker

---

### Post by iding on 2009-10-02
wow it works !!!
Thanks a lot !!!

---

