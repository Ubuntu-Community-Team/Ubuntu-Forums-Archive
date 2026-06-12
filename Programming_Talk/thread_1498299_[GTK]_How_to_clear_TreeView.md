---
title: "[GTK] How to clear TreeView?"
date: 2010-05-31
forum: Programming Talk
---

### Post by lampak on 2010-05-31
I have a TreeView in my window, storing data in a ListStore. Now I want to do what seemed to be the simplest thing on earth, that is to remove all rows from the widget and refill it. 

The problem is, Clear method of ListStore seems to broke the list, so that nothing can be inserted to it any more. Or at least I don't know how to do it. (I guess it forgets column types.) 

**How can I clear a TreeView and reuse it after that? **

[s]I'm using GTK#, but I think it should be pretty much the same in any other dialect, so if you know the answer in standard C or PyGTK or whatever I suppose I could use it as well.[/s] EDIT: or maybe not.

---

### Post by Milliways on 2010-05-31
> **lampak said:**
> I have a TreeView in my window, storing data in a ListStore. Now I want to do what seemed to be the simplest thing on earth, that is to remove all rows from the widget and refill it. 

The problem is, Clear method of ListStore seems to broke the list, so that nothing can be inserted to it any more. Or at least I don't know how to do it. (I guess it forgets column types.) 

**How can I clear a TreeView and reuse it after that? **

I'm using GTK#, but I think it should be pretty much the same in any other dialect, so if you know the answer in standard C or PyGTK or whatever I suppose I could use it as well.

Without any code or error message, it is difficult to help.

gtk_list_store_append (list_store, &iter); should add a new row and let you set values to that row.

---

### Post by lampak on 2010-06-01
After some investigation I think the problem may be somewhere else. It seems to be the problem with threads. And it may be GTK#-specific. 

I have more less such a code executed in a callback function passed to HttpWebRequest.BeginGetResponse (table_data is a ListStore): 
```

lock(this)
{
  table_data.Clear(); 
  for(/cut/)
  {
    /cut/
    table_data.AppendValues(some_table_of_strings);  
  }
}

```

It turns out that Clear function does work - but only a limited number of times. Sometimes it's one, sometimes it's ten. But after that the programme crashes. 

The problem disappears if I comment the call of Clear - but then obviously all new rows append to the old ones. 

The problem appears only when it is executed by this callback - when it's executed synchronously in an event of a clicked button, for instance, everything's fine. 

The error I'm getting is: 
```
(KPK:6669): Gtk-CRITICAL **: gtk_list_store_get_value: assertion `VALID_ITER (iter, list_store)' failed

(KPK:6669): GLib-GObject-CRITICAL **: g_object_set_property: assertion `G_IS_VALUE (value)' failed

(KPK:6669): GLib-GObject-CRITICAL **: g_value_unset: assertion `G_IS_VALUE (value)' failed

(KPK:6669): Gtk-CRITICAL **: gtk_list_store_get_value: assertion `VALID_ITER (iter, list_store)' failed

(KPK:6669): GLib-GObject-CRITICAL **: g_object_set_property: assertion `G_IS_VALUE (value)' failed

(KPK:6669): GLib-GObject-CRITICAL **: g_value_unset: assertion `G_IS_VALUE (value)' failed

(KPK:6669): Gtk-CRITICAL **: gtk_list_store_get_value: assertion `VALID_ITER (iter, list_store)' failed

(KPK:6669): GLib-GObject-CRITICAL **: g_object_set_property: assertion `G_IS_VALUE (value)' failed

(KPK:6669): GLib-GObject-CRITICAL **: g_value_unset: assertion `G_IS_VALUE (value)' failed

(KPK:6669): Gtk-CRITICAL **: gtk_list_store_get_value: assertion `VALID_ITER (iter, list_store)' failed

(KPK:6669): GLib-GObject-CRITICAL **: g_object_set_property: assertion `G_IS_VALUE (value)' failed

(KPK:6669): GLib-GObject-CRITICAL **: g_value_unset: assertion `G_IS_VALUE (value)' failed

(KPK:6669): Gtk-CRITICAL **: gtk_list_store_get_value: assertion `VALID_ITER (iter, list_store)' failed

