---
title: "fglrx segfault?"
date: 2010-11-28
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2010-11-28
_Edit: Don't bother reading the errors or code snippets, problem is already solved._


I have ATI Radeon HD 4290 integrated in my PC's motherboard.

And I also have installed Catalyst 10.11, although amdcccle tells me 10.7 is installed. Re-installing catalyst doesnt help, it says 10.7 with all catalyst versions. o.O

I'm working on a very simple FPS game called "Elimination Chamber". It uses OpenGL.

There will be segmentation fault at exit, caused by fglrx. How can I fix this?

```

arho@a91-156-166-231:~/Source/Elimination Chamber$ valgrind --track-origins=yes ./elimination &> valgrind_output_166.txt
Segmentation fault
arho@a91-156-166-231:~/Source/Elimination Chamber$ cat valgrind_output_166.txt 
==2478== Memcheck, a memory error detector
==2478== Copyright (C) 2002-2009, and GNU GPL'd, by Julian Seward et al.
==2478== Using Valgrind-3.6.0.SVN-Debian and LibVEX; rerun with -h for copyright info
==2478== Command: ./elimination
==2478== 
==2478== Conditional jump or move depends on uninitialised value(s)
==2478==    at 0x4E64DF7: ??? (in /usr/lib/libSDL-1.2.so.0.11.3)
==2478==    by 0x4E656BE: ??? (in /usr/lib/libSDL-1.2.so.0.11.3)
==2478==    by 0x4E660DA: ??? (in /usr/lib/libSDL-1.2.so.0.11.3)
==2478==    by 0x4E3A3CF: SDL_PumpEvents (in /usr/lib/libSDL-1.2.so.0.11.3)
==2478==    by 0x4E3A7F8: SDL_PollEvent (in /usr/lib/libSDL-1.2.so.0.11.3)
==2478==    by 0x402581: main (main.c:29)
==2478==  Uninitialised value was created by a heap allocation
==2478==    at 0x4C274A8: malloc (vg_replace_malloc.c:236)
==2478==    by 0x76AE91E: _XEnq (in /usr/lib/libX11.so.6.3.0)
==2478==    by 0x76B6203: ??? (in /usr/lib/libX11.so.6.3.0)
==2478==    by 0x76B68EF: _XReply (in /usr/lib/libX11.so.6.3.0)
==2478==    by 0x76A3E36: XQueryKeymap (in /usr/lib/libX11.so.6.3.0)
==2478==    by 0x4E64F66: ??? (in /usr/lib/libSDL-1.2.so.0.11.3)
==2478==    by 0x4E6C5D0: ??? (in /usr/lib/libSDL-1.2.so.0.11.3)
==2478==    by 0x4E5CC5E: SDL_SetVideoMode (in /usr/lib/libSDL-1.2.so.0.11.3)
==2478==    by 0x402C0B: set_video_mode (renderer.c:87)
==2478==    by 0x402BDC: init_gfx (renderer.c:81)
==2478==    by 0x40245E: main (main.c:20)
==2478== 
800x600 video mode set
Using built-in texture
230 boxes loaded from data/map2.txt
==2478== 
==2478== Process terminating with default action of signal 11 (SIGSEGV)
==2478==  Access not within mapped region at address 0x4033000
==2478==    at 0xB97F39A: ??? (in /usr/lib/dri/fglrx_dri.so)
==2478==    by 0x1000180200000067: ???
==2478==    by 0x110000001C: ???
==2478==    by 0x1000000000027: ???
==2478==    by 0x7FEFFF01F: ???
==2478==  If you believe this happened as a result of a stack
==2478==  overflow in your program's main thread (unlikely but
==2478==  possible), you can try to increase the size of the
==2478==  main thread stack using the --main-stacksize= flag.
==2478==  The main thread stack size used in this run was 8388608.
==2478== 
==2478== HEAP SUMMARY:
==2478==     in use at exit: 2,008,303 bytes in 12,806 blocks
==2478==   total heap usage: 96,793 allocs, 83,987 frees, 94,817,001 bytes allocated
==2478== 
==2478== LEAK SUMMARY:
==2478==    definitely lost: 768 bytes in 10 blocks
==2478==    indirectly lost: 1,234 bytes in 6 blocks
==2478==      possibly lost: 644,135 bytes in 10,954 blocks
==2478==    still reachable: 1,362,166 bytes in 1,836 blocks
==2478==         suppressed: 0 bytes in 0 blocks
==2478== Rerun with --leak-check=full to see details of leaked memory
==2478== 
==2478== For counts of detected and suppressed errors, rerun with: -v
==2478== ERROR SUMMARY: 1 errors from 1 contexts (suppressed: 185305102 from 439)

```

---

### Post by nvteighen on 2010-11-28
I'd bet you're overwriting some pointer or didn't initialize it so that you're getting really weird memory addresses shown by valgrind.

1) Recompile with debugging symbols
2) Run your code using gdb and spot the call that fires the segfault
3) Take a look at the parameters that are being used at that place and check their values... 

Without any further information, it's pretty sure that's the issue. Please, always post some code... This generic solution is all I can give you from valgrind's report.

---

### Post by crazyfuturamanoob on 2010-11-28
I had the program compiled with -g (debugging symbols) when I made the first post. I have always compiled it with debugging symbols.

