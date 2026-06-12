---
title: "Strangeness with libpng/zlib on Edgy"
date: 2007-02-15
forum: Programming Talk
---

### Post by EReckase on 2007-02-15
I've got a real strangeness that I can't seem to track down.  I've recently built a new machine and put a fresh install of Edgy (32-bit) on it:

ASUS M2N-SLI Deluxe motherboard
AMD Athlon X2 4600+ (65W)
CORSAIR XMS2 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800
XFX GeForce 7900GS PCIe x16 video card

I had some difficulties with the RAM (had to change some of the BIOS settings to get it to work) but I've installed Edgy and Beryl with no major problems.  No overclocking.  System is totally stable...


...except this one nagging problem.  I'm in charge of code maintenance for the flam3 project ([www.flam3.com](www.flam3.com)) and I was running a test of the latest code when I got a segmentation fault.  As it turns out, on a very irregular basis, I'll get segmentation faults when using libpng functions to write out data to a png image.  I've been unable to reproduce this error on my older AMD Turion64 HP Pavilion laptop running Dapper (32-bit).  The fact is, the segfault happens on a very unpredictable basis, so it's extremely hard to track down.  I've run valgrind on the code without finding much, other than some weirdness in the pthreads library that I can't explain....I've backtraced the segfault in gdb, and it happens in the middle of writing out the image data to memory - but since the libpng and zlib libraries are compiled without debugging, it's very hard for me to identify the source of the problem.  Seems like things just 'freak out' in the middle of the compression.

It's hard for me to believe that it's a bug in libpng or zlib - so I'm beginning to suspect hardware.  I've run memtest86+ for a short time to verify that the ram is at least functional, and I've run SP2004 Orthos edition under WinXP without any problems, either.  What else can I check?

If anyone can help me figure out this problem, I'd be eternally grateful.  I'll be happy to post backtrace information, install new versions of libpng or zlib, swap out RAM, anything in order to figure out what's wrong.  :confused:

---

### Post by lnostdal on 2007-02-15
figure out what version of libpng you're currently using .. download the source, matching that version - from the libpng-site (or possibly using apt-source#1) .. compile it with debugging (or do not strip the binaries) .. and make your program link to the resulting local libpng library instead of the global one (that has no debug info)

see man 8 ld.so

#1: i have limited experience using the apt-source tools and deb-packaging in general :)

---

### Post by EReckase on 2007-02-15
Well, I did part of this yesterday.  I actually grabbed the latest libpng source, compiled it, and pointed the flam3 code to use that library instead (is there an easier way other than specifying the library directly in the LIBS variable?).  This bug still happened with the latest libpng exactly as before, backtraced to the deflate function - which calls zlib schtuff, which was compiled without debugging, so I'm stuck again.  I would suspect zlib is the true location of the problem - if it's not my hardware.

I've been unable to compile libpng against zlib compiled from source, however.  Any ideas on how to do that?

I'll post a full backtrace later today...not at the machine currently.

Erik

---

### Post by EReckase on 2007-02-15
OK, I recompiled zlib, used that recompiled library when recompiling libpng, and then recompiled my application with both of the new libraries...


...and NO SEGFAULTS.

Does this mean that there's a bug in the distributed zlib package?

Erik

---

### Post by lnostdal on 2007-02-15
> **EReckase said:**
> Does this mean that there's a bug in the distributed zlib package?

Maybe. Or there might be an actual bug in your code that is only triggered/shown when using the distributed zlib-package, and not in the one you compiled. edit: sometimes only adding debug-symbols will trigger these things

..you are sure you're working with the same versions of zlib/libpng. I mean; is the only difference that you've added debugging symbols?

Maybe you should start isolating the bug. Make a copy of the directory with the source code that triggers it. Then start removing one piece of the code at a time until it doesn't happen any more then undo the last change. Or, you are using threads? You might want to make sure the libraries you're using actually are thread-safe - and/or what they say about using threads.

..i think i'm out of general ideas that might lead you to a quick fix/conclusion.. :}

---

### Post by EReckase on 2007-02-15
Well, how about this?

When I hit the print-screen button on my keyboard to take a screen capture, I irregularly get the exact same segfault/backtrace!  I'll post it shortly.

---

### Post by EReckase on 2007-02-15
Intermittently, I get the following bug report when taking a screenshot:

```
Memory status: size: 63733760 vsize: 0 resident: 63733760 share: 0 rss: 17010688 rss_rlim: 0
CPU usage: start_time: 1171574803 rtime: 0 utime: 70 stime: 0 cutime:70 cstime: 0 timeout: 0 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/gnome-panel-screenshot'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1225701712 (LWP 10190)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb73ed34b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7eaa1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb731b37c in memcpy () from /lib/tls/i686/cmov/libc.so.6
#5  0xb71e0e8d in deflateCopy () from /usr/lib/libz.so.1
#6  0xb71e1a44 in deflateInit_ () from /usr/lib/libz.so.1
#7  0xb71e1f10 in deflate () from /usr/lib/libz.so.1
#8  0xb709c101 in png_write_chunk () from /usr/lib/libpng12.so.0
#9  0xb709c64b in png_write_chunk () from /usr/lib/libpng12.so.0
#10 0xb70a0774 in png_write_row () from /usr/lib/libpng12.so.0
#11 0xb70a0937 in png_write_rows () from /usr/lib/libpng12.so.0
#12 0xb6db0a79 in fill_info ()
   from /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
#13 0x0825a2f8 in ?? ()
#14 0xbfa3e370 in ?? ()
#15 0x00000001 in ?? ()
#16 0x00000400 in ?? ()
#17 0x00000008 in ?? ()
#18 0x00000006 in ?? ()
#19 0x00000000 in ?? ()

Thread 1 (Thread -1225701712 (LWP 10190)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb73ed34b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7eaa1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb731b37c in memcpy () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#5  0xb71e0e8d in deflateCopy () from /usr/lib/libz.so.1
No symbol table info available.
#6  0xb71e1a44 in deflateInit_ () from /usr/lib/libz.so.1
No symbol table info available.
#7  0xb71e1f10 in deflate () from /usr/lib/libz.so.1
No symbol table info available.
#8  0xb709c101 in png_write_chunk () from /usr/lib/libpng12.so.0
No symbol table info available.
#9  0xb709c64b in png_write_chunk () from /usr/lib/libpng12.so.0
No symbol table info available.
#10 0xb70a0774 in png_write_row () from /usr/lib/libpng12.so.0
No symbol table info available.
#11 0xb70a0937 in png_write_rows () from /usr/lib/libpng12.so.0
No symbol table info available.
#12 0xb6db0a79 in fill_info ()
   from /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
No symbol table info available.
#13 0x0825a2f8 in ?? ()
No symbol table info available.
#14 0xbfa3e370 in ?? ()
No symbol table info available.
#15 0x00000001 in ?? ()
No symbol table info available.
#16 0x00000400 in ?? ()
No symbol table info available.
#17 0x00000008 in ?? ()
No symbol table info available.
#18 0x00000006 in ?? ()
No symbol table info available.
#19 0x00000000 in ?? ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()
```

---

