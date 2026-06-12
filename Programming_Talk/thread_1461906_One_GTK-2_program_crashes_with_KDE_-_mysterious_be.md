---
title: "One GTK-2 program crashes with KDE - mysterious behavior"
date: 2010-04-24
forum: Programming Talk
---

### Post by Tricity on 2010-04-24
A challenge for you GTK programmers out there. I am trying to move a program to 10.04 (beta2 and kde installed). This involved moving from gtk-1.2 to gtk-2.0 and from gdk-imlib to gdk-pixbuf. So I had massive changes throughout the codebase (some 70,000 lines in total). The program works on 8.04. The program crashes very early under 10.04/KDE4 when it enters gtk_main(), even before any windows are displayed. The stack trace is copied below. The problem seems to hint at Pulse Audio (and my program does not use audio at all), but...

1) The program works fine under 10.04 and Gnome
2) The program works fine if I run int on the 10.04 box remotely with the display on a 8.04 box
3) A similarly-designed GTk-2.0 program works in all cases (but that one does not have the long GTK1.2 history)
4) Reducing my program down to the bare minimum does not help:
                GtkWidget *window = gtk_window_new();
                gtk_window_show (window);
                gtk_main();

Any ideas would be greatly appreciated. If you want the code, let me know and I'll post it somewhere.
---------------------------------------------------
[New Thread 0xb1bf8b70 (LWP 10952)]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb1bf8b70 (LWP 10952)]
0xb5e17ed4 in pa_init_proplist () from /usr/lib/libpulsecommon-0.9.21.so
(gdb) where
#0  0xb5e17ed4 in pa_init_proplist () from /usr/lib/libpulsecommon-0.9.21.so
#1  0xb5e6ff26 in ?? () from /usr/lib/libpulse.so.0
#2  0xb5e14b35 in ?? () from /usr/lib/libpulsecommon-0.9.21.so
#3  0xb5e153b6 in pa_pdispatch_run () from /usr/lib/libpulsecommon-0.9.21.so
#4  0xb5e6f319 in ?? () from /usr/lib/libpulse.so.0
#5  0xb5e19c48 in ?? () from /usr/lib/libpulsecommon-0.9.21.so
#6  0xb5e04cfe in ?? () from /usr/lib/libpulsecommon-0.9.21.so
#7  0xb5e7f50b in pa_mainloop_dispatch () from /usr/lib/libpulse.so.0
#8  0xb5e7fa21 in pa_mainloop_iterate () from /usr/lib/libpulse.so.0
#9  0xb5e7fae4 in pa_mainloop_run () from /usr/lib/libpulse.so.0
#10 0xb5e912a3 in ?? () from /usr/lib/libpulse.so.0
#11 0xb5e29e02 in ?? () from /usr/lib/libpulsecommon-0.9.21.so
#12 0xb760596e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#13 0xb7573a0e in clone () from /lib/tls/i686/cmov/libc.so.6
(gdb)

---

### Post by splicerr on 2010-04-24
> **Tricity said:**
> 
4) Reducing my program down to the bare minimum does not help:
                GtkWidget *window = gtk_window_new();
                gtk_window_show (window);
                gtk_main();


Aren't you missing a call to gtk_init() here?

---

### Post by Tricity on 2010-04-25
No, I was just trying to be concise. To be precise, this is the exact sequence:

int main (int argc, char *argv[])
{
 GtkWidget *window;    /* Main (menu) window */
 gtk_set_locale ();
 gtk_init (&argc, &argv);
window = gtk_window_new();
                gtk_window_show (window);
[LEFT]                 gtk_main();
[/LEFT]
 return 0;
}

But I promise you that this is not the core of the problem.

---

### Post by Tricity on 2010-04-25
I guess one question would be: What makes a completely ordinary GTK program call the Pulseaudio libraries?

The software uses neither sound nor video or any other multimedia.

Anybody got ideas? Could it be some library linked with `pkg-config gtk+-2.0 --libs` or similar?

---

### Post by Tricity on 2010-04-25
Solved - or at least, I have a workaround. After installing several -dbg packages and hours of debugging, I was unable to find the problem. However, I noticed that other GTK programs cause a "plop" sound when a checkbox gets the focus. I then uninstalled canberra-pulse, and the program behavior changed, namely, crashes occurred later in the GUI build process.

Finally, I completely removed Pulseaudio. Now, everything works.

Anybody got similar problems with Pulseaudio? Can somebody tell me why Ubuntu moved away from ALSA?
:confused:

---

