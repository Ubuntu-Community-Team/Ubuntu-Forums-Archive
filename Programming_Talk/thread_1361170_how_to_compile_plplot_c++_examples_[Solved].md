---
title: "how to compile plplot c++ examples [Solved]"
date: 2009-12-21
forum: Programming Talk
---

### Post by r.stiltskin on 2009-12-21
I just wasted a lot of time trying to compile one of the plplot c++ examples (specifically, x04.cc) in the plplot9-driver-gnome2 package.  I couldn't find any instructions in the PLplot Reference Manual, and the little information I found online was either obsolete or wrong so I'm posting the very simple solution here to save the next person (or me, in case I forget) some time.

The demos are in /usr/share/doc/plplot9-driver-gnome/examples/c++.

1. modify the header plc++demos.h, changing ```
#include "plstream.h"
```to```
#include <plplot/plstream.h>
``` to conform to the /usr/include directory structure.

2. the required linker instruction is '-lplplotcxxd', so, for example, to compile the program x04.cc and name the executable 'demo', the command is:
```
g++ x04.cc -o demo -lplplotcxxd
```

---

### Post by bubu7 on 2011-11-28
hallo ! I've tried to compile my plplot c++ example, but I received this undefined references:

[HTML]achille@achille-Aspire-5930:~/Programmi/plplot-5.9.9/examples/c++$ g++ x01.cc -o demo -lplplotcxxd
/tmp/ccf0YQbD.o: In function `x01::plot1(int)':
x01.cc:(.text+0x78e): undefined reference to `plstream::poin(int, double const*, double const*, int)'
x01.cc:(.text+0x7c8): undefined reference to `plstream::line(int, double const*, double const*)'
x01.cc:(.text+0x850): undefined reference to `plstream::poin(int, double const*, double const*, int)'
x01.cc:(.text+0x8a6): undefined reference to `plstream::poin(int, double const*, double const*, int)'
/tmp/ccf0YQbD.o: In function `x01::plot2()':
x01.cc:(.text+0xac2): undefined reference to `plstream::line(int, double const*, double const*)'
/tmp/ccf0YQbD.o: In function `x01::plot3()':
x01.cc:(.text+0xc13): undefined reference to `plstream::styl(int, int const*, int const*)'
x01.cc:(.text+0xc8f): undefined reference to `plstream::styl(int, int const*, int const*)'
x01.cc:(.text+0xd63): undefined reference to `plstream::line(int, double const*, double const*)'
collect2: ld returned 1 exit status
achille@achille-Aspire-5930:~/Programmi/plplot-5.9.9/examples/c++$ 
[/HTML]
mabe something wrong in linking library, but i can't understand what...
can someone help me pls ?
thanks in advance,

---

