---
title: "Help debugging my library"
date: 2007-07-01
forum: Programming Talk
---

### Post by maddog39 on 2007-07-01
Hello all,

Well I've been trying to develop this game development framework to make things really easy for game development in C (or C++). After I get this working, I plan to make some games with it with some friends (Open Source ones of course :D). But I've been running into this problem trying to get the little demo game to run which uses the base library. Everything compiles okay, but it keeps giving me a segmentation fault and i still cant figure out why its doing thing, I tried looking at my structs and data types for anything funky or variables that were getting free'd when they weren't supposed to be, things like that.

So I just end up trying valgrind to see what's going on and it gives me an idea but I still have no clue what the problem might be. Valgrind outputs this:
```

==25642== Memcheck, a memory error detector.
==25642== Copyright (C) 2002-2006, and GNU GPL'd, by Julian Seward et al.
==25642== Using LibVEX rev 1606, a library for dynamic binary translation.
==25642== Copyright (C) 2004-2006, and GNU GPL'd, by OpenWorks LLP.
==25642== Using valgrind-3.2.0-Debian, a dynamic binary instrumentation framework.
==25642== Copyright (C) 2000-2006, and GNU GPL'd, by Julian Seward et al.
==25642== For more details, rerun with: -v
==25642== 
==25642== My PID = 25642, parent PID = 24220.  Prog and args are:
==25642==    ./opdemo
==25642== 
==25642== Invalid write of size 4
==25642==    at 0x804956A: op_timer_init (timer.c:20)
==25642==    by 0x8048BA0: main (main.c:29)
==25642==  Address 0x8 is not stack'd, malloc'd or (recently) free'd
==25642== 
==25642== Process terminating with default action of signal 11 (SIGSEGV)
==25642==  Access not within mapped region at address 0x8
==25642==    at 0x804956A: op_timer_init (timer.c:20)
==25642==    by 0x8048BA0: main (main.c:29)
==25642== 
==25642== ERROR SUMMARY: 1 errors from 1 contexts (suppressed: 47 from 1)
==25642== malloc/free: in use at exit: 0 bytes in 0 blocks.
==25642== malloc/free: 0 allocs, 0 frees, 0 bytes allocated.
==25642== For counts of detected errors, rerun with: -v
==25642== All heap blocks were freed -- no leaks are possible.

```Verbose mode doesnt tell me much else but finds some small errors in other external libraries that seem unrelated. All the source code is on google code (blelow). Any help would be appreciated.
[http://libop.googlecode.com/svn/trunk/](http://libop.googlecode.com/svn/trunk/)

Thanks!
-maddog39

---

### Post by Modred on 2007-07-02
The error is so simple you probably haven't even thought of it.  Your call to **op_timer_init** passes the right type of pointer, but that pointer is not initialized to any memory location, so when you attempt to assign data using that pointer, you segfault.  You need to actually allocate a OP_Timer structure at the memory fps points to before making that call.

The error valgrind's putting out says you tried to write 4 bytes (integer, I assume) onto memory you didn't have access to, and that nothing nearby has recently been allocated or freed.  That told me almost immediately that you were using uninitialized memory.  You'd probably do well to glance through the [valgrind docs](http://valgrind.org/docs/), especially the Quick Start and first few chapters of the User Manual.  Those should help you understand how to read the error reports valgrind produces.

---

### Post by maddog39 on 2007-07-02
Hmmm okay. Im not a total expert on C but I picked up on typedef struct by reading others' code and figured that if you defined a variable with a typedef'd data structure that it would make it like an object and you'd automatically have that data structure embedded pre say. But maybe I missed something. So what exactly do I have to do now, physicially define those variables with the data structure?

[Edit]
Im sort of confused. My original thought on how typedef struct works was right. But no I dont really understand what Im doing wrong then. I was searching google and found this:
[http://www.cs.princeton.edu/~lworthin/126/precepts/structs.html]("http://www.cs.princeton.edu/%7Elworthin/126/precepts/structs.html")
The second half demonstrates typdef with structs. Should I not define them as pointers and then later pass them onto the variables with an ampersand?

---

### Post by Modred on 2007-07-02
You need some good reference materials on pointers.  Here's a cursory glance:

Pointers only point to memory.  It's (mostly) up to you to ensure that memory contains what it should.  Creating a pointer doesn't actually assign anything to the memory the pointer points to.  You need to allocate memory to that space.

```
OP_Timer *fsb;
...
int main() {
...
fsb = malloc( sizeof( OP_Timer ) );
...
/* done with fsb */
free( fsb );
...

```

malloc() sets aside a chunk of memory of the size you ask for, so all I've really done here is request enough memory for an OP_Timer and then assign that pointer to fsb.  From there you should be able to access the data of the OP_Timer.  Note that none of those values are initialized, so they still have junk values until you assign something to them.  After you're done with this object, you should free the memory using free().

[size=1]There may be some other recommended way of doing this same thing only using other libraries, but I'm a bit out of the loop in that regard for the time being.  Regardless, this code should work.[/size]

---

### Post by maddog39 on 2007-07-02
Okay, I see. So when you make a pointer, it only makes sure that you store the data with the specified datatype, but doesnt actually put anything into that memory slot. And yeah I know, I intentionally left them uninitialized which is what the op_*_init() functions do, they handle it in a more dynamic way (sometimes, but thats the idea). I think what I might do is put the malloc and all that in the op_*_init() functions and do it in a way similar to Gtk+.
```
GtkWidget *window = gtk_window_new();
```And make the init functions do all the malloc'ing and stuff. That would work right? This all makes alot more sense now. I guess I only had a basic understanding of pointers before.

Thanks alot btw!

---

### Post by Modred on 2007-07-02
> **maddog39 said:**
> And make the init functions do all the malloc'ing and stuff. That would work right? This all makes alot more sense now. I guess I only had a basic understanding of pointers before.

Thanks alot btw!

Putting malloc inside your init functions should work fine, so long as you use it before attempting to access the memory, since that was your problem.  Plus it makes your code more modular and a little more manageable putting them in the functions.  Just make sure you return the pointer you get from malloc from your function.  (Of course, the mismatched type compiler error would probably keep you from missing that...)

---

### Post by maddog39 on 2007-07-02
Okay, well I implemented it. But now I'm getting errors from GCC when trying to compile the demo game saying:
```

gcc -Wall -g -I./engine -I/usr/include/SDL -D_REENTRANT -c main.c -o main.o
main.c:18: error: initializer element is not constant
main.c:19: error: initializer element is not constant
main.c:20: error: initializer element is not constant

```All changes were committed to SVN.

[Edit]
Okay fixed that problem, i see a small black window for a split second now, so we're getting somewhere. But I got more seg. faults, running valgrind again.

---

### Post by maddog39 on 2007-07-02
Okay, according to valgrind it looks like a memory leak somewhere or some other related problem. I now see a small black window for a split second and then another segmentation fault. I looked at some possible problems and took care of them but it still happens. All my changes were committed to the SVN repository and here is my latest valgrind output. They were both generated with --leak-check=full and one was generated in verbose mode.

[http://www.dximages.uni.cc/files/1/output.txt](http://www.dximages.uni.cc/files/1/output.txt)
[http://www.dximages.uni.cc/files/1/output_verbose.txt](http://www.dximages.uni.cc/files/1/output_verbose.txt)

Thanks!
-maddog39

---

### Post by Modred on 2007-07-02
A lot of these errors appear to be coming from your SDL library.  Like in your op_init_engine(), several of the conditions you're passing to those if statements are part of the backtrace from the error.  So assuming you're doing everything correctly there, it's probably feeding you errors from your libraries (valgrind does this).

You could set up some suppressions to cut out a large number of those errors that aren't yours, but I'll refer you to the valgrind manual for that.

Oh, and your segfault is hitting you when you call op_engine_load_bitmap() from op_sprite_init().  Might pay some attention around that.

---

### Post by maddog39 on 2007-07-02
Okay, well I setup suppressions to ignore all of the SDL and audio (libasound) errors. I looked at op_sprite_init() and it seems to be a problem when I pass on 'engine' a second time to op_engine_load_bitmap() and there's something wrong with the variable at that point, still cant figure out exactly what it is.

[Edit]
Okay, i basically just took out the prefix feature (since I don't use it anyway, although thought that I might) and now it seems to startup successfully and then it crashes because free() trys to free something that has an invalid pointer type, although I think thats just because I dont have any resource files for it yet so it tries to load them and cant and on op_*_exit() functions it tries to free those buffers and what not and finds that they're already null. I get a memory dump when running it, havnt used valgrind yet, but I believe my assumption is right.
```

maddog39@ubuntu:~/Projects/libop$ ./opdemo
open /dev/sequencer: No such file or directory
Error: failed to load bitmap: res/sprite.bmp
Error: failed to play music file: res/music.wav
Error: failed to load bitmap: res/background.bmp
*** glibc detected *** ./opdemo: free(): invalid pointer: 0xbf850880 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7db98bd]
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x84)[0xb7db9a44]
./opdemo[0x8048f5d]
./opdemo[0x8048c50]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7d688cc]
./opdemo[0x8048ae1]
======= Memory map: ========
08048000-0804a000 r-xp 00000000 08:01 21168741   /home/maddog39/Projects/libop/opdemo
0804a000-0804b000 rw-p 00001000 08:01 21168741   /home/maddog39/Projects/libop/opdemo
0804b000-080ae000 rw-p 0804b000 00:00 0          [heap]
b6700000-b6721000 rw-p b6700000 00:00 0 
b6721000-b6800000 ---p b6721000 00:00 0 
b680c000-b680d000 r-xp 00000000 08:01 27410986   /usr/lib/gconv/ISO8859-1.so
b680d000-b680f000 rw-p 00001000 08:01 27410986   /usr/lib/gconv/ISO8859-1.so
b680f000-b6816000 r--s 00000000 08:01 27411044   /usr/lib/gconv/gconv-modules.cache
b6816000-b6817000 rw-p b6816000 00:00 0 
b6817000-b6818000 ---p b6817000 00:00 0 
b6818000-b7018000 rwxp b6818000 00:00 0 
b7018000-b7038000 rw-s 00000000 00:07 11042835   /SYSV0056a4d6 (deleted)
b7038000-b7048000 rw-s 00000000 00:0c 8011       /dev/snd/pcmC0D0p
b7048000-b70c8000 rw-s 00000000 00:07 11010066   /SYSV00000000 (deleted)
b70c8000-b70c9000 ---p b70c8000 00:00 0 
b70c9000-b78c9000 rwxp b70c9000 00:00 0 
b78c9000-b78d2000 r-xp 00000000 08:01 13959988   /lib/tls/i686/cmov/libnss_files-2.4.so
b78d2000-b78d4000 rw-p 00008000 08:01 13959988   /lib/tls/i686/cmov/libnss_files-2.4.so
b78d4000-b78dc000 r-xp 00000000 08:01 13959990   /lib/tls/i686/cmov/libnss_nis-2.4.so
b78dc000-b78de000 rw-p 00007000 08:01 13959990   /lib/tls/i686/cmov/libnss_nis-2.4.so
b78de000-b78f0000 r-xp 00000000 08:01 13959985   /lib/tls/i686/cmov/libnsl-2.4.so
b78f0000-b78f2000 rw-p 00011000 08:01 13959985   /lib/tls/i686/cmov/libnsl-2.4.so
b78f2000-b78f4000 rw-p b78f2000 00:00 0 
b78f4000-b78fb000 r-xp 00000000 08:01 13959986   /lib/tls/i686/cmov/libnss_compat-2.4.so
b78fb000-b78fd000 rw-p 00006000 08:01 13959986   /lib/tls/i686/cmov/libnss_compat-2.4.so
b78fd000-b7905000 r-xp 00000000 08:01 27395300   /usr/lib/libXcursor.so.1.0.2
b7905000-b7906000 rw-p 00007000 08:01 27395300   /usr/lib/libXcursor.so.1.0.2
b7914000-b7930000 r-xp 00000000 08:01 27510043   /usr/lib/X11/locale/common/ximcp.so.2.0.0
b7930000-b7932000 rw-p 0001b000 08:01 27510043   /usr/lib/X11/locale/common/ximcp.so.2.0.0
b7932000-b7934000 r-xp 00000000 08:01 27395141   /usr/lib/libXrandr.so.2.0.0
b7934000-b7935000 rw-p 00002000 08:01 27395141   /usr/lib/libXrandr.so.2.0.0
b7935000-b793c000 r-xp 00000000 08:01 27394999   /usr/lib/libXrender.so.1.3.0
b793c000-b793d000 rw-p 00006000 08:01 27394999   /usr/lib/libXrender.so.1.3.0
b793d000-b7949000 r-xp 00000000 08:01 27395287   /usr/lib/libXext.so.6.4.0
b7949000-b794a000 rw-p 0000c000 08:01 27395287   /usr/lib/libXext.so.6.4.0
b794a000-b794e000 r-xp 00000000 08:01 27395482   /usr/lib/libXdmcp.so.6.0.0
b794e000-b794f000 rw-p 00003000 08:01 27395482   /usr/lib/libXdmcp.so.6.0.0
b794f000-b7951000 r-xp 00000000 08:01 27395423   /usr/lib/libXau.so.6.0.0
b7951000-b7952000 rw-p 00001000 08:01 27395423   /usr/lib/libXau.so.6.0.0
b7952000-b7a18000 r-xp 00000000 08:01 27394189   /usr/lib/libX11.so.6.2.0
b7a18000-b7a1b000 rw-p 000c5000 08:01 27394189   /usr/lib/libX11.so.6.2.0
b7a1b000-b7a1d000 rw-p b7a1b000 00:00 0 
b7a1d000-b7a27000 r-xp 00000000 08:01 13926424   /lib/libgcc_s.so.1
b7a27000-b7a28000 rw-p 00009000 08:01 13926424   /lib/libgcc_s.so.1
b7a28000-b7afc000 r-xp 00000000 08:01 27395248   /usr/lib/libstdc++.so.6.0.8
b7afc000-b7aff000 r--p 000d4000 08:01 27395248   /usr/lib/libstdc++.so.6.0.8
b7aff000-b7b01000 rw-p 000d7000 08:01 27395248   /usr/lib/libstdc++.so.6.0.8
b7b01000-b7b07000 rw-p b7b01000 00:00 0 
b7b07000-b7b40000 r-xp 00000000 08:01 27397052   /usr/lib/libsmpeg-0.4.so.0.1.4
b7b40000-b7b42000 rw-p 00038000 08:01 27397052   /usr/lib/libsmpeg-0.4.so.0.1.4
b7b42000-b7b5e000 rw-p b7b42000 00:00 0 
b7b5e000-b7b62000 r-xp 00000000 08:01 27396376   /usr/lib/libogg.so.0.5.3
b7b62000-b7b63000 rw-p 00003000 08:01 27396376   /usr/lib/libogg.so.0.5.3
b7b63000-b7b64000 rw-p b7b63000 00:00 0 
b7b64000-b7b7d000 r-xp 00000000 08:01 27395969   /usr/lib/libvorbis.so.0.3.1
b7b7d000-b7b8b000 rw-p 00019000 08:01 27395969   /usr/lib/libvorbis.so.0.3.1
b7b8b000-b7b91000 r-xp 00000000 08:01 27395699   /usr/lib/libvorbisfile.so.3.1.1
b7b91000-b7b92000 rw-p 00005000 08:01 27395699   /usr/lib/libvorbisfile.so.3.1.1
b7b92000-b7bf9000 r-xp 00000000 08:01 27395296   /usr/lib/libfreetype.so.6.3.10
b7bf9000-b7bfc000 rw-p 00067000 08:01 27395296   /usr/lib/libfreetype.so.6.3.10
b7bfc000-b7bfe000 r-xp 00000000 08:01 13959982   /lib/tls/i686/cmov/libdl-2.4.so
b7bfe000-b7c00000 rw-p 00001000 08:01 13959982   /lib/tls/i686/cmov/libdl-2.4.so
b7c00000-b7c13000 r-xp 00000000 08:01 27395000   /usr/lib/libz.so.1.2.3
b7c13000-b7c14000 rw-p 00012000 08:01 27395000   /usr/lib/libz.so.1.2.3
b7c14000-b7c20000 r-xp 00000000 08:01 27394269   /usr/lib/libdirect-0.9.so.24.0.0
b7c20000-b7c21000 rw-p 0000c000 08:01 27394269   /usr/lib/libdirect-0.9.so.24.0.0
b7c21000-b7c22000 rw-p b7c21000 00:00 0 
b7c22000-b7c26000 r-xp 00000000 08:01 27394271   /usr/lib/libfusion-0.9.so.24.0.0
b7c26000-b7c27000 rw-p 00003000 08:01 27394271   /usr/lib/libfusion-0.9.so.24.0.0
b7c27000-b7c73000 r-xp 00000000 08:01 27394270   /usr/lib/libdirectfb-0.9.so.24.0.0
b7c73000-b7c75000 rw-p 0004b000 08:01 27394270   /usr/lib/libdirectfb-0.9.so.24.0.0
b7c75000-b7c99000 r-xp 00000000 08:01 13959983   /lib/tls/i686/cmov/libm-2.4.so
b7c99000-b7c9b000 rw-p 00023000 08:01 13959983   /lib/tls/i686/cmov/libm-2.4.so
b7c9b000-b7d4e000 r-xp 00000000 08:01 27394399   /usr/lib/libasound.so.2.0.0
b7d4e000-b7d53000 rw-p 000b2000 08:01 27394399   /usr/lib/libasound.so.2.0.0
b7d53000-b7e80000 r-xp 00000000 08:01 13959979   /lib/tls/i686/cmov/libc-2.4.so
b7e80000-b7e82000 r--p 0012c000 08:01 13959979   /lib/tls/i686/cmov/libc-2.4.so
b7e82000-b7e84000 rw-p 0012e000 08:01 13959979   /lib/tls/i686/cmov/libc-2.4.so
b7e84000-b7e87000 rw-p b7e84000 00:00 0 
b7e87000-b7e96000 r-xp 00000000 08:01 13959993   /lib/tls/i686/cmov/libpthread-2.4.so
b7e96000-b7e98000 rw-p 0000f000 08:01 13959993   /lib/tls/i686/cmov/libpthread-2.4.so
b7e98000-b7e9a000 rw-p b7e98000 00:00 0 
b7e9a000-b7ed3000 r-xp 00000000 08:01 27397054   /usr/lib/libSDL_mixer-1.2.so.0.2.4
b7ed3000-b7ede000 rw-p 00039000 08:01 27397054   /usr/lib/libSDL_mixer-1.2.so.0.2.4
b7ede000-b7f09000 rw-p b7ede000 00:00 0 
b7f09000-b7f0d000 r-xp 00000000 08:01 27397083   /usr/lib/libSDL_ttf-2.0.so.0.6.2
b7f0d000-b7f0e000 rw-p 00003000 08:01 27397083   /usr/lib/libSDL_ttf-2.0.so.0.6.2
b7f0e000-b7f72000 r-xp 00000000 08:01 27396179   /usr/lib/libSDL-1.2.so.0.7.3
b7f72000-b7f74000 rw-p 00064000 08:01 27396179   /usr/lib/libSDL-1.2.so.0.7.3
b7f74000-b7f9c000 rw-p b7f74000 00:00 0 
b7f9c000-b7f9d000 rw-s 81000000 00:0c 8011       /dev/snd/pcmC0D0p
b7f9d000-b7f9e000 r--s 80000000 00:0c 8011       /dev/snd/pcmC0D0p
b7f9e000-b7f9f000 rw-s 00000000 00:07 10944527   /SYSV0056a4d5 (deleted)
b7f9f000-b7fa3000 r-xp 00000000 08:01 27395247   /usr/lib/libXfixes.so.3.1.0
b7fa3000-b7fa4000 rw-p 00003000 08:01 27395247   /usr/lib/libXfixes.so.3.1.0
b7fa4000-b7fa9000 r-xp 00000000 08:01 27510046   /usr/lib/X11/locale/common/xlibi18n.so.2.0.0
b7fa9000-b7faa000 rw-p 00004000 08:01 27510046   /usr/lib/X11/locale/common/xlibi18n.so.2.0.0
b7faa000-b7fac000 rw-p b7faa000 00:00 0 
b7fac000-b7fc5000 r-xp 00000000 08:01 13926416   /lib/ld-2.4.so
b7fc5000-b7fc7000 rw-p 00018000 08:01 13926416   /lib/ld-2.4.so
bf83e000-bf851000 rwxp bf83e000 00:00 0          [stack]
bf851000-bf854000 rw-p bf851000 00:00 0 
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]
Aborted (core dumped)

```
Okay, it runs now, no problem. I just gotta fix a ton of functionality bugs. Thanks alot for the help Modred.

---

