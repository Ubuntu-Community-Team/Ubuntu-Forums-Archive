---
title: "HOWTO: Creating Simple Game Levels With SDL"
date: 2006-11-30
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2006-11-30
Hi

You can find our latest HOWTO on games development on the Ubuntu Games Developer Resource Wiki!

Heres the link:
[http://ubuntu-gamedev.pbwiki.com/](http://ubuntu-gamedev.pbwiki.com/)

Mike

---

### Post by hod139 on 2006-11-30
I tried running this example and it seg faulted on me.  
```

./maze
Fatal signal: Segmentation Fault (SDL Parachute Deployed)

```After running a backtrace, the problem seems to be line 67
```

(gdb) bt
#0  0xb7eb53d2 in SDL_UpperBlit () from /usr/lib/libSDL-1.2.so.0
#1  0x08048f6d in DrawScene () at maze.cpp:67
#2  0x0804a0b2 in main (argc=1, argv=0xbf831b14) at maze.cpp:440

```

I spent a few minutes looking at the code, and couldn't figure out the bug.  I'll spend more time looking tonight if no one else finds it first.

---

### Post by Mickeysofine1972 on 2006-11-30
Can I ask? did you compile this on a windows or Linux system?

I have compiled this a few time and never gotten that happen myself. Even when I put -Wall on the end of my compile command it only points out that there is a unused SDL_Rect in the Main().

Mike

---

### Post by hod139 on 2006-11-30
Running standard install of Ubuntu Dapper.  Just to be certain, I re-downloaded the tarbal, extracted it, and ran:
```

 g++ `sdl-config --cflags --libs` -o maze maze.cpp -lSDL -lSDL_image
./maze
Fatal signal: Segmentation Fault (SDL Parachute Deployed)

```
When I compile in debug mode, and run gdb, 
```

g++ -g `sdl-config --cflags --libs` -o maze maze.cpp -lSDL -lSDL_image
gdb ./maze
(gdb) run
Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1214110016 (LWP 17969)]
0xb7f083d2 in SDL_UpperBlit () from /usr/lib/libSDL-1.2.so.0
(gdb) bt
#0  0xb7f083d2 in SDL_UpperBlit () from /usr/lib/libSDL-1.2.so.0
#1  0x08048f6d in DrawScene () at maze.cpp:67
#2  0x0804a0b2 in main (argc=1, argv=0xbff86dd4) at maze.cpp:440

```

I'll have more time to look at it tonight, at first glance it isn't obvious what is wrong.

---

