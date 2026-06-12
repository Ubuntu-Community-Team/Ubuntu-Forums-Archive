---
title: "bizar free() error (invalid next size)"
date: 2011-08-09
forum: Programming Talk
---

### Post by solaris235 on 2011-08-09
I have a strange problem that I can't seem to figure out.
I'm developing an authentication routine for a gtk+ app that I'm working on for Ubuntu 10.10 with gnome desktop.
It connects to a mysql database version 5.1.49.
I have two users registered in the database with username, passwordhash and allowed access level.
If I authenticate with the first user in the database everything works fine.
If I authenticate with the second user everything works fine until I destroy the authentication window with gtk_widget_destroy(data->win);
I don't know if the problem is gtk related or mysql related.
The only form of free() that I use is g_free(hash); the same thing happens wether it's there or not.
Any thoughts, suggestion,etc, would be greatly appreciated.

Scroll down for the error, backtrace and code:


here's the error;
*** glibc detected *** /home/ronh/Programming/MWAutomation/Debug/MWAutomation: free(): invalid next size (fast): 0x091efa38 ***

here's the back trace;

======= Backtrace: =========
/lib/libc.so.6(+0x6c501)[0x2cb501]
/lib/libc.so.6(+0x6dd70)[0x2ccd70]
/lib/libc.so.6(cfree+0x6d)[0x2cfe5d]
/lib/libglib-2.0.so.0(g_free+0x36)[0x402486]
/usr/lib/libgtk-x11-2.0.so.0(+0xbc38e)[0x98c38e]
/usr/lib/libgobject-2.0.so.0(g_object_unref+0x1d4)[0x11e994]
/usr/lib/libgtk-x11-2.0.so.0(+0xb3787)[0x983787]
/usr/lib/libgobject-2.0.so.0(g_object_run_dispose+0x7f)[0x11ee8f]
/usr/lib/libgtk-x11-2.0.so.0(gtk_object_destroy+0x7e)[0xa2cfbe]
/usr/lib/libgtk-x11-2.0.so.0(+0x6f325)[0x93f325]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_foreach+0xa4)[0x973824]
/usr/lib/libgtk-x11-2.0.so.0(+0xa40de)[0x9740de]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x7c)[0x12bf2c]
/usr/lib/libgobject-2.0.so.0(+0xaa87)[0x11aa87]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xc0)[0x11c340]
/usr/lib/libgobject-2.0.so.0(+0x22a06)[0x132a06]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x75c)[0x133fac]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x32)[0x134452]
/usr/lib/libgtk-x11-2.0.so.0(+0x15d2b1)[0xa2d2b1]
/usr/lib/libgtk-x11-2.0.so.0(+0x26ba54)[0xb3ba54]
/usr/lib/libgobject-2.0.so.0(g_object_run_dispose+0x7f)[0x11ee8f]
/usr/lib/libgtk-x11-2.0.so.0(gtk_object_destroy+0x7e)[0xa2cfbe]
/usr/lib/libgtk-x11-2.0.so.0(+0x6f325)[0x93f325]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_foreach+0xa4)[0x973824]
/usr/lib/libgtk-x11-2.0.so.0(+0xa40de)[0x9740de]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x7c)[0x12bf2c]
/usr/lib/libgobject-2.0.so.0(+0xaa87)[0x11aa87]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xc0)[0x11c340]
/usr/lib/libgobject-2.0.so.0(+0x22a06)[0x132a06]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x75c)[0x133fac]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x32)[0x134452]
/usr/lib/libgtk-x11-2.0.so.0(+0x15d2b1)[0xa2d2b1]
/usr/lib/libgtk-x11-2.0.so.0(+0x26ba54)[0xb3ba54]
/usr/lib/libgobject-2.0.so.0(g_object_run_dispose+0x7f)[0x11ee8f]
/usr/lib/libgtk-x11-2.0.so.0(gtk_object_destroy+0x7e)[0xa2cfbe]
/usr/lib/libgtk-x11-2.0.so.0(+0x6b1ad)[0x93b1ad]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_foreach+0xa4)[0x973824]
/usr/lib/libgtk-x11-2.0.so.0(+0xa40de)[0x9740de]
/usr/lib/libgtk-x11-2.0.so.0(+0x278f13)[0xb48f13]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x7c)[0x12bf2c]
/usr/lib/libgobject-2.0.so.0(+0xaa87)[0x11aa87]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x192)[0x11c412]
/usr/lib/libgobject-2.0.so.0(+0x22a06)[0x132a06]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x75c)[0x133fac]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x32)[0x134452]
/usr/lib/libgtk-x11-2.0.so.0(+0x15d2b1)[0xa2d2b1]
/usr/lib/libgtk-x11-2.0.so.0(+0x26ba54)[0xb3ba54]
/usr/lib/libgtk-x11-2.0.so.0(+0x27a356)[0xb4a356]
/usr/lib/libgobject-2.0.so.0(g_object_run_dispose+0x7f)[0x11ee8f]
/usr/lib/libgtk-x11-2.0.so.0(gtk_object_destroy+0x7e)[0xa2cfbe]
/home/ronh/Programming/MWAutomation/Debug/MWAutomation[0x804987c]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x7c)[0x12bf2c]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x192)[0x11c412]
/usr/lib/libgobject-2.0.so.0(+0x22b85)[0x132b85]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x75c)[0x133fac]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x32)[0x134452]
/usr/lib/libgtk-x11-2.0.so.0(gtk_button_clicked+0x8a)[0x9472ca]
/usr/lib/libgtk-x11-2.0.so.0(+0x78785)[0x948785]
/usr/lib/libgtk-x11-2.0.so.0(+0x7882c)[0x94882c]
/usr/lib/libgtk-x11-2.0.so.0(+0x135284)[0xa05284]
/usr/lib/libgobject-2.0.so.0(+0xaa87)[0x11aa87]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x192)[0x11c412]
/usr/lib/libgobject-2.0.so.0(+0x227d6)[0x1327d6]
======= Memory map: ========
00110000-00151000 r-xp 00000000 08:01 538675     /usr/lib/libgobject-2.0.so.0.2600.1
00151000-00152000 r--p 00040000 08:01 538675     /usr/lib/libgobject-2.0.so.0.2600.1
00152000-00153000 rw-p 00041000 08:01 538675     /usr/lib/libgobject-2.0.so.0.2600.1
00153000-00161000 r-xp 00000000 08:01 528142     /usr/lib/libXext.so.6.4.0
00161000-00162000 r--p 0000d000 08:01 528142     /usr/lib/libXext.so.6.4.0
00162000-00163000 rw-p 0000e000 08:01 528142     /usr/lib/libXext.so.6.4.0
00163000-00165000 r-xp 00000000 08:01 528152     /usr/lib/libXinerama.so.1.0.0
00165000-00166000 r--p 00001000 08:01 528152     /usr/lib/libXinerama.so.1.0.0
00166000-00167000 rw-p 00002000 08:01 528152     /usr/lib/libXinerama.so.1.0.0
00167000-00173000 r-xp 00000000 08:01 528150     /usr/lib/libXi.so.6.1.0
00173000-00174000 r--p 0000b000 08:01 528150     /usr/lib/libXi.so.6.1.0
00174000-00175000 rw-p 0000c000 08:01 528150     /usr/lib/libXi.so.6.1.0
00175000-0017b000 r-xp 00000000 08:01 528162     /usr/lib/libXrandr.so.2.2.0
0017b000-0017c000 r--p 00005000 08:01 528162     /usr/lib/libXrandr.so.2.2.0
0017c000-0017d000 rw-p 00006000 08:01 528162     /usr/lib/libXrandr.so.2.2.0
0017d000-00187000 r-xp 00000000 08:01 527412     /usr/lib/libpangocairo-1.0.so.0.2800.2
00187000-00188000 r--p 00009000 08:01 527412     /usr/lib/libpangocairo-1.0.so.0.2800.2
00188000-00189000 rw-p 0000a000 08:01 527412     /usr/lib/libpangocairo-1.0.so.0.2800.2
00189000-0018b000 r-xp 00000000 08:01 528134     /usr/lib/libXcomposite.so.1.0.0
0018b000-0018c000 r--p 00001000 08:01 528134     /usr/lib/libXcomposite.so.1.0.0
0018c000-0018d000 rw-p 00002000 08:01 528134     /usr/lib/libXcomposite.so.1.0.0
0018d000-0018f000 r-xp 00000000 08:01 528138     /usr/lib/libXdamage.so.1.1.0
0018f000-00190000 r--p 00001000 08:01 528138     /usr/lib/libXdamage.so.1.1.0
00190000-00191000 rw-p 00002000 08:01 528138     /usr/lib/libXdamage.so.1.1.0
00191000-00195000 r-xp 00000000 08:01 528144     /usr/lib/libXfixes.so.3.1.0
00195000-00196000 r--p 00003000 08:01 528144     /usr/lib/libXfixes.so.3.1.0
00196000-00197000 rw-p 00004000 08:01 528144     /usr/lib/libXfixes.so.3.1.0
00197000-001af000 r-xp 00000000 08:01 528205     /usr/lib/libatk-1.0.so.0.3209.1
001af000-001b0000 ---p 00018000 08:01 528205     /usr/lib/libatk-1.0.so.0.3209.1
001b0000-001b1000 r--p 00018000 08:01 528205     /usr/lib/libatk-1.0.so.0.3209.1
001b1000-001b2000 rw-p 00019000 08:01 528205     /usr/lib/libatk-1.0.so.0.3209.1
001b5000-001b6000 r-xp 00000000 00:00 0          [vdso]
001b6000-0025c000 r-xp 00000000 08:01 531694     /usr/lib/libphidget21.so.0.0.0
0025c000-0025d000 r--p 000a6000 08:01 531694     /usr/lib/libphidget21.so.0.0.0
0025d000-0025e000 rw-p 000a7000 08:01 531694     /usr/lib/libphidget21.so.0.0.0
0025e000-0025f000 rw-p 00000000 00:00 0 
0025f000-003b6000 r-xp 00000000 08:01 928653     /lib/libc-2.12.1.so
003b6000-003b8000 r--p 00157000 08:01 928653     /lib/libc-2.12.1.so
003b8000-003b9000 rw-p 00159000 08:01 928653     /lib/libc-2.12.1.so
003b9000-003bc000 rw-p 00000000 00:00 0 
003bc000-00489000 r-xp 00000000 08:01 921458     /lib/libglib-2.0.so.0.2600.1
00489000-0048a000 r--p 000cc000 08:01 921458     /lib/libglib-2.0.so.0.2600.1
0048a000-0048b000 rw-p 000cd000 08:01 921458     /lib/libglib-2.0.so.0.2600.1
0048b000-0051f000 r-xp 00000000 08:01 528445     /usr/lib/libgdk-x11-2.0.so.0.2200.0
0051f000-00521000 r--p 00094000 08:01 528445     /usr/lib/libgdk-x11-2.0.so.0.2200.0
00521000-00522000 rw-p 00096000 08:01 528445     /usr/lib/libgdk-x11-2.0.so.0.2200.0
00522000-00539000 r-xp 00000000 08:01 528447     /usr/lib/libgdk_pixbuf-2.0.so.0.2200.0
00539000-0053a000 r--p 00017000 08:01 528447     /usr/lib/libgdk_pixbuf-2.0.so.0.2200.0
0053a000-0053b000 rw-p 00018000 08:01 528447     /usr/lib/libgdk_pixbuf-2.0.so.0.2200.0
0053b000-0055f000 r-xp 00000000 08:01 928657     /lib/libm-2.12.1.so
0055f000-00560000 r--p 00023000 08:01 928657     /lib/libm-2.12.1.so
00560000-00561000 rw-p 00024000 08:01 928657     /lib/libm-2.12.1.so
00561000-00584000 r-xp 00000000 08:01 921345     /lib/libpng12.so.0.44.0
00584000-00585000 r--p 00022000 08:01 921345     /lib/libpng12.so.0.44.0
00585000-00586000 rw-p 00023000 08:01 921345     /lib/libpng12.so.0.44.0
00586000-005aa000 r-xp 00000000 08:01 527413     /usr/lib/libpangoft2-1.0.so.0.2800.2
005aa000-005ab000 r--p 00023000 08:01 527413     /usr/lib/libpangoft2-1.0.so.0.2800.2
005ab000-005ac000 rw-p 00024000 08:01 527413     /usr/lib/libpangoft2-1.0.so.0.2800.2
005ac000-005bf000 r-xp 00000000 08:01 919490     /lib/libz.so.1.2.3.4
005bf000-005c0000 r--p 00012000 08:01 919490     /lib/libz.so.1.2.3.4
005c0000-005c1000 rw-p 00013000 08:01 919490     /lib/libz.so.1.2.3.4
005c1000-005c3000 r-xp 00000000 08:01 538676     /usr/lib/libgmodule-2.0.so.0.2600.1
005c3000-005c4000 r--p 00002000 08:01 538676     /usr/lib/libgmodule-2.0.so.0.2600.1
005c4000-005c5000 rw-p 00003000 08:01 538676     /usr/lib/libgmodule-2.0.so.0.2600.1
005c6000-006df000 r-xp 00000000 08:01 528125     /usr/lib/libX11.so.6.3.0
006df000-006e0000 r--p 00118000 08:01 528125     /usr/lib/libX11.so.6.3.0
006e0000-006e2000 rw-p 00119000 08:01 528125     /usr/lib/libX11.so.6.3.0
006e2000-006e3000 rw-p 00000000 00:00 0 
006e3000-00791000 r-xp 00000000 08:01 526971     /usr/lib/libcairo.so.2.11000.0
00791000-00792000 ---p 000ae000 08:01 526971     /usr/lib/libcairo.so.2.11000.0
00792000-00793000 r--p 000ae000 08:01 526971     /usr/lib/libcairo.so.2.11000.0
00793000-00794000 rw-p 000af000 08:01 526971     /usr/lib/libcairo.so.2.11000.0
00794000-00796000 rw-p 00000000 00:00 0 
00796000-007d5000 r-xp 00000000 08:01 526092     /usr/lib/libpango-1.0.so.0.2800.2
007d5000-007d6000 ---p 0003f000 08:01 526092     /usr/lib/libpango-1.0.so.0.2800.2
007d6000-007d7000 r--p 0003f000 08:01 526092     /usr/lib/libpango-1.0.so.0.2800.2
007d7000-007d8000 rw-p 00040000 08:01 526092     /usr/lib/libpango-1.0.so.0.2800.2
007d8000-007db000 r-xp 00000000 08:01 538678     /usr/lib/libgthread-2.0.so.0.2600.1
007db000-007dc000 r--p 00003000 08:01 538678     /usr/lib/libgthread-2.0.so.0.2600.1
007dc000-007dd000 rw-p 00004000 08:01 538678     /usr/lib/libgthread-2.0.so.0.2600.1
007dd000-007e4000 r-xp 00000000 08:01 928669     /lib/librt-2.12.1.so
007e4000-007e5000 r--p 00006000 08:01 928669     /lib/librt-2.12.1.so
007e5000-007e6000 rw-p 00007000 08:01 928669     /lib/librt-2.12.1.so
007e6000-007fb000 r-xp 00000000 08:01 928667     /lib/libpthread-2.12.1.so
007fb000-007fc000 ---p 00015000 08:01 928667     /lib/libpthread-2.12.1.so
007fc000-007fd000 r--p 00015000 08:01 928667     /lib/libpthread-2.12.1.so
007fd000-007fe000 rw-p 00016000 08:01 928667     /lib/libpthread-2.12.1.so
007fe000-00800000 rw-p 00000000 00:00 0 
00802000-0080a000 r-xp 00000000 08:01 528164     /usr/lib/libXrender.so.1.3.0
0080a000-0080b000 r--p 00007000 08:01 528164     /usr/lib/libXrender.so.1.3.0
0080b000-0080c000 rw-p 00008000 08:01 528164     /usr/lib/libXrender.so.1.3.0
0080c000-0081f000 r-xp 00000000 08:01 928659     /lib/libnsl-2.12.1.so
0081f000-00820000 r--p 00012000 08:01 928659     /lib/libnsl-2.12.1.so
00820000-00821000 rw-p 00013000 08:01 928659     /lib/libnsl-2.12.1.so
00821000-00823000 rw-p 00000000 00:00 0 
00823000-00829000 r-xp 00000000 08:01 919477     /lib/libusb-0.1.so.4.4.4
00829000-0082a000 r--p 00005000 08:01 919477     /lib/libusb-0.1.so.4.4.4
0082a000-0082c000 rw-p 00006000 08:01 919477     /lib/libusb-0.1.so.4.4.4
0082c000-0082e000 r-xp 00000000 08:01 928656     /lib/libdl-2.12.1.so
0082e000-0082f000 r--p 00001000 08:01 928656     /lib/libdl-2.12.1.so
0082f000-00830000 rw-p 00002000 08:01 928656     /lib/libdl-2.12.1.so
00830000-00832000 r-xp 00000000 08:01 529089     /usr/lib/libxcb-shm.so.0.0.0
00832000-00833000 r--p 00001000 08:01 529089     /usr/lib/libxcb-shm.so.0.0.0
00833000-00834000 rw-p 00002000 08:01 529089     /usr/lib/libxcb-shm.so.0.0.0
00834000-00836000 r-xp 00000000 08:01 531368     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
00836000-00837000 r--p 00001000 08:01 531368     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
00837000-00838000 rw-p 00002000 08:01 531368     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
00838000-00854000 r-xp 00000000 08:01 928643     /lib/ld-2.12.1.so
00854000-00855000 r--p 0001b000 08:01 928643     /lib/ld-2.12.1.so
00855000-00856000 rw-p 0001c000 08:01 928643     /lib/ld-2.12.1.so
00856000-0085c000 r-xp 00000000 08:01 529087     /usr/lib/libxcb-render.so.0.0.0
0085c000-0085d000 r--p 00005000 08:01 529087     /usr/lib/libxcb-render.so.0.0.0
0085d000-0085e000 rw-p 00006000 08:01 529087     /usr/lib/libxcb-render.so.0.0.0
00860000-00868000 r-xp 00000000 08:01 528136     /usr/lib/libXcursor.so.1.0.2
00868000-00869000 r--p 00007000 08:01 528136     /usr/lib/libXcursor.so.1.0.2
00869000-0086a000 rw-p 00008000 08:01 528136     /usr/lib/libXcursor.so.1.0.2
0086a000-00898000 r-xp 00000000 08:01 528404     /usr/lib/libfontconfig.so.1.4.4
00898000-00899000 r--p 0002d000 08:01 528404     /usr/lib/libfontconfig.so.1.4.4
00899000-0089a000 rw-p 0002e000 08:01 528404     /usr/lib/libfontconfig.so.1.4.4
0089a000-008a3000 r-xp 00000000 08:01 928655     /lib/libcrypt-2.12.1.so
008a3000-008a4000 r--p 00008000 08:01 928655     /lib/libcrypt-2.12.1.so
008a4000-008a5000 rw-p 00009000 08:01 928655     /lib/libcrypt-2.12.1.so
008a5000-008cc000 rw-p 00000000 00:00 0 
008cc000-008ce000 r-xp 00000000 08:01 928672     /lib/libutil-2.12.1.so
008ce000-008cf000 r--p 00001000 08:01 928672     /lib/libutil-2.12.1.so
008cf000-008d0000 rw-p 00002000 08:01 928672     /lib/libutil-2.12.1.so
008d0000-00c98000 r-xp 00000000 08:01 528593     /usr/lib/libgtk-x11-2.0.so.0.2200.0
00c98000-00c9c000 r--p 003c8000 08:01 528593     /usr/lib/libgtk-x11-2.0.so.0.2200.0
00c9c000-00c9e000 rw-p 003cc000 08:01 528593     /usr/lib/libgtk-x11-2.0.so.0.2200.0
00c9e000-00ca0000 rw-p 00000000 00:00 0 
00ca0000-00ca4000 r-xp 00000000 08:01 528140     /usr/lib/libXdmcp.so.6.0.0
00ca4000-00ca5000 r--p 00003000 08:01 528140     /usr/lib/libXdmcp.so.6.0.0
00ca5000-00ca6000 rw-p 00004000 08:01 528140     /usr/lib/libXdmcp.so.6.0.0
00ca6000-00ca8000 r-xp 00000000 08:01 528129     /usr/lib/libXau.so.6.0.0
00ca8000-00ca9000 r--p 00001000 08:01 528129     /usr/lib/libXau.so.6.0.0
00ca9000-00caa000 rw-p 00002000 08:01 528129     /usr/lib/libXau.so.6.0.0
00caa000-00cb0000 r-xp 00000000 08:01 928660     /lib/libnss_compat-2.12.1.so
00cb0000-00cb1000 r--p 00006000 08:01 928660     /lib/libnss_compat-2.12.1.so
00cb1000-00cb2000 rw-p 00007000 08:01 928660     /lib/libnss_compat-2.12.1.so
00cb2000-00e58000 r-xp 00000000 08:01 537441     /usr/lib/libmysqlclient.so.16.0.0
00e58000-00e5b000 r--p 001a5000 08:01 537441     /usr/lib/libmysqlclient.so.16.0.0
00e5b000-00ea0000 rw-p 001a8000 08:01 537441     /usr/lib/libmysqlclient.so.16.0.0
00ea0000-00ea1000 rw-p 00000000 00:00 0 
00ea1000-00f89000 r-xp 00000000 08:01 538684     /usr/lib/libgio-2.0.so.0.2600.1
00f89000-00f8b000 r--p 000e7000 08:01 538684     /usr/lib/libgio-2.0.so.0.2600.1
00f8b000-00f8c000 rw-p 000e9000 08:01 538684     /usr/lib/libgio-2.0.so.0.2600.1
00f8c000-00f8d000 rw-p 00000000 00:00 0 
00f8d000-00fff000 r-xp 00000000 08:01 538952     /usr/lib/libfreetype.so.6.6.0
00fff000-01003000 r--p 00071000 08:01 538952     /usr/lib/libfreetype.so.6.6.0
01003000-01004000 rw-p 00075000 08:01 538952     /usr/lib/libfreetype.so.6.6.0
01004000-01031000 r-xp 00000000 08:01 532261     /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
01031000-01032000 r--p 0002c000 08:01 532261     /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
01032000-01033000 rw-p 0002d000 08:01 532261     /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
01286000-01290000 r-xp 00000000 08:01 928662     /lib/libnss_files-2.12.1.so
01290000-01291000 r--p 00009000 08:01 928662     /lib/libnss_files-2.12.1.so
01291000-01292000 rw-p 0000a000 08:01 928662     /lib/libnss_files-2.12.1.so
013dc000-013ff000 r-xp 00000000 08:01 527671     /usr/lib/gio/modules/libgvfsdbus.so
013ff000-01400000 r--p 00022000 08:01 527671     /usr/lib/gio/modules/libgvfsdbus.so
01400000-01401000 rw-p 00023000 08:01 527671     /usr/lib/gio/modules/libgvfsdbus.so
016ec000-016f3000 r-xp 00000000 08:01 532262     /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
016f3000-016f4000 ---p 00007000 08:01 532262     /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
016f4000-016f5000 r--p 00007000 08:01 532262     /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
016f5000-016f6000 rw-p 00008000 08:01 532262     /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
021cf000-02209000 r-xp 00000000 08:01 527678     /usr/lib/libibus.so.2.0.0
02209000-0220a000 r--p 00039000 08:01 527678     /usr/lib/libibus.so.2.0.0
0220a000-0220b000 rw-p 0003a000 08:01 527678     /usr/lib/libibus.so.2.0.0
03165000-0316e000 r-xp 00000000 08:01 928664     /lib/libnss_nis-2.12.1.so
0316e000-0316f000 r--p 00008000 08:01 928664     /lib/libnss_nis-2.12.1.so
0316f000-03170000 rw-p 00009000 08:01 928664     /lib/libnss_nis-2.12.1.so
031a5000-031a9000 r-xp 00000000 08:01 525867     /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
031a9000-031aa000 r--p 00003000 08:01 525867     /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
031aa000-031ab000 rw-p 00004000 08:01 525867     /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
032f2000-0330c000 r-xp 00000000 08:01 919375     /lib/libgcc_s.so.1
0330c000-0330d000 r--p 00019000 08:01 919375     /lib/libgcc_s.so.1
0330d000-0330e000 rw-p 0001a000 08:01 919375     /lib/libgcc_s.so.1
03358000-03366000 r-xp 00000000 08:01 528260     /usr/lib/libcanberra.so.0.2.4
03366000-03367000 r--p 0000d000 08:01 528260     /usr/lib/libcanberra.so.0.2.4
03367000-03368000 rw-p 0000e000 08:01 528260     /usr/lib/libcanberra.so.0.2.4
036cf000-036f5000 r-xp 00000000 08:01 529048     /usr/lib/libvorbis.so.0.4.4
036f5000-036f6000 r--p 00025000 08:01 529048     /usr/lib/libvorbis.so.0.4.4
036f6000-036f7000 rw-p 00026000 08:01 529048     /usr/lib/libvorbis.so.0.4.4
03ff5000-0400d000 r-xp 00000000 08:01 529091     /usr/lib/libxcb.so.1.1.0
0400d000-0400e000 r--p 00017000 08:01 529091     /usr/lib/libxcb.so.1.1.0
0400e000-0400f000 rw-p 00018000 08:01 529091     /usr/lib/libxcb.so.1.1.0
04631000-04636000 r-xp 00000000 08:01 528812     /usr/lib/libogg.so.0.7.0
04636000-04637000 r--p 00004000 08:01 528812     /usr/lib/libogg.so.0.7.0
04637000-04638000 rw-p 00005000 08:01 528812     /usr/lib/libogg.so.0.7.0
04d7f000-04ddb000 r-xp 00000000 08:01 528855     /usr/lib/libpixman-1.so.0.18.4
04ddb000-04dde000 r--p 0005c000 08:01 528855     /usr/lib/libpixman-1.so.0.18.4
04dde000-04ddf000 rw-p 0005f000 08:01 528855     /usr/lib/libpixman-1.so.0.18.4
055ab000-055b2000 r-xp 00000000 08:01 528735     /usr/lib/libltdl.so.7.2.1
055b2000-055b3000 r--p 00006000 08:01 528735     /usr/lib/libltdl.so.7.2.1
055b3000-055b4000 rw-p 00007000 08:01 528735     /usr/lib/libltdl.so.7.2.1
05b93000-05ba0000 r-xp 00000000 08:01 528997     /usr/lib/libtdb.so.1.2.1
05ba0000-05ba1000 r--p 0000c000 08:01 528997     /usr/lib/libtdb.so.1.2.1
05ba1000-05ba2000 rw-p 0000d000 08:01 528997     /usr/lib/libtdb.so.1.2.1
06672000-06677000 r-xp 00000000 08:01 532283     /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
06677000-06678000 r--p 00004000 08:01 532283     /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
06678000-06679000 rw-p 00005000 08:01 532283     /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
06711000-0674b000 r-xp 00000000 08:01 919444     /lib/libdbus-1.so.3.5.2
0674b000-0674c000 r--p 00039000 08:01 919444     /lib/libdbus-1.so.3.5.2
0674c000-0674d000 rw-p 0003a000 08:01 919444     /lib/libdbus-1.so.3.5.2
06c50000-06c6a000 r-xp 00000000 08:01 919457     /lib/libselinux.so.1
06c6a000-06c6b000 r--p 00019000 08:01 919457     /lib/libselinux.so.1
06c6b000-06c6c000 rw-p 0001a000 08:01 919457     /lib/libselinux.so.1
08048000-0804a000 r-xp 00000000 08:01 3419405    /home/ronh/Programming/MWAutomation/Debug/MWAutomation
0804a000-0804b000 r--p 00001000 08:01 3419405    /home/ronh/Programming/MWAutomation/Debug/MWAutomation
0804b000-0804c000 rw-p 00002000 08:01 3419405    /home/ronh/Programming/MWAutomation/Debug/MWAutomation
083a6000-083b6000 r-xp 00000000 08:01 928668     /lib/libresolv-2.12.1.so
083b6000-083b7000 r--p 00010000 08:01 928668     /lib/libresolv-2.12.1.so
083b7000-083b8000 rw-p 00011000 08:01 928668     /lib/libresolv-2.12.1.so
083b8000-083ba000 rw-p 00000000 00:00 0 
08514000-0851e000 r-xp 00000000 08:01 921364     /lib/libudev.so.0.9.1
0851e000-0851f000 r--p 00009000 08:01 921364     /lib/libudev.so.0.9.1
0851f000-08520000 rw-p 0000a000 08:01 921364     /lib/libudev.so.0.9.1
08536000-08549000 r-xp 00000000 08:01 525696     /usr/lib/libgvfscommon.so.0.0.0
08549000-0854a000 r--p 00012000 08:01 525696     /usr/lib/libgvfscommon.so.0.0.0
0854a000-0854b000 rw-p 00013000 08:01 525696     /usr/lib/libgvfscommon.so.0.0.0
088a7000-088ae000 r-xp 00000000 08:01 529052     /usr/lib/libvorbisfile.so.3.3.2
088ae000-088af000 r--p 00006000 08:01 529052     /usr/lib/libvorbisfile.so.3.3.2
088af000-088b0000 rw-p 00007000 08:01 529052     /usr/lib/libvorbisfile.so.3.3.2
0894e000-08952000 r-xp 00000000 08:01 528258     /usr/lib/libcanberra-gtk.so.0.1.6
08952000-08953000 r--p 00003000 08:01 528258     /usr/lib/libcanberra-gtk.so.0.1.6
08953000-08954000 rw-p 00004000 08:01 528258     /usr/lib/libcanberra-gtk.so.0.1.6
08d7b000-08dae000 r-xp 00000000 08:01 919433     /lib/libpcre.so.3.12.1
08dae000-08daf000 r--p 00032000 08:01 919433     /lib/libpcre.so.3.12.1
08daf000-08db0000 rw-p 00033000 08:01 919433     /lib/libpcre.so.3.12.1
08ede000-08f02000 r-xp 00000000 08:01 919368     /lib/libexpat.so.1.5.2
08f02000-08f04000 r--p 00024000 08:01 919368     /lib/libexpat.so.1.5.2
08f04000-08f05000 rw-p 00026000 08:01 919368     /lib/libexpat.so.1.5.2
0913f000-09267000 rw-p 00000000 00:00 0          [heap]
b7200000-b7221000 rw-p 00000000 00:00 0 
b7221000-b7300000 ---p 00000000 00:00 0 
b7339000-b7388000 r--p 00000000 08:01 1578800    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
b7388000-b73de000 r--p 00000000 08:01 1576922    /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-R.ttf
b73de000-b73df000 r--s 00000000 08:01 403984     /var/cache/fontconfig/26de28bc8622bbc1fb67fd234c21975f-le32d4.cache-3
b73df000-b73e0000 r--s 00000000 08:01 394048     /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
b73e0000-b73e6000 r--s 00000000 08:01 394045     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
b73e6000-b73e8000 r--s 00000000 08:01 394046     /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
b73e8000-b73eb000 r--s 00000000 08:01 394055     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
b73eb000-b73f1000 r--s 00000000 08:01 403985     /var/cache/fontconfig/401a5dd6b567794a1d18dd9342dfa604-le32d4.cache-3
b73f1000-b73f4000 r--s 00000000 08:01 403061     /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-3
b73f4000-b73f6000 r--s 00000000 08:01 402858     /var/cache/fontconfig/ea47318ec9849e1a71e80a5d69d13859-le32d4.cache-3
b73f6000-b73f7000 r--s 00000000 08:01 402880     /var/cache/fontconfig/e3fa16a14183b06aa45b3e009278fd14-le32d4.cache-3
b73f7000-b73f8000 r--s 00000000 08:01 394056     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
b73f8000-b73fb000 r--s 00000000 08:01 394042     /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
b73fb000-b73fc000 r--s 00000000 08:01 394038     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
b73fc000-b73fd000 r--s 00000000 08:01 394031     /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
b73fd000-b73fe000 r--s 00000000 08:01 394040     /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b73fe000-b7402000 r--s 00000000 08:01 394047     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
b7402000-b7406000 r--s 00000000 08:01 403920     /var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-le32d4.cache-3
b7406000-b740d000 r--s 00000000 08:01 394050     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
b740d000-b7418000 r--s 00000000 08:01 394032     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
b7418000-b741b000 r--s 00000000 08:01 394052     /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b741b000-b741c000 r--s 00000000 08:01 402744     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b741c000-b743e000 r--s 00000000 08:01 400341     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-3
b743e000-b7446000 r--s 00000000 08:01 394051     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
b7446000-b7448000 r--s 00000000 08:01 394057     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
b7448000-b744b000 r--s 00000000 08:01 403981     /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b744b000-b744c000 r--s 00000000 08:01 3417370    /home/ronh/.fontconfig/af2b761596a194f7fabe84339ffc45cd-le32d4.cache-3
b744c000-b744d000 r--p 00000000 08:01 1582731    /usr/share/locale-langpack/en_CA/LC_MESSAGES/glib20.mo
b744d000-b744e000 rw-p 00000000 00:00 0 
b744e000-b7455000 r--s 00000000 08:01 536972     /usr/lib/gconv/gconv-modules.cache
b7455000-b7458000 r--p 00000000 08:01 1583595    /usr/share/locale-langpack/en_CA/LC_MESSAGES/gtk20-properties.mo
b7458000-b745a000 r--p 00000000 08:01 1583596    /usr/share/locale-langpack/en_CA/LC_MESSAGES/gtk20.mo
b745a000-b757a000 r--p 00178000 08:01 529165     /usr/lib/locale/locale-archive
b757a000-b777a000 r--p 00000000 08:01 529165     /usr/lib/locale/locale-archive
b777a000-b7786000 rw-p 00000000 00:00 0 
b779d000-b779f000 rw-p 00000000 00:00 0 
bff6c000-bff8d000 rw-p 00000000 00:00 0          [stack]