(KPK:6669): GLib-GObject-CRITICAL **: g_object_set_property: assertion `G_IS_VALUE (value)' failed

(KPK:6669): GLib-GObject-CRITICAL **: g_value_unset: assertion `G_IS_VALUE (value)' failed
Stacktrace:

  at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00004>
  at (wrapper managed-to-native) Gtk.Application.gtk_main () <0xffffffff>
  at Gtk.Application.Run () <0x0000a>
  at KPK.MainClass.Main (string[]) [0x00011] in /home/lampak/Programowanie/KPK/KPK/Main.cs:13
  at (wrapper runtime-invoke) KPK.MainClass.runtime_invoke_void_object (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	/usr/bin/mono() [0x80ca6e4]
	/usr/bin/mono() [0x80f6893]
	[0xb788a410]
	/usr/lib/libgtk-x11-2.0.so.0(+0x2535c7) [0xb680f5c7]
	/usr/lib/libgtk-x11-2.0.so.0(+0x254e89) [0xb6810e89]
	/usr/lib/libgtk-x11-2.0.so.0(+0x13d364) [0xb66f9364]
	/usr/lib/libgobject-2.0.so.0(+0x98b9) [0xb610c8b9]
	/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1b2) [0xb610e252]
	/usr/lib/libgobject-2.0.so.0(+0x1f5e6) [0xb61225e6]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x5d3) [0xb6123c33]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0xb6124256]
	/usr/lib/libgtk-x11-2.0.so.0(+0x26a566) [0xb6826566]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x61b) [0xb66f305b]
	/usr/lib/libgdk-x11-2.0.so.0(+0x3b84b) [0xb656184b]
	/usr/lib/libgdk-x11-2.0.so.0(+0x3b7fa) [0xb65617fa]
	/usr/lib/libgdk-x11-2.0.so.0(+0x3b7fa) [0xb65617fa]
	/usr/lib/libgdk-x11-2.0.so.0(+0x64ad4) [0xb658aad4]
	/usr/lib/libgdk-x11-2.0.so.0(+0x37fa3) [0xb655dfa3]
	/usr/lib/libgdk-x11-2.0.so.0(gdk_window_process_all_updates+0x13f) [0xb655ffbf]
	/usr/lib/libgtk-x11-2.0.so.0(+0xac76f) [0xb666876f]
	/usr/lib/libgdk-x11-2.0.so.0(+0x16358) [0xb653c358]
	/lib/libglib-2.0.so.0(+0x39661) [0xb77d3661]
	/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1d5) [0xb77d55e5]
	/lib/libglib-2.0.so.0(+0x3f2d8) [0xb77d92d8]
	/lib/libglib-2.0.so.0(g_main_loop_run+0x187) [0xb77d9817]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9) [0xb66f3309]
	[0xb5e166f2]
	[0xb5e166a3]
	[0xb71c432e]
	[0xb71c425b]
	/usr/bin/mono(mono_runtime_exec_main+0xde) [0x8113b1e]
	/usr/bin/mono(mono_runtime_run_main+0x15a) [0x811429a]
	/usr/bin/mono(mono_debugger_main+0x77) [0x80f9e67]
	/usr/bin/mono(mono_main+0x150c) [0x80b316c]
	/usr/bin/mono() [0x805ad25]
	/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0xb7609bd6]
	/usr/bin/mono() [0x805ac61]

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

```

Or some other run: 

```
(KPK:6719): Gtk-CRITICAL **: gtk_list_store_get_value: assertion `VALID_ITER (iter, list_store)' failed

(KPK:6719): GLib-GObject-CRITICAL **: g_object_set_property: assertion `G_IS_VALUE (value)' failed

(KPK:6719): GLib-GObject-CRITICAL **: g_value_unset: assertion `G_IS_VALUE (value)' failed

(KPK:6719): Gtk-CRITICAL **: gtk_list_store_get_value: assertion `VALID_ITER (iter, list_store)' failed

