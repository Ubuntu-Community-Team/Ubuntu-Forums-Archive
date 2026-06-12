---
title: "Ubuntu 12.10 vs 13.04 -- g++ compiler crazyness"
date: 2013-06-28
forum: Programming Talk
---

### Post by Dirich on 2013-06-28
Every time I try a new Ubuntu release my programs stop compiling... Last time I found out they played around with some option and I had to change the order my libraries were listed. This time instead...

First of all the code for the source file tryit.cpp:
```
#include <iostream>
#include "library.hpp"

int main ()
{
    int size = Get_Terminal_Size ();
    std::cout << size << std::endl;
    return 0;
}
```

Then the library.hpp file:
```
#ifndef library_h_
#define library_h_

// Dependecies
#include <sys/ioctl.h>        // ioctl ()
#include <cstdlib>

/*!
    This function determines the current size of the terminal being used.

    @return:            width of the terminal
*/
inline int Get_Terminal_Size ()
{
    // initalized to default value in case the macros are both not defined
    int cols = 80;
//    int lines = 24;

#ifdef TIOCGSIZE
    struct ttysize ts;
    ioctl (STDIN_FILENO, TIOCGSIZE, &ts);
    cols = ts.ts_cols;
//    lines = ts.ts_lines;
#elif defined (TIOCGWINSZ)
    struct winsize ts;
    ioctl (STDIN_FILENO, TIOCGWINSZ, &ts);
    cols = ts.ws_col;
//    lines = ts.ws_row;
#endif /* TIOCGSIZE */

    return cols;
}

#endif /* library_h_ */
```

compile command: g++ -o test tryit.cpp

Ubuntu 12.10 -----> COMPILES!
Ubuntu 13.04 -----> I WISH!

The compilers outputs the following:
```

In file included from tryit.cpp:2:0:
library.hpp: In function ‘int Get_Terminal_Size()’:
library.hpp:26:9: error: ‘STDIN_FILENO’ was not declared in this scope

```

That macro he is crying about is included in unistd.h, which once upon a time I found to be, in some way, included in c++ via cstdlib, although cstdlib is just another way to call stdlib.h, which is a different header than unistd.h.
Anyway, in 12.10 it works, in 13.04 I have to substitute cstdlib with unistd.h, otherwise it does not work.

Can anybody explain to me WHY? /cry

---

### Post by steeldriver on 2013-06-28
It's a gcc 4.7 thing, I think --> [http://gcc.gnu.org/gcc-4.7/porting_to.html](http://gcc.gnu.org/gcc-4.7/porting_to.html)
> 
Many of the standard C++ library include files have been edited to no longer include <unistd.h> to remove [namespace pollution]("http://gcc.gnu.org/PR49745").


---

### Post by Dirich on 2013-06-28
That sounds like it, thanks!
Poor ubuntu guys, I always blame tham... :(

---

