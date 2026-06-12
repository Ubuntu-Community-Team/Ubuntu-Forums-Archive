---
title: "How to use dmalloc?"
date: 2010-04-15
forum: Programming Talk
---

### Post by Xamuel Alexander on 2010-04-15
Hello,

I'm trying to compile a C program with dmalloc.

I installed dmalloc using:  sudo apt-get install libdmalloc5

That apparently worked with no problems, but if I try to <include dmalloc.h>, the compiler can't find it.

Adding -enable-dmalloc to the Makefile doesn't help.

Do I need to do <include /usr/include/dmalloc.h> or something like that?  Speaking of which, I cannot actually *find* any trace of dmalloc.  How would I determine where apt-get actually downloaded it to?

Thanks very much for helping :)

---

### Post by lisati on 2010-04-15
Moved to "Programming Talk"

---

### Post by falconindy on 2010-04-15
> **Xamuel Alexander said:**
> Hello,

I'm trying to compile a C program with dmalloc.

I installed dmalloc using:  sudo apt-get install libdmalloc5

That apparently worked with no problems, but if I try to <include dmalloc.h>, the compiler can't find it.

Adding -enable-dmalloc to the Makefile doesn't help.

Do I need to do <include /usr/include/dmalloc.h> or something like that?  Speaking of which, I cannot actually *find* any trace of dmalloc.  How would I determine where apt-get actually downloaded it to?

Thanks very much for helping :)
To locate a file:
```
sudo updatedb
locate dmalloc.h
```
The first command is run nightly via cron, but you may as well make sure that your DB is up to date before searching. It *should* be installed to /usr/include. If that's the case, an include should be enough, but you may need to link it as well. Of course, there's also the [official doc](http://dmalloc.com/docs/latest/online/dmalloc_toc.html) which should give you a definitive answer.

Also, I'm not sure if it's a typo on your part, but the way you've mentioned your include is incorrect. They should be:
```
#include <dmalloc.h>
```
...for header files found via the include path.

---

### Post by happyhamster on 2010-04-16
> **Xamuel Alexander said:**
> 
I installed dmalloc using:  sudo apt-get install libdmalloc5

To get dmalloc.h you'll need to install libdmalloc-dev as well. Good luck.

---

### Post by falconindy on 2010-04-16
> **happyhamster said:**
> To get dmalloc.h you'll need to install libdmalloc-dev as well. Good luck.

Aha. How often I forget Ubuntu enjoys splitting packages.

---

### Post by Xamuel Alexander on 2010-04-16
Thanks for the fast help everyone, you guys are really awesome :)

After installing the dev package, dmalloc.h was put in /usr/include as desired.  It seems a little silly to have to install two packages for this: why would anyone get the non-dev version of dmalloc?

Anyway...  now when I try to compile something with #include <dmalloc.h>, the compiler goes spastic, misdiagnosing dozens of syntax errors in standard include files everywhere, and saying eg:

/usr/include/stdlib.h:488: error: conflicting types for 'dmalloc_free'
/usr/include/dmalloc.h:266: error: previous declaration of 'dmalloc_free' was here

That's whether or not -enable-dmalloc is put in Makefile.

If I remove the #include <dmalloc.h>, but keep -enable-dmalloc in the Makefile, then the compiler says:

/usr/bin/ld: warning: cannot find entry symbol nable-dmalloc; defaulting to 0000000008048b50

If I change -enable-dmalloc to --enable-dmalloc, it says:

cc1: error: unrecognized command line option "-fenable-dmalloc"
cc1: error: unrecognized command line option "-fenable-dmalloc"

I've tried reading the official docs, it never says how to actually use dmalloc.  I'm thinking of just throwing up my hands and writing my very own malloc debugger-- that seems like it would be easier than figuring this out :lolflag:

Thanks a lot for helping :)

---

### Post by MadCow108 on 2010-04-16
you have to place #include <dmalloc.h> after #include <stdlib.h> as it defines a macro named malloc which expands into all following headers and overwrites the definition of libc's malloc...
well at least its documented:
> It should be inserted at the bottom of your include files as to not conflict with wother includes

are you sure the -enable-dmalloc flag even exists?

the -e flag is a linker flag for the entry point
and this error message suggests
cannot find entry symbol nable-dmalloc
that it passes -*e*nable-dmalloc to the linker which thinks nable-dmalloc entry point (which its not)

for me it works when following the getting started guide using current ubuntu 9.10 package when I include dmalloc.h last
no extra flags except the -ldmalloc and setup of DMALLOC_OPTIONS enviroment variable, for which there is the program /usr/lib/dmalloc

btw what is the purpose of using it?
maybe using valgrind and its tools would already be enough. They do not require you to change the source and are generally easier to use

---

### Post by Xamuel Alexander on 2010-04-16
Thanks, I got it to compile after changing how includes were done.

I have 3 files:  jprest.c, scgiapi.c, and scgiapi.h.  Both .c files include the .h file.

In order to make it compile I did the following:
1. Remove #include <stdlib.h> from both of the .c files
2. Put #include <stdlib.h> in the .h file
3. Put #include <dmalloc.h> in all 3 files, and put it BELOW the #include <stdlib.h> in scgiapi.h
4. Put -ldmalloc in the Makefile, so the full Makefile is:

all:
        gcc -ldmalloc -Wall -g jprest.c scgiapi.c -o jprest

Now the compile works without errors :guitar:

Soon I will report back whether or not it actually *works*...  *grin*


Re: MadCow108:  The application is periodically segfaulting due to memory corruption.  Since the crash occurs some time *after* the corruption, gdb offers no useful insight.  I'm hoping dmalloc will force a segfault *as soon as the corruption occurs*, or something.

Never used valgrind, I'll have to read about it...

Thanks guys :)

---

### Post by MadCow108 on 2010-04-16
for such kind of problems valgrind and/or a debugger are far better suited
valgrind will report the line number where an illegal memory read/write occures (in addition to much other useful information like memory leaks, uninitialized use, stack overflows, race conditions, heap profiling, speed profiling...)

and with a debugger (like gdb) you can then break in that line or on the segfault and inspect the program state and step through the program line by line

the important feature for you is in the default behavior of valgrind, just type:
valgrind executable

---

### Post by Xamuel Alexander on 2010-04-16
Running with dmalloc  (or with dmalloc+valgrind), the program failed to segfault at all.

So dmalloc seems like it has the potential to make a program more "robust" at the cost of being less efficient (but obviously one shouldn't rely on the "robustness" provided by dmalloc)

Running with valgrind alone (disabling dmalloc), the problem was diagnosed.

It was a very subtle little memory error buried deep in a routine whose whole purpose was to avoid a *different* memory error  9_9

I'm so happy to have finally found that!!!  Seems like now the program is fixed!!  :guitar:

I could never have done it without you guys!  This forum is way better than most the other linux forums out there  ;)

---

