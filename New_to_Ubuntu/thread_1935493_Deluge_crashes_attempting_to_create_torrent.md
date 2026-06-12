---
title: "Deluge crashes attempting to create torrent"
date: 2012-03-04
forum: New to Ubuntu
---

### Post by aykoola on 2012-03-04
When i attempt to create a torrent in Deluge, i do everything, and when i hit save, Deluge disappears. I've ran it in a terminal, and when it crashed it said:


/usr/lib/python2.7/dist-packages/deluge/ui/gtkui/createtorrentdialog.py:263: GtkWarning: Unable to retrieve the file info for `file:///home/xxxxx/Partis%20Torrenti/Damir.Avdi%C4%87.-.Mein.Kapital.torrent': Error while confirming file '/home/xxxxx/Partis Torrenti/Damir.Avdi&#263;.-.Mein.Kapital.torrent': No such file or directory
  response = chooser.run()
*** glibc detected *** /usr/bin/python: double free or corruption (!prev): 0x00000000036f7d20 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x78a96)[0x7f1212dc7a96]
/lib/x86_64-linux-gnu/libc.so.6(cfree+0x6c)[0x7f1212dcbd7c]
/usr/lib/x86_64-linux-gnu/libgdk-x11-2.0.so.0(gdk_region_union+0x97)[0x7f120d615cc7]
/usr/lib/x86_64-linux-gnu/libgdk-x11-2.0.so.0(+0x3d827)[0x7f120d61f827]
/usr/lib/x86_64-linux-gnu/libgdk-x11-2.0.so.0(+0x3d9d3)[0x7f120d61f9d3]
/usr/lib/x86_64-linux-gnu/libgdk-x11-2.0.so.0(+0x471f6)[0x7f120d6291f6]
/usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0(+0x265da6)[0x7f120daf9da6]
/usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0(+0x267220)[0x7f120dafb220]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_closure_invoke+0x154)[0x7f120f3c60a4]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(+0x2081a)[0x7f120f3d781a]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_signal_emit_valist+0x851)[0x7f120f3e16b1]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_signal_emit+0x82)[0x7f120f3e1852]
/usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0(gtk_widget_size_allocate+0x13e)[0x7f120daea35e]
/usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0(+0x266ebc)[0x7f120dafaebc]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_closure_invoke+0x154)[0x7f120f3c60a4]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(+0x20e5f)[0x7f120f3d7e5f]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_signal_emit_valist+0x851)[0x7f120f3e16b1]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_signal_emit+0x82)[0x7f120f3e1852]
/usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0(+0xb8f60)[0x7f120d94cf60]
/usr/lib/x86_64-linux-gnu/libgdk-x11-2.0.so.0(+0x1dd26)[0x7f120d5ffd26]
/lib/x86_64-linux-gnu/libglib-2.0.so.0(g_main_context_dispatch+0x1dd)[0x7f120feb7a5d]
/lib/x86_64-linux-gnu/libglib-2.0.so.0(+0x45258)[0x7f120feb8258]
/lib/x86_64-linux-gnu/libglib-2.0.so.0(g_main_loop_run+0x162)[0x7f120feb8792]
/usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0(gtk_main+0xa7)[0x7f120d9c8db7]
/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/_gtk.so(+0x1ac056)[0x7f120e07c056]
/usr/bin/python(PyEval_EvalFrameEx+0xea4)[0x4b7114]
/usr/bin/python(PyEval_EvalCodeEx+0x13d)[0x4bcd2d]
/usr/bin/python(PyEval_EvalFrameEx+0x7eb)[0x4b6a5b]
/usr/bin/python(PyEval_EvalCodeEx+0x735)[0x4bd325]
/usr/bin/python[0x448edf]
/usr/bin/python(PyObject_Call+0x3a)[0x41ad2a]
/usr/bin/python[0x43074e]
/usr/bin/python(PyObject_Call+0x3a)[0x41ad2a]
/usr/bin/python[0x480c73]
/usr/bin/python[0x47c1d1]
/usr/bin/python(PyObject_Call+0x3a)[0x41ad2a]
/usr/bin/python(PyEval_EvalFrameEx+0x92e)[0x4b6b9e]
/usr/bin/python(PyEval_EvalCodeEx+0x13d)[0x4bcd2d]
/usr/bin/python[0x448edf]
/usr/bin/python(PyObject_Call+0x3a)[0x41ad2a]
/usr/bin/python[0x43074e]
/usr/bin/python(PyObject_Call+0x3a)[0x41ad2a]
/usr/bin/python(PyEval_CallObjectWithKeywords+0x36)[0x4b5d76]
/usr/bin/python(PyInstance_New+0xec)[0x4349bc]
/usr/bin/python(PyObject_Call+0x3a)[0x41ad2a]
/usr/bin/python(PyEval_EvalFrameEx+0x92e)[0x4b6b9e]
/usr/bin/python(PyEval_EvalFrameEx+0xb07)[0x4b6d77]
/usr/bin/python(PyEval_EvalCodeEx+0x13d)[0x4bcd2d]
/usr/bin/python(PyEval_EvalCode+0x32)[0x4bd802]
/usr/bin/python[0x4dcc22]
/usr/bin/python(PyRun_FileExFlags+0x84)[0x4dd7e4]
/usr/bin/python(PyRun_SimpleFileExFlags+0x17e)[0x4de2ee]
/usr/bin/python(Py_Main+0x4fd)[0x4ee6dd]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed)[0x7f1212d7030d]
/usr/bin/python[0x41cb69]
======= Memory map: ========
00400000-00633000 r-xp 00000000 08:01 26084244                           /usr/bin/python2.7
00832000-00833000 r--p 00232000 08:01 26084244                           /usr/bin/python2.7
00833000-0089c000 rw-p 00233000 08:01 26084244                           /usr/bin/python2.7
0089c000-008ae000 rw-p 00000000 00:00 0 
01e50000-03c92000 rw-p 00000000 00:00 0                                  [heap]
7f11f2ffe000-7f11f2fff000 ---p 00000000 00:00 0 
7f11f2fff000-7f11f37ff000 rw-p 00000000 00:00 0 
7f11f37ff000-7f11f3800000 ---p 00000000 00:00 0 
7f11f3800000-7f11f4000000 rw-p 00000000 00:00 0 
7f11f4000000-7f11f419e000 rw-p 00000000 00:00 0 
7f11f419e000-7f11f8000000 ---p 00000000 00:00 0 
7f11f85c8000-7f11f85c9000 ---p 00000000 00:00 0 
7f11f85c9000-7f11f8dc9000 rw-p 00000000 00:00 0 
7f11f8dc9000-7f11f8dcc000 r-xp 00000000 08:01 26479250                   /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-bmp.so
7f11f8dcc000-7f11f8fcc000 ---p 00003000 08:01 26479250                   /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-bmp.so
7f11f8fcc000-7f11f8fcd000 r--p 00003000 08:01 26479250                   /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-bmp.so
7f11f8fcd000-7f11f8fce000 rw-p 00004000 08:01 26479250                   /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-bmp.so
7f11f8fce000-7f11f8fd1000 r-xp 00000000 08:01 26479253                   /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-ico.so
7f11f8fd1000-7f11f91d0000 ---p 00003000 08:01 26479253                   /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-ico.so
7f11f91d0000-7f11f91d1000 r--p 00002000 08:01 26479253                   /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-ico.so
7f11f91d1000-7f11f91d2000 rw-p 00003000 08:01 26479253                   /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-ico.so
7f11f91d2000-7f11f91d4000 r-xp 00000000 08:01 17170496                   /lib/libnss_mdns4.so.2
7f11f91d4000-7f11f93d3000 ---p 00002000 08:01 17170496                   /lib/libnss_mdns4.so.2
7f11f93d3000-7f11f93d4000 r--p 00001000 08:01 17170496                   /lib/libnss_mdns4.so.2
7f11f93d4000-7f11f93d5000 rw-p 00002000 08:01 17170496                   /lib/libnss_mdns4.so.2
7f11f93d5000-7f11f93db000 r-xp 00000000 08:01 17174196                   /lib/x86_64-linux-gnu/libnss_dns-2.13.so
7f11f93db000-7f11f95da000 ---p 00006000 08:01 17174196                   /lib/x86_64-linux-gnu/libnss_dns-2.13.so
7f11f95da000-7f11f95db000 r--p 00005000 08:01 17174196                   /lib/x86_64-linux-gnu/libnss_dns-2.13.so
7f11f95db000-7f11f95dc000 rw-p 00006000 08:01 17174196                   /lib/x86_64-linux-gnu/libnss_dns-2.13.so
7f11f95dc000-7f11f95de000 r-xp 00000000 08:01 17170497                   /lib/libnss_mdns4_minimal.so.2
7f11f95de000-7f11f97dd000 ---p 00002000 08:01 17170497                   /lib/libnss_mdns4_minimal.so.2
7f11f97dd000-7f11f97de000 r--p 00001000 08:01 17170497                   /lib/libnss_mdns4_minimal.so.2
7f11f97de000-7f11f97df000 rw-p 00002000 08:01 17170497                   /lib/libnss_mdns4_minimal.so.2
7f11f97f0000-7f11f97f1000 ---p 00000000 00:00 0 
7f11f97f1000-7f11f9ff1000 rw-p 00000000 00:00 0 
7f11f9ff1000-7f11f9ff2000 ---p 00000000 00:00 0 
7f11f9ff2000-7f11faaf3000 rw-p 00000000 00:00 0 
7f11faaf4000-7f11fab54000 rw-s 00000000 00:04 19628034                   /SYSV00000000 (deleted)
7f11fab54000-7f11fabb4000 rw-s 00000000 00:04 19595265                   /SYSV00000000 (deleted)
7f11fabb4000-7f11fabf4000 r-xp 00000000 08:01 26086488                   /usr/lib/libibus-1.0.so.0.0.0
7f11fabf4000-7f11fadf4000 ---p 00040000 08:01 26086488                   /usr/lib/libibus-1.0.so.0.0.0
7f11fadf4000-7f11fadf5000 r--p 00040000 08:01 26086488                   /usr/lib/libibus-1.0.so.0.0.0
7f11fadf5000-7f11fadf6000 rw-p 00041000 08:01 26086488                   /usr/lib/libibus-1.0.so.0.0.0
7f11fadf6000-7f11fadf7000 rw-p 00000000 00:00 0 
7f11fadf7000-7f11fadfd000 r-xp 00000000 08:01 26479284                   /usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
7f11fadfd000-7f11faffc000 ---p 00006000 08:01 26479284                   /usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
7f11faffc000-7f11faffd000 r--p 00005000 08:01 26479284                   /usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
7f11faffd000-7f11faffe000 rw-p 00006000 08:01 26479284                   /usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
7f11faffe000-7f11fafff000 ---p 00000000 00:00 0 
7f11fafff000-7f11fb7ff000 rw-p 00000000 00:00 0 
7f11fb7ff000-7f11fb800000 ---p 00000000 00:00 0 
7f11fb800000-7f11fc000000 rw-p 00000000 00:00 0 
7f11fc000000-7f11fc044000 rw-p 00000000 00:00 0 
7f11fc044000-7f1200000000 ---p 00000000 00:00 0 
7f1200007000-7f1200059000 r--p 00000000 08:01 27132910                   /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-B.ttf
7f1200059000-7f120005a000 ---p 00000000 00:00 0 
7f120005a000-7f120085a000 rw-p 00000000 00:00 0 
7f1200ffb000-7f1200ffc000 rw-p 00000000 00:00 0 
7f1200ffc000-7f120105b000 r--p 00000000 08:01 27132916                   /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-RI.ttf
7f120105b000-7f1201b40000 r--p 00000000 08:01 27529853                   /usr/share/icons/hicolor/icon-theme.cache
7f1201b40000-7f1201d5d000 r--p 00000000 08:01 27529893                   /usr/share/icons/gnome/icon-theme.cache
7f1201d5d000-7f1201e46000 r--p 00000000 08:01 27538962                   /usr/share/icons/Humanity/icon-theme.cache
7f1201e46000-7f1201e69000 r--p 00000000 08:01 27547171                   /usr/share/icons/ubuntu-mono-dark/icon-theme.cache
7f1201e69000-7f1201e7c000 r-xp 00000000 08:01 26087919                   /usr/lib/gio/modules/libgioremote-volume-monitor.so
7f1201e7c000-7f120207b000 ---p 00013000 08:01 26087919                   /usr/lib/gio/modules/libgioremote-volume-monitor.so
7f120207b000-7f120207c000 r--p 00012000 08:01 26087919                   /usr/lib/gio/modules/libgioremote-volume-monitor.so
7f120207c000-7f120207d000 rw-p 00013000 08:01 26087919                   /usr/lib/gio/modules/libgioremote-volume-monitor.so
7f120207d000-7f120208a000 r-xp 00000000 08:01 17170577                   /lib/x86_64-linux-gnu/libudev.so.0.12.0
7f120208a000-7f1202289000 ---p 0000d000 08:01 17170577                   /lib/x86_64-linux-gnu/libudev.so.0.12.0
7f1202289000-7f120228a000 r--p 0000c000 08:01 17170577                   /lib/x86_64-linux-gnu/libudev.so.0.12.0
7f120228a000-7f120228b000 rw-p 0000d000 08:01 17170577                   /lib/x86_64-linux-gnu/libudev.so.0.12.0
7f1202291000-7f120229c000 r--p 00000000 08:01 27546237                   /usr/share/icons/Humanity-Dark/icon-theme.cache
7f120229c000-7f12022b2000 r-xp 00000000 08:01 26088475                   /usr/lib/gvfs/libgvfscommon.so
7f12022b2000-7f12024b1000 ---p 00016000 08:01 26088475                   /usr/lib/gvfs/libgvfscommon.so
7f12024b1000-7f12024b2000 r--p 00015000 08:01 26088475                   /usr/lib/gvfs/libgvfscommon.so
7f12024b2000-7f12024b3000 rw-p 00016000 08:01 26088475                   /usr/lib/gvfs/libgvfscommon.so
7f12024b3000-7f12024dc000 r-xp 00000000 08:01 26087920                   /usr/lib/gio/modules/libgvfsdbus.so
7f12024dc000-7f12026dc000 ---p 00029000 08:01 26087920                   /usr/lib/gio/modules/libgvfsdbus.so
7f12026dc000-7f12026dd000 r--p 00029000 08:01 26087920                   /usr/lib/gio/modules/libgvfsdbus.so
7f12026dd000-7f12026de000 rw-p 0002a000 08:01 26087920                   /usr/lib/gio/modules/libgvfsdbus.so
7f12026de000-7f12026df000 rw-p 00000000 00:00 0 
7f12026df000-7f12026e6000 r-xp 00000000 08:01 26087918                   /usr/lib/gio/modules/libdconfsettings.so
7f12026e6000-7f12028e6000 ---p 00007000 08:01 26087918                   /usr/lib/gio/modules/libdconfsettings.so
7f12028e6000-7f12028e7000 r--p 00007000 08:01 26087918                   /usr/lib/gio/modules/libdconfsettings.so
7f12028e7000-7f12028e8000 rw-p 00008000 08:01 26087918                   /usr/lib/gio/modules/libdconfsettings.so
7f12028e8000-7f120293a000 r--p 00000000 08:01 27132868                   /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
7f120293a000-7f1202991000 r--p 00000000 08:01 27132915                   /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-R.ttf
7f1202991000-7f1202993000 r-xp 00000000 08:01 26479358                   /usr/lib/x86_64-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
7f1202993000-7f1202b92000 ---p 00002000 08:01 26479358                   /usr/lib/x86_64-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
7f1202b92000-7f1202b93000 r--p 00001000 08:01 26479358                   /usr/lib/x86_64-linux-gnu/pango/1.6.0/modules/pango-basic-fc.soAborted

---

### Post by aykoola on 2012-03-04
bump

---

### Post by eloydark on 2012-03-07
No one seems to care about this bug enough to fix it
[https://bugs.launchpad.net/ubuntu/+source/deluge/+bug/857634]("https://bugs.launchpad.net/ubuntu/+source/deluge/+bug/857634")

---

### Post by aykoola on 2012-03-11
But is there an alternative to Deluge if noone has yet fixed this bug? I mean a good alternative :)

Thank you!

---

### Post by kostkon on 2012-03-11
> **aykoola said:**
> But is there an alternative to Deluge if noone has yet fixed this bug? I mean a good alternative :)
I believe, yes; have you tried [qbittorrent]("http://www.qbittorrent.org/")?

---

### Post by synaptix on 2012-03-11
What version of Deluge are you using?

---

### Post by Cas07 on 2012-03-11
This is strange GTK bug which only seems to affect Ubuntu Oneiric. The workaround for Deluge is to comment out 'pbar.set_text':

```
--- a/deluge/ui/gtkui/createtorrentdialog.py
+++ b/deluge/ui/gtkui/createtorrentdialog.py
@@ -370,7 +370,7 @@ def create_torrent(self, path, tracker, piece_length, progress, comment, target,
     def _on_create_torrent_progress(self, value, num_pieces):
         percent = float(value)/float(num_pieces)
         pbar = self.glade.get_widget("progressbar")
-        pbar.set_text("%.2f%%" % (percent*100))
+        #pbar.set_text("%.2f%%" % (percent*100))
         if percent >= 0 and percent <= 1.0:
             pbar.set_fraction(percent)
```

We will put this into the next PPA release for Oneiric.

Edit: You could also use a standalone program such as mktorrent

---

### Post by aykoola on 2012-03-13
I'm using Deluge 1.3.3

I will try out Qbittorrent and mktorrent to see how that will work. Thank you!

---

### Post by aykoola on 2012-03-20
I've had the same problem in Qbittorrent!

---