Here's the code:

```
struct     credentials{
        GtkWidget    *usr;
        GtkWidget    *pwd;
        int            type;
        GtkWidget    *win;
}credintials;

char        c_auth_level[1];
const char    *cc_auth_level = &c_auth_level[0];/*authentication level 0,1,2 etc */

void    close_authenticate_window(void);
void    do_authentication(GtkWidget *w ,struct credentials *data);
void    authenticate_window(int auth_type);

/*******************************************************************************
* begin the authentication process
*
********************************************************************************/
int        authenticate(int auth_type)
{
int i;
const char *cc_l;

    printf("[MWAutomation] -> Starting Authentication proccess\n");
    authenticate_window(auth_type);
    printf("[MWAutomation] -> Authentication process complete\n");
    printf("cc_auth_level = %s\n",cc_auth_level);
    cc_l = "0";
    i = strncmp(cc_auth_level,cc_l,strlen(cc_auth_level));
    if(i == 0)
    {
        return 0;
    }

    return -1;
}

void     authenticate_window(int auth_type)
{

struct credentials    auth;
GtkWidget    *auth_window;
GtkWidget    *lbl_auth_type;
GtkWidget    *lbl_username;
GtkWidget    *entry_username;
GtkWidget    *lbl_password;
GtkWidget    *entry_password;
GtkWidget    *btn_authenticate;
GtkWidget    *vbox1;
GtkWidget    *hbox1;
GtkWidget    *hbox2;

/* create the window */
    auth_window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
    gtk_window_set_modal(GTK_WINDOW(auth_window),TRUE);
    gtk_window_set_position(GTK_WINDOW(auth_window),GTK_WIN_POS_CENTER);
    gtk_window_set_title(GTK_WINDOW(auth_window),"Authentication Required:");
    gtk_widget_set_size_request(auth_window,400,100);

    vbox1 = gtk_vbox_new(TRUE,6);
    gtk_container_add(GTK_CONTAINER(auth_window),vbox1);

    if(auth_type == 0)
    {
        lbl_auth_type = gtk_label_new("*** System Start ***");
        gtk_container_add(GTK_CONTAINER(vbox1),lbl_auth_type);
    }

    hbox1 = gtk_hbox_new(FALSE,6);
    gtk_container_add(GTK_CONTAINER(vbox1),hbox1);
    hbox2 = gtk_hbox_new(FALSE,6);
    gtk_container_add(GTK_CONTAINER(vbox1),hbox2);

    lbl_username = gtk_label_new("Username:");
    gtk_container_add(GTK_CONTAINER(hbox1),lbl_username);
    entry_username = gtk_entry_new();
    gtk_container_add(GTK_CONTAINER(hbox1),entry_username);

    lbl_password = gtk_label_new("Password:");
    gtk_container_add(GTK_CONTAINER(hbox2),lbl_password);
    entry_password = gtk_entry_new();
    gtk_entry_set_visibility(GTK_ENTRY(entry_password),FALSE);
    gtk_container_add(GTK_CONTAINER(hbox2),entry_password);

    btn_authenticate = gtk_button_new_with_label("Authenticate");
    gtk_container_add(GTK_CONTAINER(vbox1),btn_authenticate);

    auth.usr = entry_username;
    auth.pwd = entry_password;
    auth.type = auth_type;
    auth.win = auth_window;

    g_signal_connect(G_OBJECT(auth_window), "destroy",
            G_CALLBACK(close_authenticate_window), NULL);
    g_signal_connect(G_OBJECT(btn_authenticate),"clicked",
            G_CALLBACK(do_authentication),&auth);

    gtk_widget_show_all(auth_window);
    gtk_main();
    printf("[MWAutomation] -> gtk_main() returned\n");
}

/*************************************************************************************
 * close the authentication window and return control to the main app
 */
void    close_authenticate_window()
{
    printf("[MWAutomation] -> close_authentication_window()\n");
    gtk_main_quit();
    printf("[MWAutomation] -> gtk_main_quit()\n");
}

/*************************************************************************************
 * do the authentications
 *
 */
void    do_authentication(GtkWidget *w,struct credentials *data)
{
gchar        *hash;
char        s1[512];
char        username[50];
char        password[100];
const char    *cc_s1=&s1[0];
const char    *usr = &username[0];
const char    *pwd = &password[0];

const char    *server = "localhost";
const char    *database = "MWAutomation";
const char    *err;
int            i;
GtkWidget    *MD;
MYSQL        *connection;
MYSQL_RES     *result;
MYSQL_ROW     row;

    usr = gtk_entry_get_text(GTK_ENTRY(GTK_WIDGET(data->usr)));
    pwd = gtk_entry_get_text(GTK_ENTRY(GTK_WIDGET(data->pwd)));

    if ((strlen(usr) == 0)||(strlen(pwd) == 0))
    {
        printf("Application Terminated: blank username or password not allowed!\n");
        g_signal_emit_by_name(G_OBJECT(data->win),"destroy",NULL);
        cc_auth_level = "-1";
    }
    else
    {
        strncat((char*)pwd,usr,50);

        if(data->type == 0)
        {
            hash = g_compute_checksum_for_string(G_CHECKSUM_SHA256,pwd,strlen(pwd));

            connection = mysql_init(NULL);
            if (!mysql_real_connect(connection, server, usr, hash, database, 0, NULL, 0))
            {
                err = mysql_error(connection);
                MD = gtk_message_dialog_new(GTK_WINDOW(data->win),
                                            GTK_DIALOG_DESTROY_WITH_PARENT,
                                               GTK_MESSAGE_ERROR,
                                               GTK_BUTTONS_OK,
                                               "%s",err);
                gtk_window_set_title(GTK_WINDOW(MD), "Connection Error !");
                gtk_dialog_run(GTK_DIALOG(MD));
                gtk_widget_destroy(MD);
                printf("[MWAutomation] -> mysql connection failed !!!\n");
            }
            else
            {
                i = sprintf(s1,"SELECT * FROM Authentication WHERE username = '%s'",usr);
                //cc_s1 = (const char *)s1;
                mysql_query(connection, cc_s1);
                result = mysql_store_result(connection);
                err = mysql_error(connection);
                if ((result!=NULL)&&(mysql_num_rows(result)!=0))
                {
                    row = mysql_fetch_row(result);
                    err = mysql_error(connection);
                    i = strncmp(row[1],hash,strlen(row[1]));
                    if(i==0)
                    {
                        cc_auth_level = row[2];
                    }
                }
                mysql_free_result(result);
            }
        }
        printf("%s\n",gtk_entry_get_text(GTK_ENTRY(GTK_WIDGET(data->usr))));
        printf("%s\n",gtk_entry_get_text(GTK_ENTRY(GTK_WIDGET(data->pwd))));
        printf("%i\n",data->type);
        printf("hash = %s\n",hash);
        g_free(hash);
        mysql_close(connection);
        gtk_window_set_modal(GTK_WINDOW(data->win),FALSE);
        gtk_widget_destroy(data->win);
    }
}

```

