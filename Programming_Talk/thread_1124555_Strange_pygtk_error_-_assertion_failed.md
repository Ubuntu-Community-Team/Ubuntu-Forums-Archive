---
title: "Strange pygtk error - assertion failed"
date: 2009-04-13
forum: Programming Talk
---

### Post by god0fgod on 2009-04-13
```
**
Gdk:ERROR:/build/buildd/gtk+2.0-2.14.4/gdk/gdkregion-generic.c:1082:miUnionNonO: assertion failed: (y1 < y2)
Aborted

```

I also once got on the same thing:

```
*** glibc detected *** python: double free or corruption (fasttop): 0x0a1e3768 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7de7454]
/lib/tls/i686/cmov/libc.so.6[0xb7deaf4d]
/lib/tls/i686/cmov/libc.so.6(realloc+0x106)[0xb7debde6]
/usr/lib/libglib-2.0.so.0(g_realloc+0x3a)[0xb7b5ac6a]
/usr/lib/libgdk-x11-2.0.so.0[0xb743c09d]
/usr/lib/libgdk-x11-2.0.so.0[0xb743b387]
/usr/lib/libgdk-x11-2.0.so.0(gdk_region_union+0xac)[0xb743cb7c]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_maybe_recurse+0x1e2)[0xb7447602]
/usr/lib/libgtk-x11-2.0.so.0[0xb76e3e56]
/usr/lib/libgtk-x11-2.0.so.0[0xb76e50ef]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_queue_resize+0x87)[0xb76ea4f7]
/usr/lib/libgtk-x11-2.0.so.0[0xb75b8726]
/usr/lib/libgtk-x11-2.0.so.0(gtk_label_set_text+0xb0)[0xb75bae50]
/var/lib/python-support/python2.5/gtk-2.0/gtk/_gtk.so[0xb796fa5c]
python(PyEval_EvalFrameEx+0x55c9)[0x80cea39]
python(PyEval_EvalCodeEx+0x685)[0x80d0345]
python[0x811797e]
python(PyObject_Call+0x27)[0x805d867]
python(PyEval_EvalFrameEx+0x4092)[0x80cd502]
python(PyEval_EvalFrameEx+0x6785)[0x80cfbf5]
python(PyEval_EvalFrameEx+0x6785)[0x80cfbf5]
python(PyEval_EvalCodeEx+0x685)[0x80d0345]
python[0x8117891]
python(PyObject_Call+0x27)[0x805d867]
python[0x8063a7a]
python(PyObject_Call+0x27)[0x805d867]
python(PyEval_CallObjectWithKeywords+0x6c)[0x80c850c]
python[0x80f9e68]
/lib/tls/i686/cmov/libpthread.so.0[0xb7f0b50f]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0xb7e59a0e]
======= Memory map: ========
08048000-08144000 r-xp 00000000 07:00 229064     /usr/bin/python2.5
08144000-08145000 r--p 000fb000 07:00 229064     /usr/bin/python2.5
08145000-0816a000 rw-p 000fc000 07:00 229064     /usr/bin/python2.5
0816a000-08170000 rw-p 0816a000 00:00 0 
09939000-0a394000 rw-p 09939000 00:00 0          [heap]
b4900000-b4921000 rw-p b4900000 00:00 0 
b4921000-b4a00000 ---p b4921000 00:00 0 
b4a3f000-b4afe000 r-xp 00000000 07:00 232168     /usr/lib/libapt-pkg-libc6.8-6.so.4.6.0
b4afe000-b4b00000 r--p 000be000 07:00 232168     /usr/lib/libapt-pkg-libc6.8-6.so.4.6.0
b4b00000-b4b01000 rw-p 000c0000 07:00 232168     /usr/lib/libapt-pkg-libc6.8-6.so.4.6.0
b4b19000-b4b37000 r-xp 00000000 07:00 294807     /usr/lib/python2.5/site-packages/apt_pkg.so
b4b37000-b4b38000 r--p 0001d000 07:00 294807     /usr/lib/python2.5/site-packages/apt_pkg.so
b4b38000-b4b3b000 rw-p 0001e000 07:00 294807     /usr/lib/python2.5/site-packages/apt_pkg.so
b4b3b000-b4b6a000 r-xp 00000000 07:00 294353     /usr/lib/python2.5/lib-dynload/pyexpat.so
b4b6a000-b4b6c000 r--p 0002e000 07:00 294353     /usr/lib/python2.5/lib-dynload/pyexpat.so
b4b6c000-b4b6d000 rw-p 00030000 07:00 294353     /usr/lib/python2.5/lib-dynload/pyexpat.so
b4b6d000-b4b6e000 rw-p b4b6d000 00:00 0 
b4b6e000-b4b7e000 r-xp 00000000 07:00 220344     /lib/tls/i686/cmov/libresolv-2.8.90.so
b4b7e000-b4b7f000 r--p 0000f000 07:00 220344     /lib/tls/i686/cmov/libresolv-2.8.90.so
b4b7f000-b4b80000 rw-p 00010000 07:00 220344     /lib/tls/i686/cmov/libresolv-2.8.90.so
b4b80000-b4b82000 rw-p b4b80000 00:00 0 
b4b82000-b4b86000 r-xp 00000000 07:00 220337     /lib/tls/i686/cmov/libnss_dns-2.8.90.so
b4b86000-b4b87000 r--p 00003000 07:00 220337     /lib/tls/i686/cmov/libnss_dns-2.8.90.so
b4b87000-b4b88000 rw-p 00004000 07:00 220337     /lib/tls/i686/cmov/libnss_dns-2.8.90.so
b4b88000-b4b8a000 r-xp 00000000 07:00 644735     /lib/libnss_mdns4_minimal.so.2
b4b8a000-b4b8b000 rw-p 00001000 07:00 644735     /lib/libnss_mdns4_minimal.so.2
b4b9f000-b4ba1000 r-xp 00000000 07:00 294618     /usr/lib/python2.5/lib-dynload/grp.so
b4ba1000-b4ba2000 r--p 00001000 07:00 294618     /usr/lib/python2.5/lib-dynload/grp.so
b4ba2000-b4ba3000 rw-p 00002000 07:00 294618     /usr/lib/python2.5/lib-dynload/grp.so
b4ba3000-b4ba4000 ---p b4ba3000 00:00 0 
b4ba4000-b53a4000 rwxp b4ba4000 00:00 0 
b53a4000-b53a9000 r-xp 00000000 07:00 253006     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-gif.so
b53a9000-b53aa000 r--p 00004000 07:00 253006     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-gif.so
b53aa000-b53ab000 rw-p 00005000 07:00 253006     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloadeAborted

```

While trying to debug the whole thing I got completely lost and it may not just be the certain functions I originally thought could cause the problems. I this case I think it's best to post all of the code. It happens when the player wins and it only happens most of the time but not all of the time. Look at line 526. This is the if statement that runs when the player wins.

The error is probably triggered from something else happening. Maybe I just can't find it or I don't understand anything wrong with it.

If anyone can determine the problem, they are a true genius.

---

