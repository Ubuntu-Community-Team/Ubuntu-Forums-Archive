---
title: "Need help about libglib2.0-0-dbg package"
date: 2009-03-18
forum: Packaging and Compiling Programs
---

### Post by mhexyl on 2009-03-18
I composed a simplest GLib program in C listed blow, and then checked it by Valgrind. The Memcheck tool reported there were several possibly lost blocks. While I was tracing these possibly lost blocks, there were two lines of source code can't be located. The report I have posted blow also. Hence, I installed libglib2.0-0-dbg package through synaptic. Then the possibly lost blocks magically changed into suppressed blocks without any more different operation, and the suppressed number is as similar as before in the report.

I wonder
 1.  Has anyone observed this? Could you reveal the origin for me?

 2.  Is there anybody could tell me how to extracted debug information to separate files just like files in the libglib2.0-0-dbg package? Since I have run the program with the glib compiled by myself and there were several suppressed blocks reported only. I think may be the separation of debug information caused the difference. I want to make a simpler share library with a separate debug information file for experience.

 - The version of reference software I used
    1. Ubuntu 8.04
    2. Valgrind 3.3.0
    3. glib 2.16.6
    4. gcc 4.2.4

 - The program I composed
    #include <glib-object.h>

    int main()
    {
       g_type_init();
       return 0;
    }

 - Compile operation
    gcc empty_glib.c -g -Wall -O0 `pkg-config --cflags --libs gobject-2.0` -o empty_glib

 - Check operation
    G_SLICE=always-malloc G_DEBUG=gc-friendly valgrind --tool=memcheck --leak-check=full ./empty_glib

 - The Valgrind report
    1. Without libglib2.0-0-dbg installing

        ...

==10287== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 17 from 1)
--10287--
--10287-- supp:     17 dl-hack3-1
==10287== malloc/free: in use at exit: 12,868 bytes in 309 blocks.
==10287== malloc/free: 503 allocs, 194 frees, 187,652 bytes allocated.
==10287==
==10287== searching for pointers to 309 not-freed blocks.
==10287== checked 82,596 bytes.
==10287==
==10287== 800 bytes in 20 blocks are possibly lost in loss record 1 of 5
==10287==    at 0x4021BDE: calloc (vg_replace_malloc.c:397)
==10287==    by 0x40BAC44: g_malloc0 (in /usr/lib/libglib-2.0.so.0.1600.6)
==10287==    by 0x40622F4: (within /usr/lib/libgobject-2.0.so.0.1600.6)
==10287==    by 0x4062494: (within /usr/lib/libgobject-2.0.so.0.1600.6)
==10287==    by 0x40651CF: g_type_init_with_debug_flags (in /usr/lib/libgobject-2.0.so.0.1600.6)
==10287==    by 0x4065331: g_type_init (in /usr/lib/libgobject-2.0.so.0.1600.6)
==10287==    by 0x80483D9: main (empty_glib.c:6)
==10287==
==10287== LEAK SUMMARY:
==10287==    definitely lost: 0 bytes in 0 blocks.
==10287==      possibly lost: 800 bytes in 20 blocks.
==10287==    still reachable: 12,068 bytes in 289 blocks.
==10287==         suppressed: 0 bytes in 0 blocks.

        ...

    2. After libglib2.0-0-dbg installed

        ...

==10262== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 17 from 1)
--10262--
--10262-- supp:     17 dl-hack3-1
==10262== malloc/free: in use at exit: 12,868 bytes in 309 blocks.
==10262== malloc/free: 503 allocs, 194 frees, 187,652 bytes allocated.
==10262==
==10262== searching for pointers to 309 not-freed blocks.
==10262== checked 82,596 bytes.
==10262==
==10262== LEAK SUMMARY:
==10262==    definitely lost: 0 bytes in 0 blocks.
==10262==      possibly lost: 0 bytes in 0 blocks.
==10262==    still reachable: 12,068 bytes in 289 blocks.
==10262==         suppressed: 800 bytes in 20 blocks.

        ...

---

### Post by mhexyl on 2009-03-20
I built glib myself and use strip with flag -g and flag --strip-unneeded to strip the debug information. Then at the end of Valgrind execution the result is as same as using the glib installed by synaptic. It's still confusing me that why will use flag like --strip-unneeded, it seems inconvenient rather than effective.

---