---

### Post by Bachstelze on 2011-08-09
Please compile your code with -g, run it into gdb until you get the error. Then type the command "bt" and paste what you get.

---

### Post by solaris235 on 2011-08-09
Here's the bt results:

```
Program received signal SIGABRT, Aborted.
0x0012e416 in __kernel_vsyscall ()
(gdb) bt
#0  0x0012e416 in __kernel_vsyscall ()
#1  0x007c1941 in raise (sig=6) at ../nptl/sysdeps/unix/sysv/linux/raise.c:64
#2  0x007c4e42 in abort () at abort.c:92
#3  0x007f9305 in __libc_message (do_abort=2, 
    fmt=0x8d1280 "*** glibc detected *** %s: %s: 0x%s ***\n")
    at ../sysdeps/unix/sysv/linux/libc_fatal.c:189
#4  0x00803501 in malloc_printerr (action=<value optimized out>, 
    str=0x6 <Address 0x6 out of bounds>, ptr=0x80994c8) at malloc.c:6283
#5  0x00804d70 in _int_free (av=<value optimized out>, p=<value optimized out>)
    at malloc.c:4795
#6  0x00807e5d in __libc_free (mem=0x80994c8) at malloc.c:3738
#7  0x0097d486 in g_free () from /lib/libglib-2.0.so.0
#8  0x001eb38e in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#9  0x00902994 in g_object_unref () from /usr/lib/libgobject-2.0.so.0
#10 0x001e2787 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#11 0x00902e8f in g_object_run_dispose () from /usr/lib/libgobject-2.0.so.0
#12 0x0028bfbe in gtk_object_destroy () from /usr/lib/libgtk-x11-2.0.so.0
#13 0x0019e325 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#14 0x001d2824 in gtk_container_foreach () from /usr/lib/libgtk-x11-2.0.so.0
#15 0x001d30de in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#16 0x0090ff2c in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#17 0x008fea87 in ?? () from /usr/lib/libgobject-2.0.so.0
---Type <return> to continue, or q <return> to quit---
#18 0x00900340 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#19 0x00916a06 in ?? () from /usr/lib/libgobject-2.0.so.0
#20 0x00917fac in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#21 0x00918452 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#22 0x0028c2b1 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#23 0x0039aa54 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#24 0x00902e8f in g_object_run_dispose () from /usr/lib/libgobject-2.0.so.0
#25 0x0028bfbe in gtk_object_destroy () from /usr/lib/libgtk-x11-2.0.so.0
#26 0x0019e325 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#27 0x001d2824 in gtk_container_foreach () from /usr/lib/libgtk-x11-2.0.so.0
#28 0x001d30de in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#29 0x0090ff2c in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#30 0x008fea87 in ?? () from /usr/lib/libgobject-2.0.so.0
#31 0x00900340 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#32 0x00916a06 in ?? () from /usr/lib/libgobject-2.0.so.0
#33 0x00917fac in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#34 0x00918452 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#35 0x0028c2b1 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#36 0x0039aa54 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#37 0x00902e8f in g_object_run_dispose () from /usr/lib/libgobject-2.0.so.0
#38 0x0028bfbe in gtk_object_destroy () from /usr/lib/libgtk-x11-2.0.so.0
#39 0x0019a1ad in ?? () from /usr/lib/libgtk-x11-2.0.so.0
---Type <return> to continue, or q <return> to quit---
#40 0x001d2824 in gtk_container_foreach () from /usr/lib/libgtk-x11-2.0.so.0
#41 0x001d30de in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#42 0x003a7f13 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#43 0x0090ff2c in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#44 0x008fea87 in ?? () from /usr/lib/libgobject-2.0.so.0
#45 0x00900412 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#46 0x00916a06 in ?? () from /usr/lib/libgobject-2.0.so.0
#47 0x00917fac in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#48 0x00918452 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#49 0x0028c2b1 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#50 0x0039aa54 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#51 0x003a9356 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#52 0x00902e8f in g_object_run_dispose () from /usr/lib/libgobject-2.0.so.0
#53 0x0028bfbe in gtk_object_destroy () from /usr/lib/libgtk-x11-2.0.so.0
#54 0x0804987c in do_authentication (w=0x80df018, data=0xbffff2f8)
    at /home/ronh/Programming/MWAutomation/crypto.h:208
#55 0x0090ff2c in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#56 0x00900412 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#57 0x00916b85 in ?? () from /usr/lib/libgobject-2.0.so.0
#58 0x00917fac in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#59 0x00918452 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
---Type <return> to continue, or q <return> to quit---
#60 0x001a62ca in gtk_button_clicked () from /usr/lib/libgtk-x11-2.0.so.0
#61 0x001a7785 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#62 0x001a782c in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#63 0x00264284 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#64 0x008fea87 in ?? () from /usr/lib/libgobject-2.0.so.0
#65 0x00900412 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#66 0x009167d6 in ?? () from /usr/lib/libgobject-2.0.so.0
#67 0x00917e2b in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#68 0x00918452 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#69 0x00392b96 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#70 0x0025c90c in gtk_propagate_event () from /usr/lib/libgtk-x11-2.0.so.0
#71 0x0025dc17 in gtk_main_do_event () from /usr/lib/libgtk-x11-2.0.so.0
#72 0x00a5c36a in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#73 0x00974855 in g_main_context_dispatch () from /lib/libglib-2.0.so.0
#74 0x00978668 in ?? () from /lib/libglib-2.0.so.0
#75 0x00978ba7 in g_main_loop_run () from /lib/libglib-2.0.so.0
#76 0x0025e1d9 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#77 0x0804936a in authenticate_window (auth_type=0)
    at /home/ronh/Programming/MWAutomation/crypto.h:113
#78 0x08048fc1 in authenticate (auth_type=0)
    at /home/ronh/Programming/MWAutomation/crypto.h:39
#79 0x080498f6 in main (argc=2, argv=0xbffff444) at ../MWAutomation.c:30

```