Here's the output from gdb, doesn't really help:
```

arho@a91-156-166-231:~/Source/Elimination Chamber$ gdb ./elimination 
GNU gdb (GDB) 7.1-ubuntu
Copyright (C) 2010 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /home/arho/Source/Elimination Chamber/elimination...done.
(gdb) run
Starting program: /home/arho/Source/Elimination Chamber/elimination 
[Thread debugging using libthread_db enabled]
[New Thread 0x7ffff3861710 (LWP 2659)]
800x600 video mode set
Using built-in texture
230 boxes loaded from data/map2.txt
[Thread 0x7ffff3861710 (LWP 2659) exited]

Program received signal SIGSEGV, Segmentation fault.
0x00007ffff2a2639a in ?? () from /usr/lib64/dri/fglrx_dri.so
(gdb) bt
#0  0x00007ffff2a2639a in ?? () from /usr/lib64/dri/fglrx_dri.so
#1  0x00007ffff2a7ae8d in ?? () from /usr/lib64/dri/fglrx_dri.so
#2  0x00007ffff2a770fb in ?? () from /usr/lib64/dri/fglrx_dri.so
#3  0x00007ffff28c3397 in ?? () from /usr/lib64/dri/fglrx_dri.so
#4  0x00007ffff28c581e in ?? () from /usr/lib64/dri/fglrx_dri.so
#5  0x00007ffff28729b0 in ?? () from /usr/lib64/dri/fglrx_dri.so
#6  0x00007ffff28bb3f5 in ?? () from /usr/lib64/dri/fglrx_dri.so
#7  0x00007ffff285175b in ?? () from /usr/lib64/dri/fglrx_dri.so
#8  0x00007ffff285189a in ?? () from /usr/lib64/dri/fglrx_dri.so
#9  0x00007ffff20c98ce in ?? () from /usr/lib64/dri/fglrx_dri.so
#10 0x00007ffff165c853 in ?? () from /usr/lib64/dri/fglrx_dri.so
#11 0x00007ffff170fa07 in ?? () from /usr/lib64/dri/fglrx_dri.so
#12 0x00007ffff170fb79 in ?? () from /usr/lib64/dri/fglrx_dri.so
#13 0x00007ffff20ce609 in ?? () from /usr/lib64/dri/fglrx_dri.so
#14 0x00007ffff20f7ec7 in ?? () from /usr/lib64/dri/fglrx_dri.so
#15 0x00007ffff20c821c in ?? () from /usr/lib64/dri/fglrx_dri.so
#16 0x00007ffff20fc267 in ?? () from /usr/lib64/dri/fglrx_dri.so
#17 0x00007ffff20cf1a9 in ?? () from /usr/lib64/dri/fglrx_dri.so
#18 0x00007ffff20cf28c in ?? () from /usr/lib64/dri/fglrx_dri.so
#19 0x00007ffff2a2e8ab in ?? () from /usr/lib64/dri/fglrx_dri.so
#20 0x00007ffff2753d89 in ?? () from /usr/lib64/dri/fglrx_dri.so
#21 0x00007ffff1577a12 in ?? () from /usr/lib64/dri/fglrx_dri.so
#22 0x00007fffffffdfa0 in ?? ()
---Type <return> to continue, or q <return> to quit---
#23 0x00007ffff2a8a051 in ?? () from /usr/lib64/dri/fglrx_dri.so
#24 0x0000000000000000 in ?? ()
(gdb) 

```

I'm not sure what code I should post. The program has 1328 lines of code in 11 files.
If I'm overwriting some pointer or using it without initializing, why doesn't valgrind tell me about it?

I have modified the code a lot since posting this thread, but valgrind output is still the same. Same errors.
The parameters are sane: 800, 600, 0 and SDL_OPENGL. They are passed to SDL_SetVideoMode. And about the fglrx error, ??????

---

### Post by crazyfuturamanoob on 2010-11-28
Here's some code. main.c:
[php]
#include some headers...

int main( int argc, char *argv[] )
{
    if ( SDL_Init(SDL_INIT_EVERYTHING) < 0 )
    {
        printf( "Unable to init SDL: %s\n", SDL_GetError() );
        return 1;
    }

    atexit(SDL_Quit);
    glutInit( &argc, argv );
    init_gfx(); // <-- VALGRIND ERROR

    SDL_WM_SetCaption( "Elimination Chamber", NULL );
    SDL_ShowCursor( 0 );
    load_map( "data/map2.txt" );
    init_player();

    const Uint32 SKIP_TICKS = 1000 / 30;
    Uint32 next_game_tick = SDL_GetTicks() + SKIP_TICKS;
    for( ;; )
    {
        SDL_Event event;
        while (SDL_PollEvent(&event)) // <-- VALGRIND ERROR
        {
            switch (event.type)
            {
                 /// I don't post the rest of main loop, because it's so long
[/php]

<another code snippet removed>

I have added some comments, otherwise the code is exactly the same as it is now.

I think this problem is caused by the crap ATI driver. My code probably triggers a bug in fglrx.so.
That's why neither valgrind or gdb don't know what causes the fglrx.so errors.

---

### Post by crazyfuturamanoob on 2010-12-05
[SIZE="3"]**[COLOR="Red"][s]atexit(SDL_Quit);[/s][/COLOR]**[/SIZE]

Shotgun debugging saved the day.

:guitar:

---

