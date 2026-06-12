---
title: "gtk drawing area crashes"
date: 2010-07-06
forum: Programming Talk
---

### Post by tbastian on 2010-07-06
I've got this simple program that just opens a window and adds a drawing area. When I try to exit, it crashes. I have no idea why.

[php]
#include <gtk/gtk.h>

int main ( int argc, char ** argv )
{
	GtkWidget * window;
	GtkWidget * drawarea;

	gtk_init ( &argc, &argv);

	window = gtk_window_new ( GTK_WINDOW_TOPLEVEL );

	g_signal_connect ( G_OBJECT ( window ), "destroy",
						G_CALLBACK ( destroy ), NULL );

	drawarea = gtk_drawing_area_new ();
	gtk_container_add ( GTK_CONTAINER ( window ), GTK_WIDGET ( drawarea ));
	gtk_widget_show ( GTK_WIDGET ( drawarea ));
	gtk_widget_show ( window );

	gtk_main ();

	return 0;
}
[/php]

... and this is how you compile it

```
gcc -o test test.c `pkg-config gtk+-2.0 --cflags --libs`

```

and this is what I end up with.

```

*** glibc detected *** ./testplot: free(): invalid pointer: 0x09bf9260 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0x91c0d1]
/lib/tls/i686/cmov/libc.so.6[0x91d7d2]
/lib/tls/i686/cmov/libc.so.6(cfree+0x6d)[0x9208ad]
./testplot[0x804ac8a]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x7c)[0x7a19fc]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1b2)[0x794072]
/usr/lib/libgobject-2.0.so.0[0x7a97a8]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7bd)[0x7aab2d]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26)[0x7aafb6]
/usr/lib/libgtk-x11-2.0.so.0[0x272ec1]
/usr/lib/libgtk-x11-2.0.so.0[0x374360]
/usr/lib/libgtk-x11-2.0.so.0[0x381fe6]
/usr/lib/libgobject-2.0.so.0(g_object_run_dispose+0x7f)[0x79666f]
/usr/lib/libgtk-x11-2.0.so.0(gtk_object_destroy+0x7e)[0x272bce]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x4e0)[0x247170]
/usr/lib/libgdk-x11-2.0.so.0[0x52665a]
/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1f8)[0x7ffe88]
/lib/libglib-2.0.so.0[0x803730]
/lib/libglib-2.0.so.0(g_main_loop_run+0x1bf)[0x803b9f]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9)[0x247419]
./testplot[0x804adb4]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x8c7b56]
./testplot[0x8048fc1]
======= Memory map: ========
00110000-004c8000 r-xp 00000000 08:03 181703     /usr/lib/libgtk-x11-2.0.so.0.1800.3
004c8000-004c9000 ---p 003b8000 08:03 181703     /usr/lib/libgtk-x11-2.0.so.0.1800.3
004c9000-004cd000 r--p 003b8000 08:03 181703     /usr/lib/libgtk-x11-2.0.so.0.1800.3
004cd000-004cf000 rw-p 003bc000 08:03 181703     /usr/lib/libgtk-x11-2.0.so.0.1800.3
004cf000-004d1000 rw-p 00000000 00:00 0 
004d1000-00563000 r-xp 00000000 08:03 181705     /usr/lib/libgdk-x11-2.0.so.0.1800.3
00563000-00565000 r--p 00092000 08:03 181705     /usr/lib/libgdk-x11-2.0.so.0.1800.3
00565000-00566000 rw-p 00094000 08:03 181705     /usr/lib/libgdk-x11-2.0.so.0.1800.3
00566000-0058d000 r-xp 00000000 08:03 182551     /usr/lib/libpangoft2-1.0.so.0.2600.0
0058d000-0058e000 r--p 00027000 08:03 182551     /usr/lib/libpangoft2-1.0.so.0.2600.0
0058e000-0058f000 rw-p 00028000 08:03 182551     /usr/lib/libpangoft2-1.0.so.0.2600.0
0058f000-005b3000 r-xp 00000000 08:03 1786474    /lib/tls/i686/cmov/libm-2.10.1.so
005b3000-005b4000 r--p 00023000 08:03 1786474    /lib/tls/i686/cmov/libm-2.10.1.so
005b4000-005b5000 rw-p 00024000 08:03 1786474    /lib/tls/i686/cmov/libm-2.10.1.so
005b5000-0062c000 r-xp 00000000 08:03 181677     /usr/lib/libcairo.so.2.10800.8
0062c000-0062e000 r--p 00076000 08:03 181677     /usr/lib/libcairo.so.2.10800.8
0062e000-0062f000 rw-p 00078000 08:03 181677     /usr/lib/libcairo.so.2.10800.8
0062f000-00632000 r-xp 00000000 08:03 181624     /usr/lib/libgmodule-2.0.so.0.2200.3
00632000-00633000 r--p 00002000 08:03 181624     /usr/lib/libgmodule-2.0.so.0.2200.3
00633000-00634000 rw-p 00003000 08:03 181624     /usr/lib/libgmodule-2.0.so.0.2200.3
00634000-00636000 r-xp 00000000 08:03 181785     /usr/lib/libXcomposite.so.1.0.0
00636000-00637000 r--p 00001000 08:03 181785     /usr/lib/libXcomposite.so.1.0.0
00637000-00638000 rw-p 00002000 08:03 181785     /usr/lib/libXcomposite.so.1.0.0
00638000-0063a000 r-xp 00000000 08:03 181789     /usr/lib/libXdamage.so.1.1.0
0063a000-0063b000 rw-p 00001000 08:03 181789     /usr/lib/libXdamage.so.1.1.0
0063b000-0063f000 r-xp 00000000 08:03 181795     /usr/lib/libXfixes.so.3.1.0
0063f000-00640000 r--p 00003000 08:03 181795     /usr/lib/libXfixes.so.3.1.0
00640000-00641000 rw-p 00004000 08:03 181795     /usr/lib/libXfixes.so.3.1.0
00641000-00643000 r-xp 00000000 08:03 181803     /usr/lib/libXinerama.so.1.0.0
00643000-00644000 rw-p 00001000 08:03 181803     /usr/lib/libXinerama.so.1.0.0
00645000-00650000 r-xp 00000000 08:03 182549     /usr/lib/libpangocairo-1.0.so.0.2600.0
00650000-00651000 r--p 0000a000 08:03 182549     /usr/lib/libpangocairo-1.0.so.0.2600.0
00651000-00652000 rw-p 0000b000 08:03 182549     /usr/lib/libpangocairo-1.0.so.0.2600.0
00652000-0065a000 r-xp 00000000 08:03 181815     /usr/lib/libXrender.so.1.3.0
0065a000-0065b000 r--p 00007000 08:03 181815     /usr/lib/libXrender.so.1.3.0
0065b000-0065c000 rw-p 00008000 08:03 181815     /usr/lib/libXrender.so.1.3.0
0065c000-0065e000 r-xp 00000000 08:03 1786469    /lib/tls/i686/cmov/libdl-2.10.1.so
0065e000-0065f000 r--p 00001000 08:03 1786469    /lib/tls/i686/cmov/libdl-2.10.1.so
0065f000-00660000 rw-p 00002000 08:03 1786469    /lib/tls/i686/cmov/libdl-2.10.1.so
00661000-0067c000 r-xp 00000000 08:03 181864     /usr/lib/libatk-1.0.so.0.2809.1
0067c000-0067d000 r--p 0001b000 08:03 181864     /usr/lib/libatk-1.0.so.0.2809.1
0067d000-0067e000 rw-p 0001c000 08:03 181864     /usr/lib/libatk-1.0.so.0.2809.1
0067e000-00711000 r-xp 00000000 08:03 181626     /usr/lib/libgio-2.0.so.0.2200.3
00711000-00712000 r--p 00092000 08:03 181626     /usr/lib/libgio-2.0.so.0.2200.3
00712000-00713000 rw-p 00093000 08:03 181626     /usr/lib/libgio-2.0.so.0.2200.3
00713000-00714000 rw-p 00000000 00:00 0 
00714000-0075a000 r-xp 00000000 08:03 182547     /usr/lib/libpango-1.0.so.0.2600.0
0075a000-0075b000 r--p 00045000 08:03 182547     /usr/lib/libpango-1.0.so.0.2600.0
0075b000-0075c000 rw-p 00046000 08:03 182547     /usr/lib/libpango-1.0.so.0.2600.0
0075c000-00787000 r-xp 00000000 08:03 182078     /usr/lib/libfontconfig.so.1.3.0
00787000-00788000 r--p 0002a000 08:03 182078     /usr/lib/libfontconfig.so.1.3.0
00788000-00789000 rw-p 0002b000 08:03 182078     /usr/lib/libfontconfig.so.1.3.0
00789000-007c5000 r-xp 00000000 08:03 181035     /usr/lib/libgobject-2.0.so.0.2200.3
007c5000-007c6000 r--p 0003b000 08:03 181035     /usr/lib/libgobject-2.0.so.0.2200.3
007c6000-007c7000 rw-p 0003c000 08:03 181035     /usr/lib/libgobject-2.0.so.0.2200.3
007c7000-0087c000 r-xp 00000000 08:03 1761394    /lib/libglib-2.0.so.0.2200.3
0087c000-0087d000 r--p 000b4000 08:03 1761394    /lib/libglib-2.0.so.0.2200.3
0087d000-0087e000 rw-p 000b5000 08:03 1761394    /lib/libglib-2.0.so.0.2200.3
0087e000-0088c000 r-xp 00000000 08:03 181793     /usr/lib/libXext.so.6.4.0
0088c000-0088d000 r--p 0000d000 08:03 181793     /usr/lib/libXext.so.6.4.0
0088d000-0088e000 rw-p 0000e000 08:03 181793     /usr/lib/libXext.so.6.4.0
0088e000-00897000 r-xp 00000000 08:03 181801     /usr/lib/libXi.so.6.0.0
00897000-00898000 r--p 00008000 08:03 181801     /usr/lib/libXi.so.6.0.0
00898000-00899000 rw-p 00009000 08:03 181801     /usr/lib/libXi.so.6.0.0
00899000-008a2000 r-xp 00000000 08:03 181787     /usr/lib/libXcursor.so.1.0.2
008a2000-008a3000 r--p 00008000 08:03 181787     /usr/lib/libXcursor.so.1.0.2
008a3000-008a4000 rw-p 00009000 08:03 181787     /usr/lib/libXcursor.so.1.0.2
008a4000-008ac000 r-xp 00000000 08:03 182090     /usr/lib/libfusion-1.2.so.0.7.0
008ac000-008ad000 r--p 00007000 08:03 182090     /usr/lib/libfusion-1.2.so.0.7.0
008ad000-008ae000 rw-p 00008000 08:03 182090     /usr/lib/libfusion-1.2.so.0.7.0
008b0000-008b1000 r-xp 00000000 00:00 0          [vdso]
008b1000-009ef000 r-xp 00000000 08:03 1786464    /lib/tls/i686/cmov/libc-2.10.1.so
009ef000-009f0000 ---p 0013e000 08:03 1786464    /lib/tls/i686/cmov/libc-2.10.1.so
009f0000-009f2000 r--p 0013e000 08:03 1786464    /lib/tls/i686/cmov/libc-2.10.1.soAborted


```

---

### Post by pbrane on 2010-07-06
Can you post your *destroy* callback function? And if you compile with
```

gcc -W -Wall $(pkg-config gtk+-2.0 --cflags --libs) -o gtktest gtktest.c

```
you will see any warnings that come up.

---

### Post by tbastian on 2010-07-06
That was my issue. I copied that bit of code from another program, but forgot to define a destroy function. I just assumed it was a gtk defined function. I changed it to 'gtk_main_quit' and now it crashes for a different reason (which is good 'cause its pretty obvious why).

I am a little perplexed as to why it compiled without there being a definition of 'destroy' somewhere...

Thanks a lot.

---