---

### Post by Bachstelze on 2011-08-09
/home/ronh/Programming/MWAutomation/crypto.h

Is this the file you pasted in your first message?

---

### Post by solaris235 on 2011-08-09
The first post is the output of gdb from Eclipse.
The second one is direct from gdb's bt command run through a terminal.

---

### Post by Bachstelze on 2011-08-09
I mean the code in you fist post. Which file is it from?

---

### Post by solaris235 on 2011-08-09
Yes it's the same program.
crypto.h is the authentication portion that I plan to use elsewhere.
The main app is MWAutomation.c which currently only calls the routines in crypto.h.

Here is MWAutomation.c

```
#include    <MWAutomation.h>
#include    <crypto.h>


int        main(int argc, char *argv[])
{
int        login_check=0;


    /* initialize the GTK+ library */
    if(gtk_init_check(&argc, &argv) == FALSE)
    {
        g_message("[ERROR:] Unable to initialize the GTK+ library/n");
        return 1; /* end program if not found */
    }

    /* login to the application */
    cc_auth_level = "-1";
    login_check = authenticate(0);

    if (login_check == -1)
    {
        printf("MWAutomation Login Failed !!!\n");
        printf("login_check = %d\n",login_check);
        return 0;
    }

    printf("login successfull -- continue\n");
    return 0;
}

```

