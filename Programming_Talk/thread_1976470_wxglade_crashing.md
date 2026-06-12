---
title: "wxglade crashing"
date: 2012-05-08
forum: Programming Talk
---

### Post by bimbofred on 2012-05-08
When I run wxglade it all runs fine until I try to add a menubar to a frame which then causes a segmentation fault. Also I used to be able to run the program fine (adding menus etc) when I was running 11.10. I backtraced the fault and got this:
```

Program received signal SIGSEGV, Segmentation fault.
0xb6c89974 in gdk_x11_window_get_drawable_impl ()
   from /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0
(gdb) backtrace 
#0  0xb6c89974 in gdk_x11_window_get_drawable_impl ()
   from /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0
#1  0xb5eacddd in ?? () from /usr/lib/liboverlay-scrollbar-0.2.so.0
#2  0xb6bd51ec in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
#3  0xb6bd3484 in g_closure_invoke ()
   from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
#4  0xb6be50d9 in ?? () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
#5  0xb6bed2dc in g_signal_emit_valist ()
   from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
#6  0xb6bed453 in g_signal_emit ()
   from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
#7  0xb6f5f44a in gtk_widget_map ()
   from /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0
#8  0xb6f6af5d in ?? () from /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0
#9  0xb6bd51ec in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
#10 0xb6bd22fd in ?? () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
#11 0xb6bd3484 in g_closure_invoke ()
   from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
#12 0xb6be5535 in ?? () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
#13 0xb6bed2dc in g_signal_emit_valist ()
   from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
---Type <return> to continue, or q <return> to quit---
#14 0xb6bed453 in g_signal_emit ()
   from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
#15 0xb6f5fefa in gtk_widget_show ()
   from /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0
#16 0xb5eae36a in ?? () from /usr/lib/liboverlay-scrollbar-0.2.so.0
#17 0xb6b14a3f in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#18 0xb6b13cda in g_main_context_dispatch ()
   from /lib/i386-linux-gnu/libglib-2.0.so.0
#19 0xb6b140e5 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#20 0xb6b1452b in g_main_loop_run () from /lib/i386-linux-gnu/libglib-2.0.so.0
#21 0xb6e1ab8f in gtk_main () from /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0
#22 0xb74cc63a in wxEventLoop::Run() ()
   from /usr/lib/i386-linux-gnu/libwx_gtk2u_core-2.8.so.0
#23 0xb755190f in wxAppBase::MainLoop() ()
   from /usr/lib/i386-linux-gnu/libwx_gtk2u_core-2.8.so.0
#24 0xb77a1523 in wxPyApp::MainLoop() ()
   from /usr/lib/python2.7/dist-packages/wx-2.8-gtk2-unicode/wx/_core_.so
#25 0xb77be9b4 in ?? ()
   from /usr/lib/python2.7/dist-packages/wx-2.8-gtk2-unicode/wx/_core_.so
#26 0x0808c7bd in PyEval_EvalFrameEx ()
#27 0x081a7d70 in PyEval_EvalCodeEx ()
#28 0x081a9cfe in ?? ()
#29 0x0811101f in PyObject_Call ()
---Type <return> to continue, or q <return> to quit---
#30 0x080cc417 in ?? ()
#31 0x0811101f in PyObject_Call ()
#32 0x080893c6 in PyEval_EvalFrameEx ()
#33 0x080890cc in PyEval_EvalFrameEx ()
#34 0x081a7d70 in PyEval_EvalCodeEx ()
#35 0x08088fdc in PyEval_EvalFrameEx ()
#36 0x080890cc in PyEval_EvalFrameEx ()
#37 0x081a7d70 in PyEval_EvalCodeEx ()
#38 0x08151e21 in PyRun_SimpleFileExFlags ()
#39 0x0815a4d9 in Py_Main ()
#40 0x0805e78b in main ()

```Anyone got any idea how to fix it.

---

### Post by bimbofred on 2012-06-21
bump

---

### Post by Peping on 2012-08-14
Bump! Happens to me too!

---