(KPK:6719): GLib-GObject-CRITICAL **: g_object_set_property: assertion `G_IS_VALUE (value)' failed

(KPK:6719): GLib-GObject-CRITICAL **: g_value_unset: assertion `G_IS_VALUE (value)' failed
Stacktrace:

  at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00004>
  at (wrapper managed-to-native) Gtk.Application.gtk_main () <0xffffffff>
  at Gtk.Application.Run () <0x0000a>
  at KPK.MainClass.Main (string[]) [0x00011] in /home/lampak/Programowanie/KPK/KPK/Main.cs:13
  at (wrapper runtime-invoke) KPK.MainClass.runtime_invoke_void_object (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	/usr/bin/mono() [0x80ca6e4]
	/usr/bin/mono() [0x80f6893]
	[0xb78c9410]
	/usr/lib/libgtk-x11-2.0.so.0(+0x250f99) [0xb684bf99]
	/usr/lib/libgtk-x11-2.0.so.0(+0x2513c2) [0xb684c3c2]
	/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__BOXED+0x88) [0xb615a438]
	/usr/lib/libgobject-2.0.so.0(+0x98b9) [0xb614b8b9]
	/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xd8) [0xb614d178]
	/usr/lib/libgobject-2.0.so.0(+0x1f23a) [0xb616123a]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x754) [0xb6162db4]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit_by_name+0x155) [0xb6163085]
	/usr/lib/libgtk-x11-2.0.so.0(+0x1afe56) [0xb67aae56]
	/usr/lib/libgtk-x11-2.0.so.0(+0x1b0127) [0xb67ab127]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_size_request+0x7f) [0xb686a7cf]
	/usr/lib/libgtk-x11-2.0.so.0(+0x1a4ca2) [0xb679fca2]
	/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__BOXED+0x88) [0xb615a438]
	/usr/lib/libgobject-2.0.so.0(+0x98b9) [0xb614b8b9]
	/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xd8) [0xb614d178]
	/usr/lib/libgobject-2.0.so.0(+0x1f23a) [0xb616123a]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x754) [0xb6162db4]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit_by_name+0x155) [0xb6163085]
	/usr/lib/libgtk-x11-2.0.so.0(+0x1afe56) [0xb67aae56]
	/usr/lib/libgtk-x11-2.0.so.0(+0x1b0127) [0xb67ab127]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_size_request+0x7f) [0xb686a7cf]
	/usr/lib/libgtk-x11-2.0.so.0(+0x785b8) [0xb66735b8]
	/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__BOXED+0x88) [0xb615a438]
	/usr/lib/libgobject-2.0.so.0(+0x98b9) [0xb614b8b9]
	/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xd8) [0xb614d178]
	/usr/lib/libgobject-2.0.so.0(+0x1f23a) [0xb616123a]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x754) [0xb6162db4]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit_by_name+0x155) [0xb6163085]
	/usr/lib/libgtk-x11-2.0.so.0(+0x1afe56) [0xb67aae56]
	/usr/lib/libgtk-x11-2.0.so.0(+0x1b0127) [0xb67ab127]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_size_request+0x7f) [0xb686a7cf]
	/usr/lib/libgtk-x11-2.0.so.0(+0x278de2) [0xb6873de2]
	/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__BOXED+0x88) [0xb615a438]
	/usr/lib/libgobject-2.0.so.0(+0x98b9) [0xb614b8b9]
	/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1b2) [0xb614d252]
	/usr/lib/libgobject-2.0.so.0(+0x1f23a) [0xb616123a]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x754) [0xb6162db4]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit_by_name+0x155) [0xb6163085]
	/usr/lib/libgtk-x11-2.0.so.0(+0x1afe56) [0xb67aae56]
	/usr/lib/libgtk-x11-2.0.so.0(+0x1b0127) [0xb67ab127]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_size_request+0x7f) [0xb686a7cf]
	/usr/lib/libgtk-x11-2.0.so.0(+0x27915d) [0xb687415d]
	/usr/lib/libgtk-x11-2.0.so.0(+0x2822a9) [0xb687d2a9]
	/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x7c) [0xb615adcc]
	/usr/lib/libgobject-2.0.so.0(+0x98b9) [0xb614b8b9]
	/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1b2) [0xb614d252]
	/usr/lib/libgobject-2.0.so.0(+0x1f5e6) [0xb61615e6]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x754) [0xb6162db4]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0xb6163256]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_container_check_resize+0x8a) [0xb66a770a]
	/usr/lib/libgtk-x11-2.0.so.0(+0xac760) [0xb66a7760]
	/usr/lib/libgdk-x11-2.0.so.0(+0x16358) [0xb657b358]
	/lib/libglib-2.0.so.0(+0x39661) [0xb7812661]
	/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1d5) [0xb78145e5]
	/lib/libglib-2.0.so.0(+0x3f2d8) [0xb78182d8]
	/lib/libglib-2.0.so.0(g_main_loop_run+0x187) [0xb7818817]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9) [0xb6732309]
	[0xb5e556f2]
	[0xb5e556a3]
	[0xb720332e]
	[0xb720325b]
	/usr/bin/mono(mono_runtime_exec_main+0xde) [0x8113b1e]
	/usr/bin/mono(mono_runtime_run_main+0x15a) [0x811429a]
	/usr/bin/mono(mono_debugger_main+0x77) [0x80f9e67]
	/usr/bin/mono(mono_main+0x150c) [0x80b316c]
	/usr/bin/mono() [0x805ad25]
	/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0xb7648bd6]
	/usr/bin/mono() [0x805ac61]

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================
```

---

### Post by SledgeHammer_999 on 2010-06-01
Do you manipulate the Treeview always from the main thread? Gtk does not behave well if you use it from another thread, unless you acquire some specific locks(I don't know which).

---

### Post by tbastian on 2010-06-01
I Just finished doing something similar with gtkmm, and here are a few pointers:

```
0x0AAF4562,
0x45asdf22
```

... just kidding....

Threads and Gtk don't mix well. I wouldn't try do different stuff with gtk in multiple threads. period. Use idle functions or timeout functions if you absolutely need to. (threads doing separate stuff is OK)

try calling erase on your list_store with the root node... (I'm not sure if theres a native Gtk function for that, but in gtkmm I used ```
TreeStore -> erase ( row )
```)

---

### Post by JwB Zoofware on 2010-06-01
> **SledgeHammer_999 said:**
> Do you manipulate the Treeview always from the main thread? Gtk does not behave well if you use it from another thread, unless you acquire some specific locks(I don't know which).

Ditto this, it can be run on the main thread by:

```
Gtk.Application.Invoke(delegate {
treeview.Clear();
});
```

---

### Post by lampak on 2010-06-02
Thanks, I'm going with Invoke :)

BTW, with your tips I've googled [this site]("http://www.mono-project.com/Multi-threaded_GtkSharp_Programing_and_Keeping_your_Application_Responsive"). Quite useful I think. 

Thanks again :)

---

