---
title: "c++ SDL lame problem"
date: 2006-10-17
forum: Programming Talk
---

### Post by Jasper84 on 2006-10-17
I am trying to compile a c++ file with sdl but i get this.

jasper@dhcppc2:~/Desktop/cpp_proj$ g++ -o blehsdl blehsdl.cpp  `sdl-config --cflags --libs`
blehsdl.cpp:2:21: error: sdl/sdl.h: No such file or directory

here is what I was compiling:
#include <sdl/sdl.h>
#include <stdio.h>
main()
{ printf( "\n\nLet try get sdl to work\n\n" ); }

ok, it doesn't do anything with sdl, but it wouldn't work anyway without sdl.h, how do i get sdl.h in there?
I already figured out where it is:
jasper@dhcppc2:/$ sudo find -iname sdl
./usr/include/SDL
But, really, <sdl/sdl.h> or something as simple should work. (already tried variations)

---

### Post by hod139 on 2006-10-17
Try
```

 #include <SDL/SDL.h>

```

And make sure you have the package libsdl1.2-dev installed.

---

### Post by po0f on 2006-10-17
Jasper84,

Linux filesystems are case-sensitive.  Try this:
```
#include <SDL/SDL.h>
#include <cstdio>

int main() {
    printf("Hello world!\n");

    return 0;
}
```

[Here](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=libsdl1.2-dev&version=dapper&arch=i386) is a listing of all the files included with libsdl1.2-dev.

The **#include <cstdio>** is just C++'s way of including C header files, it's perfectly ok (but IIRC deprecated) to include them the way you did.

[EDIT]
Doh, too slow!

---

### Post by hod139 on 2006-10-17
> **po0f said:**
> 
Doh, too slow!
Actually, you raised some good points that I missed.  I failed to realize his code was C++, not C; and as you pointed out there were C++ errors.  You missed one point though (your code is correct, you just didn't draw attention to it), the C++ standard states the main must return int, not void.

---

### Post by Jasper84 on 2006-10-18
I knew it was something as simple as that. (thought i got that combination of sdl.sdl though :???: ) I didn't know #include<stdio.h> was depreciated.
I got a sdl app going and drawed a line on it, so its working. (guess now to add gl, but i have an idea that doesn't require it yet)
Thanks for the Replies!

---

### Post by po0f on 2006-10-18
Jasper84,

Just to clarify:  in C++ you can #include standard C libraries the old way (with stdio.h), or the new way (with cstdio).  Notice that the new way is just the name of the C library with a "c" in front and without the ".h".  Functionally, they are equivalent, but I believe the old way is deprecated (meaning it works, but is not encouraged).

If you need any more help, post back!

---

