---
title: "Is this GTK related ? Core dump"
date: 2010-03-01
forum: Programming Talk
---

### Post by dragos2 on 2010-03-01
This is related to [http://ubuntuforums.org/showthread.php?t=1416475](http://ubuntuforums.org/showthread.php?t=1416475)
After fixing that path, the GUI starts fine and when I try to load a file it dumps the core.

GTK version installed
```

ii  libgtk2.0-dev                         2.12.9-3ubuntu5 

```This is the backtrace:

```

Program received signal SIGABRT, Aborted.
[Switching to Thread 0x7f92a9e626f0 (LWP 5231)]
0x00007f92a7a4e095 in raise () from /lib/libc.so.6
(gdb) backtrace
#0  0x00007f92a7a4e095 in raise () from /lib/libc.so.6
#1  0x00007f92a7a4faf0 in abort () from /lib/libc.so.6
#2  0x00007f92a7a88a7b in ?? () from /lib/libc.so.6
#3  0x00007f92a7a9008a in ?? () from /lib/libc.so.6
#4  0x00007f92a7a93c1c in free () from /lib/libc.so.6
#5  0x00000000004194ab in load_file (button=0x6cb8c0, parent=0x0) at load_file.c:47
#6  0x00007f92a8451bbf in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#7  0x00007f92a84657e8 in ?? () from /usr/lib/libgobject-2.0.so.0
#8  0x00007f92a8467245 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#9  0x00007f92a8467633 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#10 0x00007f92a97202c9 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#11 0x00007f92a8451bbf in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#12 0x00007f92a84654be in ?? () from /usr/lib/libgobject-2.0.so.0
#13 0x00007f92a8467245 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#14 0x00007f92a8467633 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#15 0x00007f92a971eb99 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#16 0x00007f92a97e487f in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#17 0x00007f92a8451bbf in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#18 0x00007f92a8465bc8 in ?? () from /usr/lib/libgobject-2.0.so.0
#19 0x00007f92a8466f6f in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#20 0x00007f92a8467633 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#21 0x00007f92a98ebe55 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#22 0x00007f92a97ddb92 in gtk_propagate_event () from /usr/lib/libgtk-x11-2.0.so.0
#23 0x00007f92a97deb35 in gtk_main_do_event () from /usr/lib/libgtk-x11-2.0.so.0
#24 0x00007f92a944858c in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#25 0x00007f92a7db5384 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#26 0x00007f92a7db8695 in ?? () from /usr/lib/libglib-2.0.so.0
#27 0x00007f92a7db89b5 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#28 0x00007f92a97def03 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#29 0x000000000040277e in main (argc=1, argv=0x7fff0f9bf248) at maincGTK.c:91
(gdb) quit

```And this is what is dumped on terminal when running normal (compiled with -g) and trying to load a file:

```

md@deb02:~/fd/cpGUI/sourceCode$ ./cGUI 
*** glibc detected *** ./gcc_costGUI: free(): invalid pointer: 0x00007f355aacfda0 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f355a7e308a]
/lib/libc.so.6(cfree+0x8c)[0x7f355a7e6c1c]
./gcc_costGUI[0x4194ab]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x10f)[0x7f355b1a4bbf]
/usr/lib/libgobject-2.0.so.0[0x7f355b1b87e8]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x855)[0x7f355b1ba245]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x7f355b1ba633]
/usr/lib/libgtk-x11-2.0.so.0[0x7f355c4732c9]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x10f)[0x7f355b1a4bbf]
/usr/lib/libgobject-2.0.so.0[0x7f355b1b84be]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x855)[0x7f355b1ba245]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x7f355b1ba633]
/usr/lib/libgtk-x11-2.0.so.0[0x7f355c471b99]
/usr/lib/libgtk-x11-2.0.so.0[0x7f355c53787f]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x10f)[0x7f355b1a4bbf]
/usr/lib/libgobject-2.0.so.0[0x7f355b1b8bc8]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x57f)[0x7f355b1b9f6f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x7f355b1ba633]
/usr/lib/libgtk-x11-2.0.so.0[0x7f355c63ee55]
/usr/lib/libgtk-x11-2.0.so.0(gtk_propagate_event+0xd2)[0x7f355c530b92]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x2a5)[0x7f355c531b35]
/usr/lib/libgdk-x11-2.0.so.0[0x7f355c19b58c]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1e4)[0x7f355ab08384]
/usr/lib/libglib-2.0.so.0[0x7f355ab0b695]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1d5)[0x7f355ab0b9b5]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xa3)[0x7f355c531f03]
./gcc_costGUI[0x40277e]
/lib/libc.so.6(__libc_start_main+0xf4)[0x7f355a78d1c4]
./gcc_costGUI[0x4026a9]
======= Memory map: ========
00400000-00427000 r-xp 00000000 08:03 4489225                            /home/md/fd/cpGUI/sourceCode/cGUI
00626000-00628000 rw-p 00026000 08:03 4489225                            /home/md/fd/cpGUI/sourceCode/cGUI
00628000-00cf5000 rw-p 00628000 00:00 0                                  [heap]
7f354c000000-7f354c021000 rw-p 7f354c000000 00:00 0 
7f354c021000-7f3550000000 ---p 7f354c021000 00:00 0 
7f355338a000-7f355348e000 rw-p 7f355338a000 00:00 0 
7f355348e000-7f3553515000 r--p 00000000 08:03 10397574                   /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
7f3553515000-7f3553575000 rw-s 00000000 00:09 808779788                  /SYSV00000000 (deleted)
7f3553575000-7f3553584000 r-xp 00000000 08:03 14581886                   /lib/libbz2.so.1.0.4
7f3553584000-7f3553783000 ---p 0000f000 08:03 14581886                   /lib/libbz2.so.1.0.4
7f3553783000-7f3553785000 rw-p 0000e000 08:03 14581886                   /lib/libbz2.so.1.0.4
7f3553785000-7f35538c2000 r-xp 00000000 08:03 10369364                   /usr/lib/libxml2.so.2.6.31
7f35538c2000-7f3553ac2000 ---p 0013d000 08:03 10369364                   /usr/lib/libxml2.so.2.6.31
7f3553ac2000-7f3553acb000 rw-p 0013d000 08:03 10369364                   /usr/lib/libxml2.so.2.6.31
7f3553acb000-7f3553acc000 rw-p 7f3553acb000 00:00 0 
7f3553acc000-7f3553b04000 r-xp 00000000 08:03 10368053                   /usr/lib/libcroco-0.6.so.3.0.1
7f3553b04000-7f3553d03000 ---p 00038000 08:03 10368053                   /usr/lib/libcroco-0.6.so.3.0.1
7f3553d03000-7f3553d07000 rw-p 00037000 08:03 10368053                   /usr/lib/libcroco-0.6.so.3.0.1
7f3553d07000-7f3553d3e000 r-xp 00000000 08:03 10368056                   /usr/lib/libgsf-1.so.114.0.7
7f3553d3e000-7f3553f3d000 ---p 00037000 08:03 10368056                   /usr/lib/libgsf-1.so.114.0.7
7f3553f3d000-7f3553f41000 rw-p 00036000 08:03 10368056                   /usr/lib/libgsf-1.so.114.0.7
7f3553f41000-7f3553f42000 rw-p 7f3553f41000 00:00 0 
7f3553f42000-7f3553f76000 r-xp 00000000 08:03 10368058                   /usr/lib/librsvg-2.so.2.22.2
7f3553f76000-7f3554176000 ---p 00034000 08:03 10368058                   /usr/lib/librsvg-2.so.2.22.2
7f3554176000-7f3554178000 rw-p 00034000 08:03 10368058                   /usr/lib/librsvg-2.so.2.22.2
7f3554178000-7f355417a000 r-xp 00000000 08:03 10437546                   /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
7f355417a000-7f3554379000 ---p 00002000 08:03 10437546                   /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
7f3554379000-7f355437a000 rw-p 00001000 08:03 10437546                   /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
7f355437a000-7f355437e000 r-xp 00000000 08:03 10437481                   /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
7f355437e000-7f355457e000 ---p 00004000 08:03 10437481                   /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
7f355457e000-7f355457f000 rw-p 00004000 08:03 10437481                   /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
7f355457f000-7f355480a000 r--p 00000000 08:03 10437443                   /usr/share/icons/hicolor/icon-theme.cache
7f355480a000-7f3554a0e000 r--p 00000000 08:03 10668443                   /usr/share/icons/Tangerine/icon-theme.cache
7f3554a0e000-7f3554a2d000 r-xp 00000000 08:03 10368166                   /usr/lib/libdbus-glib-1.so.2.1.0
7f3554a2d000-7f3554c2c000 ---p 0001f000 08:03 10368166                   /usr/lib/libdbus-glib-1.so.2.1.0
7f3554c2c000-7f3554c2e000 rw-p 0001e000 08:03 10368166                   /usr/lib/libdbus-glib-1.so.2.1.0
7f3554c2e000-7f3554c38000 r-xp 00000000 08:03 10370358                   /usr/lib/libtrackerclient.so.0.0.0
7f3554c38000-7f3554e37000 ---p 0000a000 08:03 10370358                   /usr/lib/libtrackerclient.so.0.0.0
7f3554e37000-7f3554e38000 rw-p 00009000 08:03 10370358                   /usr/lib/libtrackerclient.so.0.0.0
7f3554e38000-7f3554e5d000 r-xp 00000000 08:03 10592386                   /usr/lib/gio/modules/libgvfsdbus.so
7f3554e5d000-7f355505d000 ---p 00025000 08:03 10592386                   /usr/lib/gio/modules/libgvfsdbus.so
7f355505d000-7f355505f000 rw-p 00025000 08:03 10592386                   /usr/lib/gio/modules/libgvfsdbus.so
7f355505f000-7f3555061000 r-xp 00000000 08:03 14583965                   /lib/libutil-2.7.so
7f3555061000-7f3555260000 ---p 00002000 08:03 14583965                   /lib/libutil-2.7.so
7f3555260000-7f3555262000 rw-p 00001000 08:03 14583965                   /lib/libutil-2.7.so
7f3555262000-7f355529d000 r-xp 00000000 08:03 10367154                   /usr/lib/libdbus-1.so.3.4.0
7f355529d000-7f355549d000 ---p 0003b000 08:03 10367154                   /usr/lib/libdbus-1.so.3.4.0
7f355549d000-7f355549f000 rw-p 0003b000 08:03 10367154                   /usr/lib/libdbus-1.so.3.4.0
7f355549f000-7f35554a7000 r-xp 00000000 08:03 14583962                   /lib/librt-2.7.so
7f35554a7000-7f35556a6000 ---p 00008000 08:03 14583962                   /lib/librt-2.7.so
7f35556a6000-7f35556a8000 rw-p 00007000 08:03 14583962                   /lib/librt-2.7.so
7f35556d9000-7f35556dd000 r-xp 00000000 08:03 10364141                   /usr/lib/libgthread-2.0.so.0.1600.6
7f35556dd000-7f35558dc000 ---p 00004000 08:03 10364141                   /usr/lib/libgthread-2.0.so.0.1600.6
7f35558dc000-7f35558dd000 rw-p 00003000 08:03 10364141                   /usr/lib/libgthread-2.0.so.0.1600.6
7f35558dd000-7f35558ec000 r-xp 00000000 08:03 10368173                   /usr/lib/libhal.so.1.0.0
7f35558ec000-7f3555aeb000 ---p 0000f000 08:03 10368173                   /usr/lib/libhal.so.1.0.0
7f3555aeb000-7f3555aec000 rw-p 0000e000 08:03 10368173                   /usr/lib/libhal.so.1.0.0
7f3555aec000-7f3555b0e000 r-xp 00000000 08:03 10592385                   /usr/lib/gio/modules/libgiohal-volume-monitor.so
7f3555b0e000-7f3555d0e000 ---p 00022000 08:03 10592385                   /usr/lib/gio/modules/libgiohal-volume-monitor.so
7f3555d0e000-7f3555d10000 rw-p 00022000 08:03 10592385                   /usr/lib/gio/modules/libgiohal-volume-monitor.so
7f3555d10000-7f3555d29000 r-xp 00000000 08:03 14581822                   /lib/libselinux.so.1
7f3555d29000-7f3555f29000 ---p 00019000 08:03 14581822                   /lib/libselinux.so.1
7f3555f29000-7f3555f2b000 rw-p 00019000 08:03 14581822                   /lib/libselinux.so.1
7f3555f2b000-7f3555f2c000 rw-p 7f3555f2b000 00:00 0 
7f3555f2c000-7f3555f9b000 r-xp 00000000 08:03 10364137                   /usr/lib/libgio-2.0.so.0.0.0
7f3555f9b000-7f355619a000 ---p 0006f000 08:03 10364137                   /usr/lib/libgio-2.0.so.0.0.0
7f355619a000-7f355619d000 rw-p 0006e000 08:03 10364137                   /usr/lib/libgio-2.0.so.0.0.0
7f355619d000-7f35561a5000 r-xp 00000000 08:03 10453808                   /usr/lib/gtk-2.0/2.10.0/filesystems/libgio.so
7f35561a5000-7f35563a4000 ---p 00008000 08:03 10453808                   /usr/lib/gtk-2.0/2.10.0/filesystems/libgio.so
7f35563a4000-7f35563a5000 rw-p 00007000 08:03 10453808                   /usr/lib/gtk-2.0/2.10.0/filesystems/liAttempting to read from \ufffdbAttempting to read from \ufffdE\ufffdAborted (core dumped)

```

---

### Post by nvteighen on 2010-03-01
Please, post the code. It's impossible to debug that...

EDIT: Don't post the whole thing. Post the load_file.c source file.

---

### Post by dragos2 on 2010-03-01
> **nvteighen said:**
> Please, post the code. It's impossible to debug that...

I can't post the whole program, there are 10 source files and 4 headers.

And the backtrace and dump does not say where the problem may be.

I will try to post isolated and relevant code but any idea from the dump and backtrace what
file can it be ?

---

### Post by pbrane on 2010-03-01
I would say that this is your problem:
```

*** glibc detected *** ./gcc_costGUI: free(): invalid pointer: 0x00007f355aacfda0 ***

```
Somewhere in gcc_costGUI you are calling free() on a pointer that is not valid. One that has either not been initialized or one that has already been *free()*'d. You could always do this:
```

if (pointer)
  free(pointer);

```

Maybe look at gcc_costGUI for pointers that you allocate memory for and look at pointers that are allocated by any called functions. Are you calling load_file() in gcc_costGUI()?

---

### Post by nvteighen on 2010-03-01
> **dragos2 said:**
> I can't post the whole program, there are 10 source files and 4 headers.

And the backtrace and dump does not say where the problem may be.

I will try to post isolated and relevant code but any idea from the dump and backtrace what
file can it be ?

Uf... I edited my post and seems you were too fast for me :P

Ok, like I said above, post the load_file.c file.

---

### Post by gnometorule on 2010-03-01
As others said above, problem should be in load_file.c per your core dump. Compile with -g option (as you already do); then set a break point at or some lines before line 47 in that file (where your program seems to hop off) using gdb. Then single step through from that breakpoint, checking vars around there at each step, in particular whichever pointer is used. That should probably isolate your problem. Repost if that doesn't solve it, with code of that file - although i am not sure that you can solve the issue with just the source code for one file. Gl.

---

