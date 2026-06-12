---
title: "Gtk3 crash opening Gui"
date: 2020-11-08
forum: New to Ubuntu
---

### Post by wilemii on 2020-11-08
Hi, 

First time posting. I'm currently stuck on a crash and don't know how to diagnose the problem:
Whenever some aplication is opened (gedit, nautilus, nemo) the aplication is displayed, but it crash after 0.1 seconds.

Context:
Last week, some dependencies were installed in my computer in order to run [https://github.com/3b1b/manim](https://github.com/3b1b/manim) in VSCode. (pycairo, pixman, and others which I don't remember now)

After rebooting, the desktop begans to blink (moving icons 20 pixels down-left), and the computer became unusable: not responding to any click (only terminal with ctrl + alt + F2).

So, trying to fix it, I upgrade my distribution (From 14.04 to 20.04), change from compiz to i3, install last nvidia drivers. (probably unrelated)

Now In Focal Fossa, I have acces to firefox and terminals, but still cannot open some other GUI application.
These are some tracebacks of the crashes (gdb on var/crash files)

[HTML] NAUTILUS CRASH
#0  __GI_raise (sig=sig@entry=6) at ../sysdeps/unix/sysv/linux/raise.c:50
#1  0x00007fc2f8769859 in __GI_abort () at abort.c:79
#2  0x00007fc2f87d43ee in __libc_message (action=action@entry=do_abort, fmt=fmt@entry=0x7fc2f88fe285 "%s\n") at ../sysdeps/posix/libc_fatal.c:155
#3  0x00007fc2f87dc47c in malloc_printerr (str=str@entry=0x7fc2f88fc4ae "free(): invalid pointer") at malloc.c:5347
#4  0x00007fc2f87ddcac in _int_free (av=<optimized out>, p=<optimized out>, have_lock=0) at malloc.c:4173
#5  0x00007fc2f8ec5664 in _cairo_clip_destroy (clip=0x55cd111488a0) at cairo-clip.c:137
#6  0x00007fc2f8ec59e6 in _cairo_clip_destroy (clip=<optimized out>) at cairo-clip.c:130
#7  0x00007fc2f8ec6fbc in _cairo_composite_rectangles_fini (extents=extents@entry=0x7ffe8c6272e0) at cairo-composite-rectangles.c:47
#8  0x00007fc2f8ec7fb7 in _cairo_compositor_paint (compositor=0x7fc2f91c4920 <compositor>, surface=0x55cd110c0400, op=<optimized out>, source=<optimized out>, clip=<optimized out>) at cairo-compositor.c:79
#9  0x00007fc2f8f1bdcc in _cairo_surface_paint (surface=0x55cd110c0400, op=CAIRO_OPERATOR_OVER, source=0x7ffe8c627620, clip=0x55cd10ee3060) at cairo-surface.c:2198
#10 0x00007fc2f8ed07d7 in _cairo_gstate_paint (gstate=0x55cd1115a960) at cairo-gstate.c:1061
#11 0x00007fc2f8f29045 in INT_cairo_paint (cr=0x55cd10c59050) at cairo.c:2219
#12 0x00007fc2f96e875c in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#13 0x00007fc2f9821a58 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#14 0x00007fc2f96e7384 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#15 0x00007fc2f969d3e5 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#16 0x00007fc2f98fcd04 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#17 0x00007fc2f96dd28b in gtk_container_propagate_draw () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#18 0x00007fc2f96dd35d in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#19 0x00007fc2f968dfd8 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#20 0x00007fc2f96e2601 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#21 0x00007fc2f96e749c in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#22 0x00007fc2f96908f5 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#23 0x00007fc2f98fcd04 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#24 0x00007fc2f96dd28b in gtk_container_propagate_draw () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#25 0x00007fc2f96dd35d in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#26 0x00007fc2f976dd50 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#27 0x00007fc2f96e2601 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#28 0x00007fc2f96e749c in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#29 0x00007fc2f976f30c in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#30 0x00007fc2f98fcd04 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#31 0x00007fc2f96dd28b in gtk_container_propagate_draw () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#32 0x00007fc2f96dd35d in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#33 0x00007fc2f990b7c5 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#34 0x00007fc2f98fcd04 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#35 0x00007fc2f9906050 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#36 0x00007fc2f97af3b4 in gtk_main_do_event () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#37 0x00007fc2f9497f79 in  () at /usr/lib/x86_64-linux-gnu/libgdk-3.so.0
#38 0x00007fc2f94a92e1 in  () at /usr/lib/x86_64-linux-gnu/libgdk-3.so.0
#39 0x00007fc2f94aa4b5 in  () at /usr/lib/x86_64-linux-gnu/libgdk-3.so.0
#40 0x00007fc2f94aa674 in  () at /usr/lib/x86_64-linux-gnu/libgdk-3.so.0
#41 0x00007fc2f8c4ca56 in  () at /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#42 0x00007fc2f8c6bb28 in g_signal_emit_valist () at /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#43 0x00007fc2f8c6c0d3 in g_signal_emit () at /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#44 0x00007fc2f94a1cf3 in  () at /usr/lib/x86_64-linux-gnu/libgdk-3.so.0
#45 0x00007fc2f948bf4d in  () at /usr/lib/x86_64-linux-gnu/libgdk-3.so.0
#46 0x00007fc2f9d63a28 in  () at /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
#47 0x00007fc2f9d62e8e in g_main_context_dispatch () at /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
#48 0x00007fc2f9d63240 in  () at /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
#49 0x00007fc2f9d632e3 in g_main_context_iteration () at /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
#50 0x00007fc2f8d7afd5 in g_application_run () at /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0
#51 0x000055cd0fbdfd4b in main ()
[/HTML]

[HTML] NEMO CRASH
#0  __GI_raise (sig=sig@entry=6) at ../sysdeps/unix/sysv/linux/raise.c:50
#1  0x00007f04ee6c5859 in __GI_abort () at abort.c:79
#2  0x00007f04ee7303ee in __libc_message (action=action@entry=do_abort, fmt=fmt@entry=0x7f04ee85a285 "%s\n") at ../sysdeps/posix/libc_fatal.c:155
#3  0x00007f04ee73847c in malloc_printerr (str=str@entry=0x7f04ee85c1e0 "munmap_chunk(): invalid pointer") at malloc.c:5347
#4  0x00007f04ee7386cc in munmap_chunk (p=<optimized out>) at malloc.c:2830
#5  0x00007f04ef155664 in _cairo_clip_destroy (clip=0x558656e35550) at cairo-clip.c:137
#6  0x00007f04ef1559e6 in _cairo_clip_destroy (clip=<optimized out>) at cairo-clip.c:130
#7  0x00007f04ef156fbc in _cairo_composite_rectangles_fini (extents=extents@entry=0x7fff0591b650) at cairo-composite-rectangles.c:47
#8  0x00007f04ef157fb7 in _cairo_compositor_paint (compositor=0x7f04ef454920 <compositor>, surface=0x558656da60b0, op=<optimized out>, source=<optimized out>, clip=<optimized out>) at cairo-compositor.c:79
#9  0x00007f04ef1abdcc in _cairo_surface_paint (surface=0x558656da60b0, op=CAIRO_OPERATOR_OVER, source=0x7fff0591b990, clip=0x558656c963a0) at cairo-surface.c:2198
#10 0x00007f04ef1607d7 in _cairo_gstate_paint (gstate=0x558656cba4d0) at cairo-gstate.c:1061
#11 0x00007f04ef1b9045 in INT_cairo_paint (cr=0x558656cd0ec0) at cairo.c:2219
#12 0x00007f04ef97875c in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#13 0x00007f04efab1a58 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#14 0x00007f04ef977384 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#15 0x00007f04ef92d3e5 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#16 0x00007f04efb8cd04 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#17 0x00007f04ef96d28b in gtk_container_propagate_draw () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#18 0x00007f04ef96d35d in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#19 0x00007f04ef91dfd8 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#20 0x00007f04ef972601 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#21 0x00007f04ef97749c in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#22 0x00007f04ef9208f5 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#23 0x00007f04efb8cd04 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#24 0x00007f04ef96d28b in gtk_container_propagate_draw () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#25 0x00007f04ef96d35d in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#26 0x00007f04efb8cd04 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#27 0x00007f04ef96d28b in gtk_container_propagate_draw () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#28 0x00007f04efb32a0d in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#29 0x00007f04ef972601 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#30 0x00007f04ef97749c in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#31 0x00007f04efb338a5 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#32 0x00007f04efb8cd04 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#33 0x00007f04ef96d28b in gtk_container_propagate_draw () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#34 0x00007f04ef96d35d in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#35 0x00007f04ef91dfd8 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#36 0x00007f04ef972601 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#37 0x00007f04ef97749c in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#38 0x00007f04ef9208f5 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#39 0x00007f04efb8cd04 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#40 0x00007f04ef96d28b in gtk_container_propagate_draw () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#41 0x00007f04ef96d35d in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#42 0x00007f04ef91dfd8 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#43 0x00007f04ef972601 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#44 0x00007f04ef97749c in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#45 0x00007f04ef9208f5 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#46 0x00007f04efb8cd04 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#47 0x00007f04ef96d28b in gtk_container_propagate_draw () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#48 0x00007f04ef96d35d in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#49 0x00007f04ef9f9fe8 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#50 0x00007f04ef972601 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#51 0x00007f04ef97749c in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#52 0x00007f04ef9faec5 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#53 0x00007f04efb8cd04 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#54 0x00007f04ef96d28b in gtk_container_propagate_draw () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
--Type <RET> for more, q to quit, c to continue without paging--
#55 0x00007f04ef96d35d in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#56 0x00007f04efb9b7c5 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#57 0x00007f04efb8cd04 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#58 0x00007f04efb96050 in  () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#59 0x00007f04efa3f3b4 in gtk_main_do_event () at /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#60 0x00007f04ef727f79 in  () at /usr/lib/x86_64-linux-gnu/libgdk-3.so.0
#61 0x00007f04ef7392e1 in  () at /usr/lib/x86_64-linux-gnu/libgdk-3.so.0
#62 0x00007f04ef73a4b5 in  () at /usr/lib/x86_64-linux-gnu/libgdk-3.so.0
#63 0x00007f04ef73a674 in  () at /usr/lib/x86_64-linux-gnu/libgdk-3.so.0
#64 0x00007f04eeedca56 in  () at /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#65 0x00007f04eeefbb28 in g_signal_emit_valist () at /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#66 0x00007f04eeefc0d3 in g_signal_emit () at /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#67 0x00007f04ef731cf3 in  () at /usr/lib/x86_64-linux-gnu/libgdk-3.so.0
#68 0x00007f04ef71bf4d in  () at /usr/lib/x86_64-linux-gnu/libgdk-3.so.0
#69 0x00007f04eedefa28 in  () at /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
#70 0x00007f04eedeee8e in g_main_context_dispatch () at /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
#71 0x00007f04eedef240 in  () at /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
#72 0x00007f04eedef2e3 in g_main_context_iteration () at /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
#73 0x00007f04ef00afd5 in g_application_run () at /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0
#74 0x0000558654e95146 in  ()
#75 0x00007f04ee6c70b3 in __libc_start_main (main=0x558654e95070, argc=1, argv=0x7fff0591d348, init=<optimized out>, fini=<optimized out>, rtld_fini=<optimized out>, stack_end=0x7fff0591d338)
    at ../csu/libc-start.c:308
[/HTML]


Dmesg do not show any useful information. 

Syslog:
[HTML]Nov  8 23:35:48 guillermo-MS-7817 dbus-daemon[797]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.132' (uid=1000 pid=14938 comm="nautilus " label="unconfined")
Nov  8 23:35:48 guillermo-MS-7817 systemd[1]: Starting Hostname Service...
Nov  8 23:35:48 guillermo-MS-7817 dbus-daemon[797]: [system] Successfully activated service 'org.freedesktop.hostname1'
Nov  8 23:35:48 guillermo-MS-7817 systemd[1]: Started Hostname Service.
[/HTML]

Apport.log
[HTML]ERROR: apport (pid 14972) Sun Nov  8 23:35:48 2020: called for pid 14938, signal 6, core limit 0, dump mode 1
ERROR: apport (pid 14972) Sun Nov  8 23:35:48 2020: executable: /usr/bin/nautilus (command line "nautilus")
ERROR: apport (pid 14972) Sun Nov  8 23:35:48 2020: gdbus call error: Error: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
[/HTML]

From tracebacks, it can be read that "_cairo_clip_destroy_" is trying to delete some protected memory, causing the crash.
Another common factor of the tracebacks is that, the cairo methods are called by libgtk3 (IDK if related)

Tried to "apt reinstall libcairo2 libcairo2-deb" with no luck.
Add "export GTK_CSD=0" on .Profile to somehow avoid gtk to paint the client side decoration, with no luck either.

Any guesses or workarounds?

Attached inxi -F:
[HTML]System:    Host: guillermo-MS-7817 Kernel: 5.4.0-52-generic x86_64 bits: 64 
           Desktop: Gnome 3.36.4 Distro: Ubuntu 20.04.1 LTS (Focal Fossa) 
Machine:   Type: Desktop Mobo: MSI model: H81M-E33 (MS-7817) v: 1.0 
           serial: <superuser/root required> BIOS: American Megatrends v: 6.6 date: 07/22/2014 
CPU:       Topology: Quad Core model: Intel Core i5-4440 bits: 64 type: MCP L2 cache: 6144 KiB 
           Speed: 800 MHz min/max: 800/3300 MHz Core speeds (MHz): 1: 800 2: 800 3: 800 4: 800 
Graphics:  Device-1: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics 
           driver: i915 v: kernel 
           Device-2: NVIDIA GK106 [GeForce GTX 660] driver: nvidia v: 450.80.02 
           Display: x11 server: X.Org 1.20.8 driver: modesetting,nvidia 
           unloaded: fbdev,nouveau,vesa 
           resolution: 1920x1080~60Hz, 1920x1080~60Hz, 1920x1080~60Hz 
           OpenGL: renderer: GeForce GTX 660/PCIe/SSE2 v: 4.6.0 NVIDIA 450.80.02 
Audio:     Device-1: Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio 
           driver: snd_hda_intel 
           Device-2: Intel 8 Series/C220 Series High Definition Audio driver: snd_hda_intel 
           Device-3: NVIDIA GK106 HDMI Audio driver: snd_hda_intel 
           Sound Server: ALSA v: k5.4.0-52-generic 
Network:   Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet driver: r8169 
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: d8:cb:8a:1f:34:ef 
Drives:    Local Storage: total: 465.76 GiB used: 360.25 GiB (77.3%) 
           ID-1: /dev/sda vendor: Samsung model: SSD 850 EVO 500GB size: 465.76 GiB 
Partition: ID-1: / size: 450.75 GiB used: 360.25 GiB (79.9%) fs: ext4 dev: /dev/sda1 
           ID-2: swap-1 size: 7.69 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sda5 
Sensors:   System Temperatures: cpu: 44.0 C mobo: N/A gpu: nvidia temp: 34 C 
           Fan Speeds (RPM): N/A gpu: nvidia fan: 10% 
Info:      Processes: 235 Uptime: 1h 56m Memory: 14.60 GiB used: 3.61 GiB (24.7%) Shell: bash 
           inxi: 3.0.38 
[/HTML]


Thanks in advance!

---

### Post by Impavidus on 2020-11-09
> **wilemii said:**
> 
So, trying to fix it, I upgrade my distribution (From 14.04 to 20.04), change from compiz to i3, install last nvidia drivers. (probably unrelated)
Was that a fresh install of 20.04 (maybe keeping your /home) or was that a triple release upgrade? In the latter case, you took a dirty system that was 19 months past end of life and made it even dirtier. If this is not a fresh install of 20.04, try a fresh install first. How did you install those nvidia drivers?

It appears to me you got somehow incompatible versions of libraries installed.

With both intel and nvidia graphics you have some peculiarities to deal with, but there are people here who know more about that than I.

---

### Post by wilemii on 2020-11-28
It worked like a charm.
Thanks!

---

