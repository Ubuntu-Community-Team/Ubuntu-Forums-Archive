---
title: "[SOLVED] g++ ld linking problems with external library *very important*"
date: 2008-06-15
forum: Programming Talk
---

### Post by kung fu buntu on 2008-06-15
I am trying to use a third party library (not something from the repos) with my application, but ld complains that it can't find the symbol.
The command is more or less like this:
```
g++ -Wall -ansi -pedantic -pthread -I<source code dir with foobar.h/cpp> -L<dir with libfoobar.a> -lfoobar
```
And in my code I:
```
#include <foobar.h>
```

The compiler understands "things" because I don't have any compilation error. For example, if I call a bogus method it says that the class has no member named like that.
So, the problem is likely with **ld**.

By just declaring a foobar variable in my code I get:> 
g++ -Wall -ansi -pedantic -pthread -I<source code dir with foobar.h/cpp> -L<dir with libfoobar.a> -lfoobar main.cpp -o application
/tmp/ccr82f9q.o: In function blahblah:
file.cpp:80: undefined reference to `foobar::foobar(int)'
file.cpp:84: undefined reference to `foobar::~foobar()'
collect2: ld returned 1 exit status
make: *** [all] Error 1
*** Exited with status: 2 ***



FWIW, I was able to build the 3rd party lib without much problems. Although a weird thing I noticed is that even though its a C++ application it is built with GCC.
And I've tried in the past to build my c++ application with with GCC and it didn't work :-/

I have tried to also use the same compilation command (but using g++) than a sample application for the 3rd party lib, which has a series of -lfoobardep1 -lfoobardep2, but it didn't work. I got exactly the same error :(

I also tried copying foobar.h to my application dir but that didn't help anything either.

Does this has anything to do with static or dynamic linking, or the use of foobar.a or foobar.so, or LD_LIBRARY_PATH?
I don't have any foobar.so so I'm assuming it's like linking with any other lib in /usr/lib/
Do I have to pass any flags to ld?

I've been at this several hours and don't know what to do! :(
I'm desperate! :(
It's a long story... but if I can't get this to work... I'm dead
How can I solve this?

Thank you very much.

---

### Post by kung fu buntu on 2008-06-15
echo "ARRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRGGGGGGGGGGHHHHHH"  >  /dev/null

I solved it. :mad:


The build command should be:
> **g++ main.cpp -o application **-Wall -ansi -pedantic -pthread -I<source code dir with foobar.h/cpp> -L<dir with libfoobar.a> -lfoobar -l<any other libs libfoobar depends on>
It seems the order matters!!! A LOT! And any other lib dependencies by libfoobar should be there as well.

And surprise, I can now replace g++ with gcc.
(Yes I know gcc calls g++ in some way, but it didn't work previously due to this error!)

---

### Post by nvteighen on 2008-06-15
> **kung fu buntu said:**
> echo "ARRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRGGGGGGGGGGHHHHHH"  >  /dev/null

I solved it. :mad:


The build command should be:

It seems the order matters!!! A LOT! And any other lib dependencies by libfoobar should be there as well.

And surprise, I can now replace g++ with gcc.
(Yes I know gcc calls g++ in some way, but it didn't work previously due to this error!)

I'm annoyed. If the library is called (whatever).a, it is meant to be statically linked, so you should be using the -static flag to compile... That would explain ld complaints: without -static, it will search for (whatever).so (a shared library) in the system's library folders (/lib, /usr/lib, and some else too).

The order seems nothing to do with this... I'm almost sure gcc/g++ have no specific order in their arguments.

---