---

### Post by Arndt on 2011-08-09
> **solaris235 said:**
> Yes it's the same program.
crypto.h is the authentication portion that I plan to use elsewhere.
The main app is MWAutomation.c which currently only calls the routines in crypto.h.

Here is MWAutomation.c

```
#include    <MWAutomation.h>
#include    <crypto.h>


int        main(int argc, char *argv[])
{
int        login_check=0;


    /* initialize the GTK+ library */
    if(gtk_init_check(&argc, &argv) == FALSE)
    {
        g_message("[ERROR:] Unable to initialize the GTK+ library/n");
        return 1; /* end program if not found */
    }

    /* login to the application */
    cc_auth_level = "-1";
    login_check = authenticate(0);

    if (login_check == -1)
    {
        printf("MWAutomation Login Failed !!!\n");
        printf("login_check = %d\n",login_check);
        return 0;
    }

    printf("login successfull -- continue\n");
    return 0;
}

```

c_auth_level looks fishy to me. It contains one char, so no final Nul, but you use %s with it in printf, and you copy to or from it with strncmp. And I don't know how it's supposed to be used, but when you set cc_auth_level to "-1", accessing the first char will just get you '-'.

---

### Post by Bachstelze on 2011-08-09
Yes, your c_auth_level and cc_auth_level variables are very fishy. You declare c_auth_level as an array of one character. What's the point of that? It can never contain any string other than the empty string. And anyway, it doesn't look like c_auth_level is used anywhere at all because you always use cc_auth_level. When you assign string literals to cc_auth_level, it doesn't point to c_auth_level anymore, so what's the point of having c_auth_level at all?

Also from the look of the bt it looks like yo have code in crypto.h. You should never put code in .h files. What's in crypto.h exactly?

---

### Post by solaris235 on 2011-08-10
First off, thanks for the responses.

Yes my c_auth_level was a  sloppy way of doing what I ultimately need. I've changed it to an int.  It only needs to hold a number from 0 through 10 but the mysql results  come back in string form. I was just being lazy. It was working find  though. I still have the same issue so this variable was not the  problem.

Yes I have code in .h files. That is because I can't get  eclipse to compile multiple .c files. I've written many programs this  way and they all work fine. but that's a whole different problem.

I  still get the same "invalid next size" error but only when I use the  second set of credentials from the database. It works fine with the  first set of credentials.
The database contains 2 entries each has 3  fields; username (text), passwordhash (text), and authentication level  (int). I've reorder them and still get the same problem so Its not  because of the position in the table.
It must be something to do with the way either the username, password or hash are accessed by one of the functions I'm using.
I may just have to start from scratch. 
hmmmm...
It's really windy out so I think I'll go windsurfing and come back to this tomorrow.

If anyone has an epiphany please reply otherwise I'll close this thread in a day or so.
Thanks again.

---

