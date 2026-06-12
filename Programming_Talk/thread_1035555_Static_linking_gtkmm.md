---
title: "Static linking gtkmm?"
date: 2009-01-09
forum: Programming Talk
---

### Post by Emill on 2009-01-09
Hello. I saw this:
"If you are starting a new project and wish to use C++ for your GUI, GTKmm is an alternative that is easily amenable to static linking as it's a C++ wrapper around a C library."

And now I want to static link a simple hello-world-app that uses gtkmm. But I have now idea how to do it.
I can dynamically link it with:
g++ test.cpp -o test `pkg-config --cflags --libs`

But what is the line for statically linking? I have installed libgtkmm-2.4-dev. That package includes the file /usr/lib/libgtkmm-2.4.a

---

### Post by monkeyking on 2009-01-10
Hey,
I might not understand your problem,
but have you tried compiling with -static ?

good luck

---

### Post by Emill on 2009-01-10
Yes. With the command:
g++ test.cpp -o test `pkg-config gtkmm-2.4 --cflags --libs` -static

I get:
/usr/bin/ld: cannot find -lpangomm-1.4
collect2: ld returned 1 exit status

I get no error if I remove "-static".

---

### Post by PandaGoat on 2009-01-10
Woh, first, you do not want to use -static unless you want to compile a static library.  Next, pkg-config gtkmm-2.4 --cflags --libs outputs the cflag arguments needed to compile a program using gtkmm.  Doing `pkg-config gtkmm-2.4 --cflags --libs` replaces it with its output inline.  

For clarification, pkg-config gtkmm-2.4 --cflags --libs just outputs to stdout (try just running this), and `pkg-config gtkmm-2.4 --cflags --libs` replaces itself with its output, if you will.

Anyway, apparently pango is required, or at least recommended, to link to gtkmm.  Just install libpangomm-1.4-dev or whatever version you have.

---

### Post by Emill on 2009-01-10
I know `blabla` first run the command blabla and then redirects the output to the first line.

I already have libpangomm-1.4-dev installed.

---

### Post by SledgeHammer_999 on 2009-01-10
> **Emill said:**
> I know `blabla` first run the command blabla and then redirects the output to the first line.

I already have libpangomm-1.4-dev installed.

I don't think that this package provides a "libpangomm-1.4.a" file. I think you have to compile manually pangomm to get the desired *.a file and link it.

---

### Post by Emill on 2009-01-11
I've done that now, but I still get a bunch of error messages:

```
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgio-2.0.a(glocalfileinfo.o): In function `lookup_gid_name':
(.text+0x203a): warning: Using 'getgrgid_r' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtkfilesel.o): In function `attempt_homedir_completion':
(.text+0x4e2): warning: Using 'getpwent' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtkfilesel.o): In function `open_user_dir':
(.text+0x2f78): warning: Using 'getpwnam' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libglib-2.0.a(gutils.o): In function `g_get_any_init_do':
(.text+0x1432): warning: Using 'getpwuid' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtkfilesel.o): In function `attempt_homedir_completion':
(.text+0x4cf): warning: Using 'setpwent' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtkfilesel.o): In function `attempt_homedir_completion':
(.text+0x6ee): warning: Using 'endpwent' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libglib-2.0.a(gutils.o): In function `g_get_any_init_do':
(.text+0x12ca): warning: Using 'getpwnam_r' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgio-2.0.a(glocalfileinfo.o): In function `lookup_uid_data':
(.text+0x1e76): warning: Using 'getpwuid_r' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtkselection.o): In function `_gtk_selection_incr_event':
(.text+0xb87): undefined reference to `XExtendedMaxRequestSize'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtkselection.o): In function `_gtk_selection_incr_event':
(.text+0xba6): undefined reference to `XMaxRequestSize'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtkselection.o): In function `_gtk_selection_incr_event':
(.text+0xc17): undefined reference to `XExtendedMaxRequestSize'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtkselection.o): In function `_gtk_selection_incr_event':
(.text+0xd6f): undefined reference to `XExtendedMaxRequestSize'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtkselection.o): In function `_gtk_selection_incr_event':
(.text+0xd92): undefined reference to `XMaxRequestSize'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtkselection.o): In function `_gtk_selection_incr_event':
(.text+0xe4f): undefined reference to `XExtendedMaxRequestSize'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtkselection.o): In function `_gtk_selection_request':
(.text+0x1c36): undefined reference to `XExtendedMaxRequestSize'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtkselection.o): In function `_gtk_selection_request':
(.text+0x1c51): undefined reference to `XMaxRequestSize'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtkselection.o): In function `_gtk_selection_request':
(.text+0x1def): undefined reference to `XExtendedMaxRequestSize'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtkselection.o): In function `_gtk_selection_request':
(.text+0x1e19): undefined reference to `XExtendedMaxRequestSize'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtkselection.o): In function `_gtk_selection_request':
(.text+0x1e2d): undefined reference to `XMaxRequestSize'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtkselection.o): In function `_gtk_selection_request':
(.text+0x1e5c): undefined reference to `XExtendedMaxRequestSize'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtkplug-x11.o): In function `xembed_set_info':
(.text+0x52e): undefined reference to `XChangeProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtksocket-x11.o): In function `xembed_get_info':
(.text+0xaf): undefined reference to `XGetWindowProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtksocket-x11.o): In function `xembed_get_info':
(.text+0xf9): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtksocket-x11.o): In function `xembed_get_info':
(.text+0x16b): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtksocket-x11.o): In function `_gtk_socket_windowing_embed_notify':
(.text+0x251): undefined reference to `XFixesChangeSaveSet'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtksocket-x11.o): In function `_gtk_socket_windowing_select_plug_window_input':
(.text+0x35c): undefined reference to `XSelectInput'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtksocket-x11.o): In function `_gtk_socket_windowing_size_request':
(.text+0x46d): undefined reference to `XGetWMNormalHints'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtksocket-x11.o): In function `_gtk_socket_windowing_realize_window':
(.text+0x559): undefined reference to `XGetWindowAttributes'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtksocket-x11.o): In function `_gtk_socket_windowing_realize_window':
(.text+0x587): undefined reference to `XSelectInput'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtksocket-x11.o): In function `_gtk_socket_windowing_send_configure_event':
(.text+0x67b): undefined reference to `XSendEvent'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtksocket-x11.o): In function `_gtk_socket_windowing_send_key_event':
(.text+0xc42): undefined reference to `XSendEvent'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtkxembed.o): In function `_gtk_xembed_send_message':
(.text+0x31d): undefined reference to `XSendEvent'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtktrayicon-x11.o): In function `gtk_tray_icon_get_orientation_property':
(.text+0x4db): undefined reference to `XGetWindowProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtktrayicon-x11.o): In function `gtk_tray_icon_get_orientation_property':
(.text+0x4fe): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtktrayicon-x11.o): In function `gtk_tray_icon_send_manager_message':
(.text+0x73e): undefined reference to `XSendEvent'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtktrayicon-x11.o): In function `gtk_tray_icon_send_manager_message':
(.text+0x74e): undefined reference to `XSync'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtktrayicon-x11.o): In function `gtk_tray_icon_update_manager_window':
(.text+0x89e): undefined reference to `XGrabServer'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtktrayicon-x11.o): In function `gtk_tray_icon_update_manager_window':
(.text+0x8b3): undefined reference to `XGetSelectionOwner'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtktrayicon-x11.o): In function `gtk_tray_icon_update_manager_window':
(.text+0x8cf): undefined reference to `XUngrabServer'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtktrayicon-x11.o): In function `gtk_tray_icon_update_manager_window':
(.text+0x8d7): undefined reference to `XFlush'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtktrayicon-x11.o): In function `gtk_tray_icon_update_manager_window':
(.text+0x968): undefined reference to `XSelectInput'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtktrayicon-x11.o): In function `gtk_tray_icon_realize':
(.text+0xb25): undefined reference to `XInternAtom'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtktrayicon-x11.o): In function `gtk_tray_icon_realize':
(.text+0xb4c): undefined reference to `XInternAtom'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtktrayicon-x11.o): In function `gtk_tray_icon_realize':
(.text+0xb73): undefined reference to `XInternAtom'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtktrayicon-x11.o): In function `gtk_tray_icon_realize':
(.text+0xb9a): undefined reference to `XInternAtom'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtktrayicon-x11.o): In function `_gtk_tray_icon_send_message':
(.text+0xd51): undefined reference to `XInternAtom'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtktrayicon-x11.o): In function `_gtk_tray_icon_send_message':
(.text+0xdb1): undefined reference to `XSendEvent'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtktrayicon-x11.o): In function `_gtk_tray_icon_send_message':
(.text+0xdc1): undefined reference to `XSync'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtktrayicon-x11.o): In function `_gtk_tray_icon_send_message':
(.text+0xe41): undefined reference to `XSendEvent'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgtk-x11-2.0.a(gtktrayicon-x11.o): In function `_gtk_tray_icon_send_message':
(.text+0xe51): undefined reference to `XSync'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcolor-x11.o): In function `gdk_colormap_alloc1':
(.text+0x12a): undefined reference to `XAllocColor'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcolor-x11.o): In function `gdk_colormap_alloc1':
(.text+0x20d): undefined reference to `XFreeColors'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcolor-x11.o): In function `gdk_colormap_sync':
(.text+0x51d): undefined reference to `XQueryColors'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcolor-x11.o): In function `gdk_colormap_sync':
(.text+0x633): undefined reference to `XQueryColors'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcolor-x11.o): In function `gdk_colormap_sync':
(.text+0x6a9): undefined reference to `XQueryColors'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcolor-x11.o): In function `gdk_color_change':
(.text+0x77d): undefined reference to `XStoreColor'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcolor-x11.o): In function `gdk_colormap_query_color':
(.text+0xa48): undefined reference to `XQueryColor'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcolor-x11.o): In function `gdk_colormap_alloc_colors':
(.text+0xd59): undefined reference to `XAllocColor'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcolor-x11.o): In function `gdk_colormap_alloc_colors':
(.text+0xe55): undefined reference to `XStoreColors'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcolor-x11.o): In function `gdk_colormap_alloc_colors':
(.text+0x141a): undefined reference to `XAllocColorCells'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcolor-x11.o): In function `gdk_colormap_free_colors':
(.text+0x1643): undefined reference to `XFreeColors'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcolor-x11.o): In function `gdk_colors_free':
(.text+0x17fd): undefined reference to `XFreeColors'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcolor-x11.o): In function `gdk_colors_alloc':
(.text+0x18a6): undefined reference to `XAllocColorCells'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcolor-x11.o): In function `gdk_colormap_change':
(.text+0x1a30): undefined reference to `XStoreColors'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcolor-x11.o): In function `gdk_colormap_change':
(.text+0x1aa8): undefined reference to `XStoreColors'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcolor-x11.o): In function `gdk_colormap_change':
(.text+0x1b20): undefined reference to `XStoreColors'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcolor-x11.o): In function `gdk_colormap_change':
(.text+0x1ba0): undefined reference to `XStoreColors'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcolor-x11.o): In function `gdk_colormap_new':
(.text+0x207e): undefined reference to `XCreateColormap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcolor-x11.o): In function `gdk_colormap_new':
(.text+0x21c6): undefined reference to `XCreateColormap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcolor-x11.o): In function `gdk_colormap_new':
(.text+0x2244): undefined reference to `XCreateColormap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcolor-x11.o): In function `gdk_colormap_new':
(.text+0x22bb): undefined reference to `XQueryColors'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcolor-x11.o): In function `gdk_colormap_new':
(.text+0x233e): undefined reference to `XCreateColormap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcolor-x11.o): In function `gdk_colormap_new':
(.text+0x23a3): undefined reference to `XQueryColors'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcolor-x11.o): In function `gdk_colormap_finalize':
(.text+0x2471): undefined reference to `XFreeColormap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcursor-x11.o): In function `gdk_display_get_maximal_cursor_size':
(.text+0x18a): undefined reference to `XQueryBestCursor'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcursor-x11.o): In function `gdk_cursor_new_from_name':
(.text+0x3ae): undefined reference to `XcursorLibraryLoadCursor'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcursor-x11.o): In function `gdk_cursor_new_from_pixbuf':
(.text+0x577): undefined reference to `XcursorImageCreate'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcursor-x11.o): In function `gdk_cursor_new_from_pixbuf':
(.text+0x661): undefined reference to `XcursorImageLoadCursor'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcursor-x11.o): In function `gdk_cursor_new_from_pixbuf':
(.text+0x66b): undefined reference to `XcursorImageDestroy'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcursor-x11.o): In function `gdk_x11_display_set_cursor_theme':
(.text+0x6ef): undefined reference to `XcursorGetTheme'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcursor-x11.o): In function `gdk_x11_display_set_cursor_theme':
(.text+0x6f9): undefined reference to `XcursorGetDefaultSize'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcursor-x11.o): In function `gdk_x11_display_set_cursor_theme':
(.text+0x73f): undefined reference to `XcursorSetTheme'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcursor-x11.o): In function `gdk_x11_display_set_cursor_theme':
(.text+0x755): undefined reference to `XcursorSetDefaultSize'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcursor-x11.o): In function `_gdk_x11_cursor_update_theme':
(.text+0x7e2): undefined reference to `XcursorShapeLoadCursor'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcursor-x11.o): In function `_gdk_x11_cursor_update_theme':
(.text+0x7fb): undefined reference to `XFixesChangeCursor'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcursor-x11.o): In function `_gdk_x11_cursor_update_theme':
(.text+0x81f): undefined reference to `XcursorLibraryLoadCursor'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcursor-x11.o): In function `gdk_cursor_get_image':
(.text+0x8bd): undefined reference to `XcursorGetDefaultSize'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcursor-x11.o): In function `gdk_cursor_get_image':
(.text+0x8c7): undefined reference to `XcursorGetTheme'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcursor-x11.o): In function `gdk_cursor_get_image':
(.text+0x8e5): undefined reference to `XcursorShapeLoadImages'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcursor-x11.o): In function `gdk_cursor_get_image':
(.text+0xa3c): undefined reference to `XcursorImagesDestroy'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcursor-x11.o): In function `gdk_cursor_get_image':
(.text+0xa6b): undefined reference to `XcursorLibraryLoadImages'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcursor-x11.o): In function `_gdk_cursor_destroy':
(.text+0xb23): undefined reference to `XFreeCursor'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcursor-x11.o): In function `gdk_cursor_new_from_pixmap':
(.text+0xcac): undefined reference to `XCreatePixmapCursor'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcursor-x11.o): In function `gdk_cursor_new_for_display':
(.text+0xdeb): undefined reference to `XCreateFontCursor'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcursor-x11.o): In function `gdk_display_get_default_cursor_size':
(.text+0x204): undefined reference to `XcursorGetDefaultSize'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcursor-x11.o): In function `gdk_display_supports_cursor_color':
(.text+0x274): undefined reference to `XcursorSupportsARGB'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkcursor-x11.o): In function `gdk_display_supports_cursor_alpha':
(.text+0x2e4): undefined reference to `XcursorSupportsARGB'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_supports_clipboard_persistence':
(.text+0x125): undefined reference to `XGetSelectionOwner'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_store_clipboard':
(.text+0x19d): undefined reference to `XGetSelectionOwner'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_store_clipboard':
(.text+0x243): undefined reference to `XChangeProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_store_clipboard':
(.text+0x27f): undefined reference to `XConvertSelection'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_request_selection_notification':
(.text+0x2d2): undefined reference to `XFixesSelectSelectionInput'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `_gdk_windowing_set_default_display':
(.text+0x43d): undefined reference to `XChangeProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_x11_display_ungrab':
(.text+0x9c0): undefined reference to `XUngrabServer'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_x11_display_grab':
(.text+0xa77): undefined reference to `XGrabServer'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_sync':
(.text+0xaf7): undefined reference to `XSync'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_beep':
(.text+0xb77): undefined reference to `XBell'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_keyboard_ungrab':
(.text+0xbf6): undefined reference to `XUngrabKeyboard'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_keyboard_ungrab':
(.text+0xbfe): undefined reference to `XFlush'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_pointer_ungrab':
(.text+0xccf): undefined reference to `XUngrabPointer'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_pointer_ungrab':
(.text+0xcd7): undefined reference to `XFlush'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `process_internal_connection':
(.text+0xd52): undefined reference to `XProcessInternalConnection'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_open':
(.text+0xef5): undefined reference to `XOpenDisplay'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_open':
(.text+0xf38): undefined reference to `XAddConnectionWatch'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_open':
(.text+0xf5e): undefined reference to `XRRQueryExtension'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_open':
(.text+0x10a4): undefined reference to `XFixesQueryExtension'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_open':
(.text+0x10cc): undefined reference to `XCompositeQueryExtension'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_open':
(.text+0x10f6): undefined reference to `XDamageQueryExtension'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_open':
(.text+0x1125): undefined reference to `XShapeQueryExtension'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_open':
(.text+0x1185): undefined reference to `XQueryPointer'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_open':
(.text+0x11ac): undefined reference to `XAllocClassHint'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_open':
(.text+0x120d): undefined reference to `XmbSetWMProperties'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_open':
(.text+0x1215): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_open':
(.text+0x1282): undefined reference to `XChangeProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_open':
(.text+0x12a9): undefined reference to `XkbLibraryVersion'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_open':
(.text+0x12ce): undefined reference to `XSyncQueryExtension'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_open':
(.text+0x1375): undefined reference to `XRRQueryVersion'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_open':
(.text+0x13b5): undefined reference to `XSyncInitialize'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_open':
(.text+0x1407): undefined reference to `XkbQueryExtension'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_open':
(.text+0x1439): undefined reference to `XkbSelectEvents'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_open':
(.text+0x1464): undefined reference to `XkbSelectEventDetails'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_open':
(.text+0x147e): undefined reference to `XkbSetDetectableAutoRepeat'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_open':
(.text+0x149f): undefined reference to `XSynchronize'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_open':
(.text+0x14fc): undefined reference to `XShapeQueryVersion'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_x11_finalize':
(.text+0x166f): undefined reference to `XDestroyWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_x11_finalize':
(.text+0x1782): undefined reference to `XCloseDisplay'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_x11_display_broadcast_startup_message':
(.text+0x1a73): undefined reference to `XCreateWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_x11_display_broadcast_startup_message':
(.text+0x1b54): undefined reference to `XSendEvent'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_x11_display_broadcast_startup_message':
(.text+0x1b78): undefined reference to `XDestroyWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_x11_display_broadcast_startup_message':
(.text+0x1b80): undefined reference to `XFlush'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_display_flush':
(.text+0x5ca): undefined reference to `XFlush'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdisplay-x11.o): In function `gdk_x11_display_ungrab':
(.text+0x9d0): undefined reference to `XFlush'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `xdnd_read_actions':
(.text+0xc99): undefined reference to `XGetWindowProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `xdnd_read_actions':
(.text+0xcac): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `xdnd_check_dest':
(.text+0xe07): undefined reference to `XGetWindowProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `xdnd_check_dest':
(.text+0xe78): undefined reference to `XGetWindowProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `xdnd_check_dest':
(.text+0xe94): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `xdnd_check_dest':
(.text+0xebf): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `xdnd_check_dest':
(.text+0xedc): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `xdnd_check_dest':
(.text+0xf14): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `motif_lookup_drag_window':
(.text+0xfb1): undefined reference to `XGetWindowProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `motif_lookup_drag_window':
(.text+0xfcb): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `motif_find_drag_window':
(.text+0x20a7): undefined reference to `XOpenDisplay'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `motif_find_drag_window':
(.text+0x20b9): undefined reference to `XSetCloseDownMode'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `motif_find_drag_window':
(.text+0x20c1): undefined reference to `XGrabServer'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `motif_find_drag_window':
(.text+0x20dc): undefined reference to `XUngrabServer'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `motif_find_drag_window':
(.text+0x20e4): undefined reference to `XCloseDisplay'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `motif_find_drag_window':
(.text+0x219e): undefined reference to `XCreateWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `motif_find_drag_window':
(.text+0x21e7): undefined reference to `XChangeProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `motif_read_target_table':
(.text+0x22e0): undefined reference to `XGetWindowProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `motif_read_target_table':
(.text+0x22fa): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `motif_read_target_table':
(.text+0x241b): undefined reference to `XGetWindowProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `motif_read_target_table':
(.text+0x243b): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `gdk_drag_motion':
(.text+0x3113): undefined reference to `XGetSelectionOwner'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `gdk_drag_motion':
(.text+0x31ee): undefined reference to `XChangeProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `gdk_drag_motion':
(.text+0x33c3): undefined reference to `XChangeProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `gdk_drag_motion':
(.text+0x359d): undefined reference to `XChangeProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `gdk_drag_motion':
(.text+0x3a15): undefined reference to `XChangeProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `_gdk_drag_get_protocol_for_display':
(.text+0x3fbe): undefined reference to `XGetWindowProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `_gdk_drag_get_protocol_for_display':
(.text+0x3fe3): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `_gdk_drag_get_protocol_for_display':
(.text+0x406a): undefined reference to `XGetWindowProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `_gdk_drag_get_protocol_for_display':
(.text+0x4084): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `_gdk_drag_get_protocol_for_display':
(.text+0x4159): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `gdk_drag_find_window_for_screen':
(.text+0x4290): undefined reference to `XGetWindowAttributes'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `gdk_drag_find_window_for_screen':
(.text+0x438c): undefined reference to `XSelectInput'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `xdnd_enter_filter':
(.text+0x4ba7): undefined reference to `XGetWindowProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `xdnd_enter_filter':
(.text+0x4c0d): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `xdnd_enter_filter':
(.text+0x4c32): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `motif_drag_context_new':
(.text+0x4ec9): undefined reference to `XGetWindowProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `motif_drag_context_new':
(.text+0x501b): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `motif_drag_context_new':
(.text+0x506b): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `gdk_drag_context_finalize':
(.text+0x56fb): undefined reference to `XSelectInput'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `gdk_window_register_dnd':
(.text+0x5947): undefined reference to `XChangeProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdnd-x11.o): In function `gdk_window_register_dnd':
(.text+0x59b4): undefined reference to `XChangeProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `_gdk_x11_have_render':
(.text+0x432): undefined reference to `XRenderQueryExtension'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `_gdk_x11_have_render':
(.text+0x47a): undefined reference to `XListDepths'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `_gdk_x11_have_render':
(.text+0x4c8): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `_gdk_x11_have_render':
(.text+0x4fd): undefined reference to `XSync'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `_gdk_x11_have_render':
(.text+0x5ac): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `_gdk_x11_have_render':
(.text+0x5eb): undefined reference to `XCreatePixmap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `_gdk_x11_have_render':
(.text+0x5f7): undefined reference to `XFreePixmap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `_gdk_x11_have_render':
(.text+0x633): undefined reference to `XCreatePixmap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `_gdk_x11_have_render':
(.text+0x63f): undefined reference to `XFreePixmap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `_gdk_x11_drawable_finish':
(.text+0x711): undefined reference to `XRenderFreePicture'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_drawable_get_picture':
(.text+0xb6b): undefined reference to `XRenderFindVisualFormat'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_drawable_get_picture':
(.text+0xb9a): undefined reference to `XRenderCreatePicture'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `shm_pixmap_info_destroy':
(.text+0xbd2): undefined reference to `XRenderFreePicture'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `shm_pixmap_info_destroy':
(.text+0xbf2): undefined reference to `XRenderFreePicture'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_pixbuf':
(.text+0xc8b): undefined reference to `XRenderFindFormat'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_pixbuf':
(.text+0xcc0): undefined reference to `XRenderFindFormat'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_pixbuf':
(.text+0xf11): undefined reference to `XRenderSetPictureClipRectangles'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_pixbuf':
(.text+0x10c7): undefined reference to `XRenderCreatePicture'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_pixbuf':
(.text+0x1113): undefined reference to `XRenderCreatePicture'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_pixbuf':
(.text+0x12fb): undefined reference to `XRenderComposite'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_pixbuf':
(.text+0x1313): undefined reference to `XRenderFreePicture'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_pixbuf':
(.text+0x1335): undefined reference to `XRenderFreePicture'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_pixbuf':
(.text+0x1380): undefined reference to `XRenderFindFormat'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_pixbuf':
(.text+0x13ae): undefined reference to `XRenderFindFormat'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_pixbuf':
(.text+0x1418): undefined reference to `XRenderFindFormat'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_pixbuf':
(.text+0x1524): undefined reference to `XRenderComposite'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_pixbuf':
(.text+0x15e7): undefined reference to `XRenderCreatePicture'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_pixbuf':
(.text+0x162d): undefined reference to `XRenderCreatePicture'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_pixbuf':
(.text+0x168b): undefined reference to `XRenderChangePicture'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_image':
(.text+0x176c): undefined reference to `XPutImage'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_image':
(.text+0x17f3): undefined reference to `XShmPutImage'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_lines':
(.text+0x189a): undefined reference to `XDrawLines'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_segments':
(.text+0x1936): undefined reference to `XDrawLine'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_segments':
(.text+0x19c3): undefined reference to `XDrawSegments'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_points':
(.text+0x1a59): undefined reference to `XDrawPoint'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_points':
(.text+0x1ad2): undefined reference to `XDrawPoints'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_drawable':
(.text+0x1c95): undefined reference to `XCopyArea'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_text_wc':
(.text+0x1d90): undefined reference to `XwcDrawString'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_text_wc':
(.text+0x1dc8): undefined reference to `XSetFont'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_text_wc':
(.text+0x1e21): undefined reference to `XDrawString'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_text':
(.text+0x1f2a): undefined reference to `XSetFont'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_text':
(.text+0x1fd5): undefined reference to `XmbDrawString'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_polygon':
(.text+0x2130): undefined reference to `XFillPolygon'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_polygon':
(.text+0x218a): undefined reference to `XDrawLines'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_text':
(.text+0x1f88): undefined reference to `XDrawString16'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_text':
(.text+0x203f): undefined reference to `XDrawString'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_arc':
(.text+0x2278): undefined reference to `XFillArc'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_arc':
(.text+0x22ca): undefined reference to `XDrawArc'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_rectangle':
(.text+0x2360): undefined reference to `XFillRectangle'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkdrawable-x11.o): In function `gdk_x11_draw_rectangle':
(.text+0x23a6): undefined reference to `XDrawRectangle'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `fetch_net_wm_check_window':
(.text+0x3a7): undefined reference to `XGetWindowProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `fetch_net_wm_check_window':
(.text+0x3c0): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `fetch_net_wm_check_window':
(.text+0x3f0): undefined reference to `XSelectInput'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `fetch_net_wm_check_window':
(.text+0x409): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `gdk_x11_screen_supports_net_wm_hint':
(.text+0x4f0): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `gdk_x11_screen_supports_net_wm_hint':
(.text+0x56c): undefined reference to `XGetWindowProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `gdk_x11_screen_get_window_manager_name':
(.text+0x72f): undefined reference to `XGetWindowProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `gdk_x11_screen_get_window_manager_name':
(.text+0x777): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `gdk_x11_get_server_time':
(.text+0x8f3): undefined reference to `XChangeProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `gdk_x11_get_server_time':
(.text+0x911): undefined reference to `XIfEvent'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `gdk_flush':
(.text+0x9d9): undefined reference to `XSync'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `gdk_event_send_client_message_to_all_recurse':
(.text+0xa72): undefined reference to `XGetWindowProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `gdk_event_send_client_message_to_all_recurse':
(.text+0xa91): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `gdk_event_send_client_message_to_all_recurse':
(.text+0xafa): undefined reference to `XQueryTree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `gdk_event_send_client_message_to_all_recurse':
(.text+0xb72): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `gdk_events_pending':
(.text+0xc03): undefined reference to `XPending'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `gdk_event_check':
(.text+0xc72): undefined reference to `XPending'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `gdk_event_prepare':
(.text+0xcd1): undefined reference to `XPending'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `gdk_check_wm_desktop_changed':
(.text+0x1355): undefined reference to `XGetWindowProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `gdk_check_wm_desktop_changed':
(.text+0x1392): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `gdk_event_translate':
(.text+0x1bb2): undefined reference to `XRefreshKeyboardMapping'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `gdk_event_translate':
(.text+0x2613): undefined reference to `XPending'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `gdk_event_translate':
(.text+0x2c1d): undefined reference to `XPeekEvent'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `gdk_event_translate':
(.text+0x2dc4): undefined reference to `XFixesCreateRegion'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `gdk_event_translate':
(.text+0x2df0): undefined reference to `XDamageSubtract'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `gdk_event_translate':
(.text+0x2e05): undefined reference to `XFixesDestroyRegion'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `gdk_event_translate':
(.text+0x2eff): undefined reference to `XGetWindowProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `gdk_event_translate':
(.text+0x2fe8): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `gdk_event_translate':
(.text+0x30d7): undefined reference to `XTranslateCoordinates'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `_gdk_events_queue':
(.text+0x3187): undefined reference to `XPending'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `_gdk_events_queue':
(.text+0x31a1): undefined reference to `XNextEvent'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `_gdk_events_queue':
(.text+0x31bf): undefined reference to `XFilterEvent'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `gdk_event_get_graphics_expose':
(.text+0x32bd): undefined reference to `XIfEvent'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkevents-x11.o): In function `gdk_wm_protocols_filter':
(.text+0x37cd): undefined reference to `XSendEvent'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkfont-x11.o): In function `gdk_text_extents_wc':
(.text+0x1e8): undefined reference to `XTextExtents'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkfont-x11.o): In function `gdk_text_extents_wc':
(.text+0x295): undefined reference to `XwcTextExtents'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkfont-x11.o): In function `gdk_text_extents':
(.text+0x3e0): undefined reference to `XTextExtents16'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkfont-x11.o): In function `gdk_text_extents':
(.text+0x460): undefined reference to `XmbTextExtents'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkfont-x11.o): In function `gdk_text_extents':
(.text+0x4e3): undefined reference to `XTextExtents'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkfont-x11.o): In function `gdk_text_width_wc':
(.text+0x5ef): undefined reference to `XTextWidth'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkfont-x11.o): In function `gdk_font_equal':
(.text+0x837): undefined reference to `XBaseFontNameListOfFontSet'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkfont-x11.o): In function `gdk_font_equal':
(.text+0x844): undefined reference to `XBaseFontNameListOfFontSet'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkfont-x11.o): In function `_gdk_font_destroy':
(.text+0xaea): undefined reference to `XFreeFont'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkfont-x11.o): In function `_gdk_font_destroy':
(.text+0xb49): undefined reference to `XFreeFontSet'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkfont-x11.o): In function `gdk_fontset_load_for_display':
(.text+0xd1d): undefined reference to `XCreateFontSet'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkfont-x11.o): In function `gdk_fontset_load_for_display':
(.text+0xd58): undefined reference to `XFontsOfFontSet'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkfont-x11.o): In function `gdk_fontset_load_for_display':
(.text+0xe1d): undefined reference to `XFreeStringList'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkfont-x11.o): In function `gdk_font_load_for_display':
(.text+0xeff): undefined reference to `XLoadQueryFont'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkfont-x11.o): In function `gdk_font_load_for_display':
(.text+0xf33): undefined reference to `XFreeFont'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkfont-x11.o): In function `gdk_text_width_wc':
(.text+0x5ae): undefined reference to `XwcTextEscapement'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkfont-x11.o): In function `gdk_text_width':
(.text+0x6b8): undefined reference to `XTextWidth16'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkfont-x11.o): In function `gdk_text_width':
(.text+0x6ee): undefined reference to `XmbTextEscapement'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkfont-x11.o): In function `gdk_text_width':
(.text+0x70b): undefined reference to `XTextWidth'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkgc-x11.o): In function `_gdk_windowing_gc_copy':
(.text+0x41): undefined reference to `XCopyGC'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkgc-x11.o): In function `_gdk_windowing_gc_set_clip_region':
(.text+0xbc): undefined reference to `XSetClipMask'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkgc-x11.o): In function `_gdk_x11_gc_flush':
(.text+0x140): undefined reference to `XSetTSOrigin'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkgc-x11.o): In function `_gdk_x11_gc_flush':
(.text+0x1c0): undefined reference to `XSetClipRectangles'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkgc-x11.o): In function `_gdk_x11_gc_flush':
(.text+0x1ee): undefined reference to `XSetClipOrigin'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkgc-x11.o): In function `_gdk_x11_gc_new':
(.text+0xa05): undefined reference to `XCreateGC'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkgc-x11.o): In function `gdk_x11_gc_set_dashes':
(.text+0xaff): undefined reference to `XSetDashes'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkgc-x11.o): In function `gdk_x11_gc_set_values':
(.text+0xbc0): undefined reference to `XChangeGC'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkgc-x11.o): In function `gdk_x11_gc_get_values':
(.text+0xc11): undefined reference to `XGetGCValues'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkgc-x11.o): In function `gdk_gc_x11_finalize':
(.text+0xf7e): undefined reference to `XFreeGC'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkgeometry-x11.o): In function `gdk_window_queue':
(.text+0x38f): undefined reference to `XSync'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkgeometry-x11.o): In function `gdk_window_queue':
(.text+0x3ad): undefined reference to `XCheckIfEvent'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkgeometry-x11.o): In function `unmap_if_needed':
(.text+0xb53): undefined reference to `XUnmapWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkgeometry-x11.o): In function `gdk_window_premove':
(.text+0xc71): undefined reference to `XMoveResizeWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkgeometry-x11.o): In function `map_if_needed':
(.text+0xddb): undefined reference to `XMapWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkgeometry-x11.o): In function `_gdk_window_move_resize_child':
(.text+0xfa9): undefined reference to `XMoveWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkgeometry-x11.o): In function `_gdk_window_move_resize_child':
(.text+0x10e1): undefined reference to `XMoveResizeWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkgeometry-x11.o): In function `_gdk_window_move_resize_child':
(.text+0x11ae): undefined reference to `XMoveResizeWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkgeometry-x11.o): In function `_gdk_window_move_resize_child':
(.text+0x11f7): undefined reference to `XMoveWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkgeometry-x11.o): In function `_gdk_window_move_resize_child':
(.text+0x1276): undefined reference to `XMoveResizeWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkgeometry-x11.o): In function `gdk_window_postmove':
(.text+0x1434): undefined reference to `XMoveResizeWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkgeometry-x11.o): In function `_gdk_x11_window_move_region':
(.text+0x16b1): undefined reference to `XCopyArea'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkgeometry-x11.o): In function `_gdk_x11_window_scroll':
(.text+0x188b): undefined reference to `XCopyArea'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkgeometry-x11.o): In function `_gdk_x11_window_scroll':
(.text+0x1a38): undefined reference to `XMoveResizeWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkgeometry-x11.o): In function `_gdk_x11_window_scroll':
(.text+0x1aa0): undefined reference to `XMoveWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkgeometry-x11.o): In function `_gdk_x11_window_scroll':
(.text+0x1af3): undefined reference to `XMoveResizeWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkim-x11.o): In function `gdk_mbstowcs':
(.text+0x96): undefined reference to `XmbTextListToTextProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkim-x11.o): In function `gdk_mbstowcs':
(.text+0xba): undefined reference to `XwcTextPropertyToTextList'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkim-x11.o): In function `gdk_mbstowcs':
(.text+0xcb): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkim-x11.o): In function `gdk_mbstowcs':
(.text+0x111): undefined reference to `XwcFreeStringList'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkim-x11.o): In function `gdk_mbstowcs':
(.text+0x136): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkim-x11.o): In function `gdk_wcstombs':
(.text+0x1d1): undefined reference to `XwcTextListToTextProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkim-x11.o): In function `gdk_wcstombs':
(.text+0x1ed): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkim-x11.o): In function `_gdk_x11_initialize_locale':
(.text+0x25f): undefined reference to `XSupportsLocale'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkim-x11.o): In function `_gdk_x11_initialize_locale':
(.text+0x2f8): undefined reference to `XSetLocaleModifiers'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkimage-x11.o): In function `_gdk_windowing_get_bits_for_depth':
(.text+0x1a): undefined reference to `XListPixmapFormats'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkimage-x11.o): In function `_gdk_windowing_get_bits_for_depth':
(.text+0x52): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkimage-x11.o): In function `_gdk_x11_image_get_shm_pixmap':
(.text+0x10f): undefined reference to `XShmCreatePixmap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkimage-x11.o): In function `_gdk_windowing_image_init':
(.text+0x147): undefined reference to `XShmQueryExtension'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkimage-x11.o): In function `_gdk_windowing_image_init':
(.text+0x179): undefined reference to `XShmQueryVersion'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkimage-x11.o): In function `_gdk_windowing_image_init':
(.text+0x18b): undefined reference to `XShmGetEventBase'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkimage-x11.o): In function `get_full_image':
(.text+0x557): undefined reference to `XGetImage'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkimage-x11.o): In function `_gdk_image_new_for_depth':
(.text+0x791): undefined reference to `XCreateImage'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkimage-x11.o): In function `_gdk_image_new_for_depth':
(.text+0x983): undefined reference to `XShmCreateImage'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkimage-x11.o): In function `_gdk_image_new_for_depth':
(.text+0xa0a): undefined reference to `XShmAttach'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkimage-x11.o): In function `_gdk_image_new_for_depth':
(.text+0xa23): undefined reference to `XSync'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkimage-x11.o): In function `_gdk_x11_copy_to_image':
(.text+0xd77): undefined reference to `XTranslateCoordinates'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkimage-x11.o): In function `_gdk_x11_copy_to_image':
(.text+0xe80): undefined reference to `XGetSubImage'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkimage-x11.o): In function `_gdk_x11_copy_to_image':
(.text+0xf54): undefined reference to `XCreateGC'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkimage-x11.o): In function `_gdk_x11_copy_to_image':
(.text+0xfa0): undefined reference to `XCopyArea'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkimage-x11.o): In function `_gdk_x11_copy_to_image':
(.text+0xfb6): undefined reference to `XSync'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkimage-x11.o): In function `_gdk_x11_copy_to_image':
(.text+0xfc8): undefined reference to `XFreeGC'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkimage-x11.o): In function `gdk_image_new_bitmap':
(.text+0x11f7): undefined reference to `XCreateImage'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkimage-x11.o): In function `gdk_x11_image_destroy':
(.text+0x1361): undefined reference to `XShmDetach'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkimage-x11.o): In function `gdk_x11_image_destroy':
(.text+0x1399): undefined reference to `XFreePixmap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkinput.o): In function `gdk_device_get_history':
(.text+0x81f): undefined reference to `XGetMotionEvents'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkinput.o): In function `gdk_device_get_history':
(.text+0x876): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkkeys-x11.o): In function `update_modmap':
(.text+0x1e8): undefined reference to `XInternAtom'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkkeys-x11.o): In function `get_xkb':
(.text+0x2c7): undefined reference to `XkbGetUpdatedMap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkkeys-x11.o): In function `get_xkb':
(.text+0x2de): undefined reference to `XkbGetNames'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkkeys-x11.o): In function `get_xkb':
(.text+0x312): undefined reference to `XDisplayKeycodes'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkkeys-x11.o): In function `get_xkb':
(.text+0x32c): undefined reference to `XkbGetMap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkkeys-x11.o): In function `gdk_keyval_convert_case':
(.text+0x46a): undefined reference to `XConvertCase'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkkeys-x11.o): In function `update_keymaps':
(.text+0x4ff): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkkeys-x11.o): In function `update_keymaps':
(.text+0x50e): undefined reference to `XFreeModifiermap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkkeys-x11.o): In function `update_keymaps':
(.text+0x536): undefined reference to `XGetKeyboardMapping'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkkeys-x11.o): In function `update_keymaps':
(.text+0x63f): undefined reference to `XGetModifierMapping'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkkeys-x11.o): In function `update_keymaps':
(.text+0x955): undefined reference to `XDisplayKeycodes'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkkeys-x11.o): In function `gdk_keymap_translate_keyboard_state':
(.text+0xf40): undefined reference to `XDisplayKeycodes'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkkeys-x11.o): In function `gdk_keymap_get_entries_for_keycode':
(.text+0x1460): undefined reference to `XDisplayKeycodes'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkkeys-x11.o): In function `gdk_keymap_have_bidi_layouts':
(.text+0x1b1f): undefined reference to `XkbGetControls'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkkeys-x11.o): In function `gdk_keymap_have_bidi_layouts':
(.text+0x1b33): undefined reference to `XkbGetUpdatedMap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkkeys-x11.o): In function `gdk_keymap_get_direction':
(.text+0x1c59): undefined reference to `XkbGetState'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkkeys-x11.o): In function `gdk_keymap_x11_finalize':
(.text+0x1e95): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkkeys-x11.o): In function `gdk_keymap_x11_finalize':
(.text+0x1ea4): undefined reference to `XFreeModifiermap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkkeys-x11.o): In function `gdk_keymap_x11_finalize':
(.text+0x1ec3): undefined reference to `XkbFreeKeyboard'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkkeys-x11.o): In function `gdk_keyval_from_name':
(.text+0x97f): undefined reference to `XStringToKeysym'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkkeys-x11.o): In function `gdk_keyval_name':
(.text+0x9ef): undefined reference to `XKeysymToString'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkmain-x11.o): In function `gdk_error_trap_pop':
(.text+0x205): undefined reference to `XSetErrorHandler'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkmain-x11.o): In function `gdk_error_trap_push':
(.text+0x271): undefined reference to `XSetErrorHandler'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkmain-x11.o): In function `_gdk_send_xevent':
(.text+0x310): undefined reference to `XSendEvent'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkmain-x11.o): In function `_gdk_send_xevent':
(.text+0x325): undefined reference to `XSync'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkmain-x11.o): In function `gdk_x_error':
(.text+0x3b7): undefined reference to `XGetErrorText'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkmain-x11.o): In function `_gdk_windowing_exit':
(.text+0x451): undefined reference to `XCloseDisplay'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkmain-x11.o): In function `_gdk_windowing_display_set_sm_client_id':
(.text+0x4b9): undefined reference to `XDeleteProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkmain-x11.o): In function `_gdk_windowing_display_set_sm_client_id':
(.text+0x51f): undefined reference to `XChangeProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkmain-x11.o): In function `gdk_keyboard_grab':
(.text+0x9b9): undefined reference to `XGrabKeyboard'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkmain-x11.o): In function `gdk_pointer_grab':
(.text+0xd32): undefined reference to `XGrabPointer'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkmain-x11.o): In function `_gdk_windowing_init':
(.text+0xde3): undefined reference to `XSetErrorHandler'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkmain-x11.o): In function `_gdk_windowing_init':
(.text+0xdef): undefined reference to `XSetIOErrorHandler'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkpixmap-x11.o): In function `gdk_pixmap_foreign_new_for_display':
(.text+0x32c): undefined reference to `XGetGeometry'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkpixmap-x11.o): In function `gdk_pixmap_create_from_data':
(.text+0x55c): undefined reference to `XCreatePixmapFromBitmapData'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkpixmap-x11.o): In function `gdk_bitmap_create_from_data':
(.text+0x818): undefined reference to `XCreateBitmapFromData'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkpixmap-x11.o): In function `gdk_pixmap_new':
(.text+0x9b4): undefined reference to `XCreatePixmap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkpixmap-x11.o): In function `gdk_pixmap_impl_x11_dispose':
(.text+0xc56): undefined reference to `XFreePixmap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkproperty-x11.o): In function `gdk_x11_xatom_to_atom_for_display':
(.text+0x2c8): undefined reference to `XGetAtomName'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkproperty-x11.o): In function `gdk_x11_xatom_to_atom_for_display':
(.text+0x316): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkproperty-x11.o): In function `_gdk_x11_precache_atoms':
(.text+0x51e): undefined reference to `XInternAtoms'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkproperty-x11.o): In function `gdk_x11_atom_to_xatom_for_display':
(.text+0x605): undefined reference to `XInternAtom'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkproperty-x11.o): In function `gdk_property_delete':
(.text+0x70b): undefined reference to `XDeleteProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkproperty-x11.o): In function `gdk_property_change':
(.text+0x92a): undefined reference to `XChangeProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkproperty-x11.o): In function `gdk_property_change':
(.text+0x978): undefined reference to `XChangeProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkproperty-x11.o): In function `gdk_property_get':
(.text+0xafc): undefined reference to `XGetWindowProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkproperty-x11.o): In function `gdk_property_get':
(.text+0xb50): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkproperty-x11.o): In function `gdk_property_get':
(.text+0xc1d): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkproperty-x11.o): In function `gdk_property_get':
(.text+0xca8): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkscreen-x11.o): In function `gdk_screen_get_window_stack':
(.text+0x761): undefined reference to `XGetWindowProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkscreen-x11.o): In function `gdk_screen_get_window_stack':
(.text+0x77a): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkscreen-x11.o): In function `gdk_screen_get_active_window':
(.text+0x901): undefined reference to `XGetWindowProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkscreen-x11.o): In function `gdk_screen_get_active_window':
(.text+0x91a): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkscreen-x11.o): In function `init_multihead':
(.text+0xc07): undefined reference to `XQueryExtension'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkscreen-x11.o): In function `init_multihead':
(.text+0xc19): undefined reference to `XineramaIsActive'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkscreen-x11.o): In function `init_multihead':
(.text+0xc93): undefined reference to `XineramaQueryScreens'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkscreen-x11.o): In function `init_multihead':
(.text+0xd3e): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkscreen-x11.o): In function `init_multihead':
(.text+0xd5a): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkscreen-x11.o): In function `_gdk_x11_screen_size_changed':
(.text+0xdb1): undefined reference to `XRRUpdateConfiguration'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkscreen-x11.o): In function `_gdk_x11_screen_new':
(.text+0x10d1): undefined reference to `XGetSelectionOwner'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkscreen-x11.o): In function `_gdk_x11_screen_new':
(.text+0x1106): undefined reference to `XSelectInput'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkscreen-x11.o): In function `_gdk_x11_screen_new':
(.text+0x1126): undefined reference to `XRRSelectInput'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkselection-x11.o): In function `gdk_string_to_compound_text_for_display':
(.text+0x2cd): undefined reference to `XmbTextListToTextProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkselection-x11.o): In function `gdk_text_property_to_text_list_for_display':
(.text+0x7e0): undefined reference to `XmbTextPropertyToTextList'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkselection-x11.o): In function `gdk_text_property_to_text_list_for_display':
(.text+0x80f): undefined reference to `XFreeStringList'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkselection-x11.o): In function `gdk_selection_property_get':
(.text+0xdd2): undefined reference to `XGetWindowProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkselection-x11.o): In function `gdk_selection_property_get':
(.text+0xf28): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkselection-x11.o): In function `gdk_selection_convert':
(.text+0x1013): undefined reference to `XConvertSelection'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkselection-x11.o): In function `gdk_selection_owner_get_for_display':
(.text+0x10c9): undefined reference to `XGetSelectionOwner'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkselection-x11.o): In function `gdk_selection_owner_set_for_display':
(.text+0x129e): undefined reference to `XSetSelectionOwner'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkselection-x11.o): In function `gdk_selection_owner_set_for_display':
(.text+0x12b0): undefined reference to `XGetSelectionOwner'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkselection-x11.o): In function `gdk_free_compound_text':
(.text+0xc): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkselection-x11.o): In function `gdk_free_text_list':
(.text+0x6ef): undefined reference to `XFreeStringList'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkvisual-x11.o): In function `_gdk_visual_init':
(.text+0x59c): undefined reference to `XGetVisualInfo'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkvisual-x11.o): In function `_gdk_visual_init':
(.text+0x70f): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `_gdk_windowing_window_set_composited':
(.text+0x12b): undefined reference to `XCompositeUnredirectWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `_gdk_windowing_window_set_composited':
(.text+0x13a): undefined reference to `XDamageDestroy'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `_gdk_windowing_window_set_composited':
(.text+0x168): undefined reference to `XCompositeRedirectWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `_gdk_windowing_window_set_composited':
(.text+0x17c): undefined reference to `XDamageCreate'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_set_opacity':
(.text+0x2cc): undefined reference to `XDeleteProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_set_opacity':
(.text+0x355): undefined reference to `XChangeProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_beep':
(.text+0x3d6): undefined reference to `XkbBell'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_configure_finished':
(.text+0x52e): undefined reference to `XSyncSetCounter'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `ensure_sync_counter':
(.text+0x5c5): undefined reference to `XSyncCreateCounter'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `ensure_sync_counter':
(.text+0x618): undefined reference to `XChangeProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_x11_window_set_user_time':
(.text+0xa15): undefined reference to `XChangeProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_set_type_hint':
(.text+0xc34): undefined reference to `XChangeProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `_gdk_moveresize_handle_event':
(.text+0x10ed): undefined reference to `XCheckIfEvent'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_x11_get_geometry':
(.text+0x11f0): undefined reference to `XGetGeometry'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_x11_get_events':
(.text+0x1293): undefined reference to `XGetWindowAttributes'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_add_rectangles':
(.text+0x12fa): undefined reference to `XShapeGetRectangles'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_add_rectangles':
(.text+0x148b): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_propagate_shapes':
(.text+0x166e): undefined reference to `XGetGeometry'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_propagate_shapes':
(.text+0x16f1): undefined reference to `XQueryTree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_propagate_shapes':
(.text+0x1741): undefined reference to `XGetWindowAttributes'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_propagate_shapes':
(.text+0x1792): undefined reference to `XGetGeometry'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_propagate_shapes':
(.text+0x1843): undefined reference to `XShapeCombineRectangles'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_propagate_shapes':
(.text+0x1856): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_set_mwm_hints':
(.text+0x1c14): undefined reference to `XGetWindowProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_set_mwm_hints':
(.text+0x1c82): undefined reference to `XChangeProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_set_mwm_hints':
(.text+0x1c92): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_set_mwm_hints':
(.text+0x1cde): undefined reference to `XChangeProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_get_decorations':
(.text+0x1dd7): undefined reference to `XGetWindowProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_get_decorations':
(.text+0x1e15): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_get_type_hint':
(.text+0x1f27): undefined reference to `XGetWindowProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_get_type_hint':
(.text+0x1f55): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `update_wm_hints':
(.text+0x21f2): undefined reference to `XSetWMHints'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_iconify':
(.text+0x27a1): undefined reference to `XIconifyWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_set_startup_id':
(.text+0x28b6): undefined reference to `XChangeProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_set_startup_id':
(.text+0x28e5): undefined reference to `XDeleteProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_set_role':
(.text+0x29c4): undefined reference to `XChangeProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_set_role':
(.text+0x29f5): undefined reference to `XDeleteProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `set_text_property':
(.text+0x2b09): undefined reference to `XChangeProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_set_icon_name':
(.text+0x2c3d): undefined reference to `XChangeProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `set_wm_name':
(.text+0x2ce4): undefined reference to `XChangeProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_set_title':
(.text+0x2e3b): undefined reference to `XChangeProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_set_icon_list':
(.text+0x2fab): undefined reference to `XExtendedMaxRequestSize'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_set_icon_list':
(.text+0x2fc1): undefined reference to `XMaxRequestSize'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_set_icon_list':
(.text+0x3183): undefined reference to `XChangeProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_set_icon_list':
(.text+0x31a3): undefined reference to `XExtendedMaxRequestSize'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_set_icon_list':
(.text+0x31c6): undefined reference to `XExtendedMaxRequestSize'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_set_icon_list':
(.text+0x31d8): undefined reference to `XMaxRequestSize'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_set_icon_list':
(.text+0x3219): undefined reference to `XExtendedMaxRequestSize'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_set_icon_list':
(.text+0x3262): undefined reference to `XDeleteProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_set_override_redirect':
(.text+0x3300): undefined reference to `XChangeWindowAttributes'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_set_static_win_gravity':
(.text+0x33ac): undefined reference to `XChangeWindowAttributes'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_x11_set_static_gravities':
(.text+0x34c1): undefined reference to `XChangeWindowAttributes'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_input_shape_combine_region':
(.text+0x35bd): undefined reference to `XShapeCombineRectangles'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_x11_shape_combine_mask':
(.text+0x36c1): undefined reference to `XShapeCombineMask'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_display_warp_pointer':
(.text+0x37b2): undefined reference to `XWarpPointer'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_get_frame_extents':
(.text+0x392a): undefined reference to `XGetWindowProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_get_frame_extents':
(.text+0x39b0): undefined reference to `XGetWindowProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_get_frame_extents':
(.text+0x3a08): undefined reference to `XQueryTree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_get_frame_extents':
(.text+0x3a1f): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_get_frame_extents':
(.text+0x3aa8): undefined reference to `XGetGeometry'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_get_frame_extents':
(.text+0x3acf): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_get_frame_extents':
(.text+0x3b36): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_get_frame_extents':
(.text+0x3bdf): undefined reference to `XGetGeometry'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_get_frame_extents':
(.text+0x3c4f): undefined reference to `XTranslateCoordinates'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_get_deskrelative_origin':
(.text+0x3fa2): undefined reference to `XQueryTree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_get_deskrelative_origin':
(.text+0x3fc0): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_get_deskrelative_origin':
(.text+0x4039): undefined reference to `XGetWindowProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_get_deskrelative_origin':
(.text+0x404e): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_get_deskrelative_origin':
(.text+0x4094): undefined reference to `XTranslateCoordinates'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_x11_get_origin':
(.text+0x415e): undefined reference to `XTranslateCoordinates'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_set_transient_for':
(.text+0x41fb): undefined reference to `XSetTransientForHint'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_set_geometry_hints':
(.text+0x439f): undefined reference to `XSetWMNormalHints'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_set_hints':
(.text+0x44eb): undefined reference to `XSetWMNormalHints'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_x11_raise':
(.text+0x452f): undefined reference to `XRaiseWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_toplevel_x11_free_contents':
(.text+0x46b6): undefined reference to `XSyncDestroyCounter'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `_gdk_windowing_window_at_pointer':
(.text+0x48a6): undefined reference to `XQueryPointer'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `_gdk_windowing_window_at_pointer':
(.text+0x4912): undefined reference to `XQueryPointer'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `_gdk_windowing_window_at_pointer':
(.text+0x4a93): undefined reference to `XQueryPointer'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `_gdk_windowing_window_at_pointer':
(.text+0x4b6e): undefined reference to `XCreateWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `_gdk_windowing_window_at_pointer':
(.text+0x4b82): undefined reference to `XMapWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `_gdk_windowing_window_at_pointer':
(.text+0x4bd4): undefined reference to `XQueryPointer'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `_gdk_windowing_window_at_pointer':
(.text+0x4be6): undefined reference to `XDestroyWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `_gdk_windowing_window_at_pointer':
(.text+0x4cb7): undefined reference to `XQueryPointer'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `_gdk_windowing_get_pointer':
(.text+0x4d76): undefined reference to `XQueryPointer'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `_gdk_windowing_get_pointer':
(.text+0x4dff): undefined reference to `XCreateWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `_gdk_windowing_get_pointer':
(.text+0x4e3e): undefined reference to `XQueryPointer'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `_gdk_windowing_get_pointer':
(.text+0x4e4a): undefined reference to `XDestroyWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `_gdk_windowing_window_get_pointer':
(.text+0x4f5d): undefined reference to `XQueryPointer'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `setup_toplevel_window':
(.text+0x5119): undefined reference to `XSetWMProtocols'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `setup_toplevel_window':
(.text+0x5170): undefined reference to `XSetWMNormalHints'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `setup_toplevel_window':
(.text+0x51b7): undefined reference to `XSetWMProperties'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `setup_toplevel_window':
(.text+0x5212): undefined reference to `XChangeProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `setup_toplevel_window':
(.text+0x5278): undefined reference to `XChangeProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `setup_toplevel_window':
(.text+0x5313): undefined reference to `XCreateSimpleWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `setup_toplevel_window':
(.text+0x5329): undefined reference to `XSelectInput'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `setup_toplevel_window':
(.text+0x5335): undefined reference to `XMapWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `setup_toplevel_window':
(.text+0x53ba): undefined reference to `XChangeProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `setup_toplevel_window':
(.text+0x5437): undefined reference to `XSetTransientForHint'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_x11_set_events':
(.text+0x549a): undefined reference to `XSelectInput'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_add_colormap_windows':
(.text+0x5545): undefined reference to `XGetWMColormapWindows'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_add_colormap_windows':
(.text+0x55ab): undefined reference to `XSetWMColormapWindows'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_add_colormap_windows':
(.text+0x55c6): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_add_colormap_windows':
(.text+0x5624): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `_gdk_x11_window_tmp_unset_bg':
(.text+0x5722): undefined reference to `XSetWindowBackgroundPixmap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `_gdk_x11_window_tmp_reset_bg':
(.text+0x5a0c): undefined reference to `XSetWindowBackgroundPixmap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `_gdk_x11_window_tmp_reset_bg':
(.text+0x5aa1): undefined reference to `XSetWindowBackground'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_foreign_new_for_display':
(.text+0x5c3b): undefined reference to `XGetWindowAttributes'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_foreign_new_for_display':
(.text+0x5c87): undefined reference to `XQueryTree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_foreign_new_for_display':
(.text+0x5cb6): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `_gdk_window_new':
(.text+0x61f4): undefined reference to `XCreateWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `_gdk_window_new':
(.text+0x64b9): undefined reference to `XAllocClassHint'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `_gdk_window_new':
(.text+0x64df): undefined reference to `XSetClassHint'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `_gdk_window_new':
(.text+0x64e7): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_x11_set_cursor':
(.text+0x67f3): undefined reference to `XDefineCursor'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_x11_reparent':
(.text+0x685f): undefined reference to `XReparentWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_x11_reparent':
(.text+0x6a1c): undefined reference to `XDestroyWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_x11_set_background':
(.text+0x6add): undefined reference to `XSetWindowBackground'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_x11_move_resize':
(.text+0x6b60): undefined reference to `XResizeWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_x11_move_resize':
(.text+0x6bf6): undefined reference to `XMoveResizeWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_x11_move_resize':
(.text+0x6cb8): undefined reference to `XMoveWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_x11_lower':
(.text+0x6def): undefined reference to `XLowerWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_x11_clear_area':
(.text+0x6e52): undefined reference to `XClearArea'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_x11_withdraw':
(.text+0x6f5c): undefined reference to `XWithdrawWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_x11_hide':
(.text+0x7053): undefined reference to `XUnmapWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_x11_show':
(.text+0x7196): undefined reference to `XMapWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_x11_show':
(.text+0x71b3): undefined reference to `XRaiseWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_x11_show':
(.text+0x72a4): undefined reference to `XChangeProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_x11_show':
(.text+0x7305): undefined reference to `XChangeProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_x11_show':
(.text+0x7395): undefined reference to `XDeleteProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_x11_show':
(.text+0x73be): undefined reference to `XMapWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_x11_show':
(.text+0x7415): undefined reference to `XDeleteProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_impl_x11_get_colormap':
(.text+0x76b3): undefined reference to `XGetWindowAttributes'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_impl_x11_set_colormap':
(.text+0x7784): undefined reference to `XSetWindowColormap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `wmspec_moveresize':
(.text+0x787e): undefined reference to `XSendEvent'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_begin_resize_drag':
(.text+0x7b61): undefined reference to `XAllocSizeHints'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_begin_resize_drag':
(.text+0x7b8d): undefined reference to `XGetWMNormalHints'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_begin_resize_drag':
(.text+0x7bd4): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `move_to_current_desktop':
(.text+0x7e98): undefined reference to `XGetWindowProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `move_to_current_desktop':
(.text+0x7f60): undefined reference to `XSendEvent'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `move_to_current_desktop':
(.text+0x7f6b): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_wmspec_change_state':
(.text+0x810b): undefined reference to `XSendEvent'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_stick':
(.text+0x8aa1): undefined reference to `XSendEvent'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_focus':
(.text+0x8c56): undefined reference to `XSendEvent'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_focus':
(.text+0x8c74): undefined reference to `XRaiseWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `_gdk_windowing_window_destroy_foreign':
(.text+0x8d9b): undefined reference to `XSendEvent'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_input_shape_combine_mask':
(.text+0x8f81): undefined reference to `XShapeCombineMask'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_x11_shape_combine_region':
(.text+0x90cd): undefined reference to `XShapeCombineRectangles'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `_gdk_windowing_window_destroy':
(.text+0x47ca): undefined reference to `XDestroyWindow'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkwindow-x11.o): In function `gdk_window_x11_set_back_pixmap':
(.text+0x586f): undefined reference to `XSetWindowBackgroundPixmap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkxftdefaults.o): In function `get_boolean_default':
(.text+0x21): undefined reference to `XGetDefault'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkxftdefaults.o): In function `get_integer_default':
(.text+0x10a): undefined reference to `XGetDefault'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkxftdefaults.o): In function `_gdk_x11_get_xft_setting':
(.text+0x318): undefined reference to `XGetDefault'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkxftdefaults.o): In function `_gdk_x11_get_xft_setting':
(.text+0x3c3): undefined reference to `XRenderQuerySubpixelOrder'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(xsettings-client.o): In function `read_settings':
(.text+0x240): undefined reference to `XSetErrorHandler'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(xsettings-client.o): In function `read_settings':
(.text+0x29f): undefined reference to `XGetWindowProperty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(xsettings-client.o): In function `read_settings':
(.text+0x2a9): undefined reference to `XSetErrorHandler'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(xsettings-client.o): In function `read_settings':
(.text+0x2ec): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(xsettings-client.o): In function `check_manager_window':
(.text+0x7a2): undefined reference to `XGetSelectionOwner'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(xsettings-client.o): In function `check_manager_window':
(.text+0x7c1): undefined reference to `XFlush'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(xsettings-client.o): In function `check_manager_window':
(.text+0x822): undefined reference to `XSelectInput'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(xsettings-client.o): In function `check_manager_window':
(.text+0x833): undefined reference to `XUngrabServer'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(xsettings-client.o): In function `check_manager_window':
(.text+0x846): undefined reference to `XGrabServer'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(xsettings-client.o): In function `_gdk_xsettings_client_new_with_grab_funcs':
(.text+0xada): undefined reference to `XInternAtoms'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(xsettings-client.o): In function `_gdk_xsettings_client_new_with_grab_funcs':
(.text+0xb24): undefined reference to `XGetWindowAttributes'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(xsettings-client.o): In function `_gdk_xsettings_client_new_with_grab_funcs':
(.text+0xb45): undefined reference to `XSelectInput'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkinput-x11.o): In function `gdk_device_get_state':
(.text+0x82a): undefined reference to `XQueryDeviceState'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkinput-x11.o): In function `gdk_device_get_state':
(.text+0x894): undefined reference to `XFreeDeviceState'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkinput-x11.o): In function `_gdk_device_get_history':
(.text+0x9bc): undefined reference to `XGetDeviceMotionEvents'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkinput-x11.o): In function `_gdk_device_get_history':
(.text+0xa2b): undefined reference to `XFreeDeviceMotionEvents'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkinput-x11.o): In function `_gdk_input_common_init':
(.text+0xdba): undefined reference to `XQueryExtension'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkinput-x11.o): In function `_gdk_input_common_init':
(.text+0xe1b): undefined reference to `XListInputDevices'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkinput-x11.o): In function `_gdk_input_common_init':
(.text+0x11b7): undefined reference to `XOpenDevice'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkinput-x11.o): In function `_gdk_input_common_init':
(.text+0x121f): undefined reference to `XFreeDeviceList'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkinput-x11.o): In function `_gdk_input_common_select_events':
(.text+0x13bf): undefined reference to `XSelectExtensionEvent'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkinput-x11.o): In function `_gdk_input_get_root_relative_geometry':
(.text+0x1433): undefined reference to `XQueryTree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkinput-x11.o): In function `_gdk_input_get_root_relative_geometry':
(.text+0x1442): undefined reference to `XFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkinput-x11.o): In function `_gdk_input_get_root_relative_geometry':
(.text+0x1482): undefined reference to `XGetGeometry'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkinput-x11.o): In function `_gdk_input_get_root_relative_geometry':
(.text+0x14b7): undefined reference to `XTranslateCoordinates'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkinput-xfree.o): In function `_gdk_input_ungrab_pointer':
(.text+0x68): undefined reference to `XUngrabDevice'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkinput-xfree.o): In function `_gdk_input_grab_pointer':
(.text+0x1aa): undefined reference to `XGrabDevice'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkinput-xfree.o): In function `_gdk_input_grab_pointer':
(.text+0x215): undefined reference to `XUngrabDevice'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkinput-xfree.o): In function `gdk_input_check_proximity':
(.text+0x3ae): undefined reference to `XQueryDeviceState'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkinput-xfree.o): In function `gdk_input_check_proximity':
(.text+0x3e3): undefined reference to `XFreeDeviceState'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkasync.o): In function `_gdk_x11_set_input_focus_safe':
(.text+0x11c): undefined reference to `_XFlush'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkasync.o): In function `_gdk_x11_set_input_focus_safe':
(.text+0x12c): undefined reference to `_XFlush'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkasync.o): In function `_gdk_x11_get_window_child_info':
(.text+0x290): undefined reference to `_XReply'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkasync.o): In function `_gdk_x11_get_window_child_info':
(.text+0x2c0): undefined reference to `_XDeqAsyncHandler'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkasync.o): In function `_gdk_x11_get_window_child_info':
(.text+0x4cc): undefined reference to `_XFlush'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkasync.o): In function `_gdk_x11_get_window_child_info':
(.text+0x547): undefined reference to `_XEatData'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkasync.o): In function `_gdk_x11_get_window_child_info':
(.text+0x554): undefined reference to `_XFlush'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkasync.o): In function `_gdk_x11_get_window_child_info':
(.text+0x56c): undefined reference to `_XFlush'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkasync.o): In function `_gdk_x11_get_window_child_info':
(.text+0x5ed): undefined reference to `_XDeqAsyncHandler'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkasync.o): In function `_gdk_x11_get_window_child_info':
(.text+0x62c): undefined reference to `_XFlush'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkasync.o): In function `_gdk_x11_get_window_child_info':
(.text+0x67c): undefined reference to `_XFlush'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkasync.o): In function `_gdk_x11_get_window_child_info':
(.text+0x6b2): undefined reference to `_XRead'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkasync.o): In function `_gdk_x11_get_window_child_info':
(.text+0x6eb): undefined reference to `_XReply'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkasync.o): In function `list_children_handler':
(.text+0x850): undefined reference to `_XGetAsyncReply'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkasync.o): In function `get_child_info_handler':
(.text+0x942): undefined reference to `_XGetAsyncReply'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkasync.o): In function `get_child_info_handler':
(.text+0xa00): undefined reference to `_XGetAsyncReply'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkasync.o): In function `get_child_info_handler':
(.text+0xa70): undefined reference to `_XGetAsyncReply'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkasync.o): In function `set_input_focus_handler':
(.text+0xafa): undefined reference to `_XDeqAsyncHandler'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkasync.o): In function `set_input_focus_handler':
(.text+0xb55): undefined reference to `_XGetAsyncReply'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkasync.o): In function `_gdk_x11_send_client_message_async':
(.text+0xd34): undefined reference to `_XFlush'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkasync.o): In function `_gdk_x11_send_client_message_async':
(.text+0xd44): undefined reference to `_XFlush'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkasync.o): In function `send_event_handler':
(.text+0xe4c): undefined reference to `_XDeqAsyncHandler'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk-x11-2.0.a(gdkasync.o): In function `send_event_handler':
(.text+0xeb0): undefined reference to `_XGetAsyncReply'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `real_save_png':
(.text+0x27a): undefined reference to `png_create_write_struct'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `real_save_png':
(.text+0x28d): undefined reference to `png_create_info_struct'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `real_save_png':
(.text+0x2d2): undefined reference to `png_set_text'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `real_save_png':
(.text+0x2ef): undefined reference to `png_init_io'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `real_save_png':
(.text+0x308): undefined reference to `png_set_compression_level'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `real_save_png':
(.text+0x35d): undefined reference to `png_set_IHDR'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `real_save_png':
(.text+0x383): undefined reference to `png_set_sBIT'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `real_save_png':
(.text+0x395): undefined reference to `png_write_info'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `real_save_png':
(.text+0x3a4): undefined reference to `png_set_shift'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `real_save_png':
(.text+0x3af): undefined reference to `png_set_packing'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `real_save_png':
(.text+0x3e6): undefined reference to `png_write_rows'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `real_save_png':
(.text+0x402): undefined reference to `png_write_end'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `real_save_png':
(.text+0x530): undefined reference to `png_destroy_write_struct'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `real_save_png':
(.text+0x642): undefined reference to `png_set_write_fn'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `png_save_to_callback_write_func':
(.text+0x7bc): undefined reference to `png_get_io_ptr'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `png_simple_error_callback':
(.text+0x836): undefined reference to `png_get_error_ptr'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `png_error_callback':
(.text+0x8b6): undefined reference to `png_get_error_ptr'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `gdk_pixbuf__png_image_load_increment':
(.text+0x99e): undefined reference to `png_process_data'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `gdk_pixbuf__png_image_stop_load':
(.text+0xb70): undefined reference to `png_destroy_read_struct'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `gdk_pixbuf__png_image_begin_load':
(.text+0xc41): undefined reference to `png_create_read_struct_2'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `gdk_pixbuf__png_image_begin_load':
(.text+0xc63): undefined reference to `png_create_info_struct'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `gdk_pixbuf__png_image_begin_load':
(.text+0xc96): undefined reference to `png_set_progressive_read_fn'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `gdk_pixbuf__png_image_begin_load':
(.text+0xcc6): undefined reference to `png_destroy_read_struct'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `gdk_pixbuf__png_image_begin_load':
(.text+0xced): undefined reference to `png_destroy_read_struct'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `png_row_callback':
(.text+0xd32): undefined reference to `png_get_progressive_ptr'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `setup_png_transformations':
(.text+0xe17): undefined reference to `png_get_bit_depth'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `setup_png_transformations':
(.text+0xe66): undefined reference to `png_get_IHDR'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `setup_png_transformations':
(.text+0xe96): undefined reference to `png_get_valid'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `setup_png_transformations':
(.text+0xeca): undefined reference to `png_set_gray_to_rgb'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `setup_png_transformations':
(.text+0xee1): undefined reference to `png_read_update_info'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `setup_png_transformations':
(.text+0xf1e): undefined reference to `png_get_IHDR'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `setup_png_transformations':
(.text+0xf9c): undefined reference to `png_set_expand'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `setup_png_transformations':
(.text+0x1010): undefined reference to `png_set_interlace_handling'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `setup_png_transformations':
(.text+0x1034): undefined reference to `png_set_strip_16'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `setup_png_transformations':
(.text+0x1048): undefined reference to `png_get_channels'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `png_info_callback':
(.text+0x1176): undefined reference to `png_get_progressive_ptr'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `png_info_callback':
(.text+0x12a8): undefined reference to `png_get_text'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `gdk_pixbuf__png_image_load':
(.text+0x142e): undefined reference to `png_create_read_struct_2'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `gdk_pixbuf__png_image_load':
(.text+0x1443): undefined reference to `png_create_info_struct'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `gdk_pixbuf__png_image_load':
(.text+0x1473): undefined reference to `png_init_io'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `gdk_pixbuf__png_image_load':
(.text+0x1485): undefined reference to `png_read_info'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `gdk_pixbuf__png_image_load':
(.text+0x153c): undefined reference to `png_read_image'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `gdk_pixbuf__png_image_load':
(.text+0x154e): undefined reference to `png_read_end'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `gdk_pixbuf__png_image_load':
(.text+0x156e): undefined reference to `png_get_text'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `gdk_pixbuf__png_image_load':
(.text+0x1613): undefined reference to `png_destroy_read_struct'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `gdk_pixbuf__png_image_load':
(.text+0x1686): undefined reference to `png_destroy_read_struct'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `gdk_pixbuf__png_image_load':
(.text+0x16c4): undefined reference to `png_destroy_read_struct'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `png_save_to_callback_write_func':
(.text+0x7ff): undefined reference to `png_error'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `png_warning_callback':
(.text+0x815): undefined reference to `png_get_error_ptr'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `png_end_callback':
(.text+0xd05): undefined reference to `png_get_progressive_ptr'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-png.o): In function `png_row_callback':
(.text+0xda3): undefined reference to `png_progressive_combine_row'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `real_save_jpeg':
(.text+0x361): undefined reference to `jpeg_std_error'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `real_save_jpeg':
(.text+0x3a3): undefined reference to `jpeg_CreateCompress'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `real_save_jpeg':
(.text+0x436): undefined reference to `jpeg_set_defaults'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `real_save_jpeg':
(.text+0x450): undefined reference to `jpeg_set_quality'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `real_save_jpeg':
(.text+0x460): undefined reference to `jpeg_start_compress'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `real_save_jpeg':
(.text+0x4df): undefined reference to `jpeg_write_scanlines'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `real_save_jpeg':
(.text+0x501): undefined reference to `jpeg_finish_compress'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `real_save_jpeg':
(.text+0x509): undefined reference to `jpeg_destroy_compress'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `real_save_jpeg':
(.text+0x5fa): undefined reference to `jpeg_destroy_compress'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `real_save_jpeg':
(.text+0x62c): undefined reference to `jpeg_stdio_dest'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `gdk_pixbuf__jpeg_image_load_lines':
(.text+0xc1b): undefined reference to `jpeg_read_scanlines'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `gdk_pixbuf__jpeg_image_stop_load':
(.text+0xdb5): undefined reference to `jpeg_destroy_decompress'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `gdk_pixbuf__jpeg_image_stop_load':
(.text+0xdef): undefined reference to `jpeg_finish_decompress'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `gdk_pixbuf__jpeg_image_begin_load':
(.text+0xe96): undefined reference to `jpeg_CreateDecompress'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `gdk_pixbuf__jpeg_image_begin_load':
(.text+0xed3): undefined reference to `jpeg_std_error'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `gdk_pixbuf__jpeg_image_begin_load':
(.text+0xf13): undefined reference to `jpeg_resync_to_restart'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `gdk_pixbuf__jpeg_image_load_increment':
(.text+0x13fb): undefined reference to `jpeg_start_output'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `gdk_pixbuf__jpeg_image_load_increment':
(.text+0x143f): undefined reference to `jpeg_finish_output'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `gdk_pixbuf__jpeg_image_load_increment':
(.text+0x1458): undefined reference to `jpeg_input_complete'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `gdk_pixbuf__jpeg_image_load_increment':
(.text+0x1467): undefined reference to `jpeg_input_complete'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `gdk_pixbuf__jpeg_image_load_increment':
(.text+0x1517): undefined reference to `jpeg_save_markers'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `gdk_pixbuf__jpeg_image_load_increment':
(.text+0x1527): undefined reference to `jpeg_read_header'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `gdk_pixbuf__jpeg_image_load_increment':
(.text+0x159f): undefined reference to `jpeg_calc_output_dimensions'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `gdk_pixbuf__jpeg_image_load_increment':
(.text+0x15db): undefined reference to `jpeg_calc_output_dimensions'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `gdk_pixbuf__jpeg_image_load_increment':
(.text+0x1672): undefined reference to `jpeg_start_decompress'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `gdk_pixbuf__jpeg_image_load':
(.text+0x182d): undefined reference to `jpeg_std_error'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `gdk_pixbuf__jpeg_image_load':
(.text+0x188c): undefined reference to `jpeg_CreateDecompress'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `gdk_pixbuf__jpeg_image_load':
(.text+0x18e6): undefined reference to `jpeg_resync_to_restart'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `gdk_pixbuf__jpeg_image_load':
(.text+0x191e): undefined reference to `jpeg_save_markers'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `gdk_pixbuf__jpeg_image_load':
(.text+0x192e): undefined reference to `jpeg_read_header'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `gdk_pixbuf__jpeg_image_load':
(.text+0x193f): undefined reference to `jpeg_start_decompress'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `gdk_pixbuf__jpeg_image_load':
(.text+0x1a03): undefined reference to `jpeg_read_scanlines'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `gdk_pixbuf__jpeg_image_load':
(.text+0x1a52): undefined reference to `jpeg_destroy_decompress'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `gdk_pixbuf__jpeg_image_load':
(.text+0x1aa1): undefined reference to `jpeg_finish_decompress'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `gdk_pixbuf__jpeg_image_load':
(.text+0x1aa9): undefined reference to `jpeg_destroy_decompress'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-jpeg.o): In function `gdk_pixbuf__jpeg_image_load':
(.text+0x1bbd): undefined reference to `jpeg_destroy_decompress'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-tiff.o): In function `tiff_push_handlers':
(.text+0x203): undefined reference to `TIFFSetErrorHandler'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-tiff.o): In function `tiff_push_handlers':
(.text+0x214): undefined reference to `TIFFSetWarningHandler'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-tiff.o): In function `tiff_pop_handlers':
(.text+0x255): undefined reference to `TIFFSetErrorHandler'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-tiff.o): In function `tiff_pop_handlers':
(.text+0x262): undefined reference to `TIFFSetWarningHandler'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-tiff.o): In function `gdk_pixbuf__tiff_image_save_to_callback':
(.text+0x41a): undefined reference to `TIFFClientOpen'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-tiff.o): In function `gdk_pixbuf__tiff_image_save_to_callback':
(.text+0x4c1): undefined reference to `TIFFSetField'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-tiff.o): In function `gdk_pixbuf__tiff_image_save_to_callback':
(.text+0x4d8): undefined reference to `TIFFSetField'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-tiff.o): In function `gdk_pixbuf__tiff_image_save_to_callback':
(.text+0x4f0): undefined reference to `TIFFSetField'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-tiff.o): In function `gdk_pixbuf__tiff_image_save_to_callback':
(.text+0x510): undefined reference to `TIFFSetField'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-tiff.o): In function `gdk_pixbuf__tiff_image_save_to_callback':
(.text+0x527): undefined reference to `TIFFSetField'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-tiff.o):(.text+0x546): more undefined references to `TIFFSetField' follow
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-tiff.o): In function `gdk_pixbuf__tiff_image_save_to_callback':
(.text+0x5cc): undefined reference to `TIFFWriteScanline'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-tiff.o): In function `gdk_pixbuf__tiff_image_save_to_callback':
(.text+0x60c): undefined reference to `TIFFClose'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-tiff.o): In function `gdk_pixbuf__tiff_image_save_to_callback':
(.text+0x63c): undefined reference to `TIFFSetField'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-tiff.o): In function `gdk_pixbuf__tiff_image_save_to_callback':
(.text+0x653): undefined reference to `TIFFSetField'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-tiff.o): In function `gdk_pixbuf__tiff_image_save_to_callback':
(.text+0x664): undefined reference to `TIFFClose'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-tiff.o): In function `tiff_image_parse':
(.text+0x9ee): undefined reference to `TIFFGetField'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-tiff.o): In function `tiff_image_parse':
(.text+0xa3e): undefined reference to `TIFFGetField'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-tiff.o): In function `tiff_image_parse':
(.text+0xb28): undefined reference to `TIFFGetField'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-tiff.o): In function `tiff_image_parse':
(.text+0xb9a): undefined reference to `TIFFReadRGBAImageOriented'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-tiff.o): In function `gdk_pixbuf__tiff_image_stop_load':
(.text+0xe05): undefined reference to `TIFFClientOpen'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-tiff.o): In function `gdk_pixbuf__tiff_image_stop_load':
(.text+0xe49): undefined reference to `TIFFClose'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-tiff.o): In function `gdk_pixbuf__tiff_image_load':
(.text+0x1016): undefined reference to `TIFFFdOpen'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgdk_pixbuf-2.0.a(io-tiff.o): In function `gdk_pixbuf__tiff_image_load':
(.text+0x109a): undefined reference to `TIFFClose'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgio-2.0.a(glocalfileinfo.o): In function `set_selinux_context':
(.text+0x674): undefined reference to `is_selinux_enabled'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgio-2.0.a(glocalfileinfo.o): In function `set_selinux_context':
(.text+0x694): undefined reference to `setfilecon_raw'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgio-2.0.a(glocalfileinfo.o): In function `_g_local_file_info_set_attributes':
(.text+0x911): undefined reference to `is_selinux_enabled'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgio-2.0.a(glocalfileinfo.o): In function `_g_local_file_info_get_from_fd':
(.text+0x19a1): undefined reference to `is_selinux_enabled'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgio-2.0.a(glocalfileinfo.o): In function `_g_local_file_info_get_from_fd':
(.text+0x19b7): undefined reference to `fgetfilecon_raw'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgio-2.0.a(glocalfileinfo.o): In function `_g_local_file_info_get_from_fd':
(.text+0x19dd): undefined reference to `freecon'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgio-2.0.a(glocalfileinfo.o): In function `_g_local_file_info_get':
(.text+0x2c49): undefined reference to `is_selinux_enabled'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgio-2.0.a(glocalfileinfo.o): In function `_g_local_file_info_get':
(.text+0x2c6c): undefined reference to `lgetfilecon_raw'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgio-2.0.a(glocalfileinfo.o): In function `_g_local_file_info_get':
(.text+0x2ca4): undefined reference to `freecon'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgio-2.0.a(glocalfileinfo.o): In function `_g_local_file_info_get':
(.text+0x31ee): undefined reference to `getfilecon_raw'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-font-face.o): In function `_cairo_toy_font_face_hash_table_lock':
(.text+0x7e): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-font-face.o): In function `_cairo_toy_font_face_hash_table_lock':
(.text+0xb5): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-font-face.o): In function `_cairo_toy_font_face_destroy':
(.text+0x152): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-font-face.o): In function `_cairo_font_face_reset_static_data':
(.text+0x1e3): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-font-face.o): In function `_cairo_font_face_reset_static_data':
(.text+0x206): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-font-face.o): In function `cairo_toy_font_face_create':
(.text+0x5fb): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-font-face.o): In function `cairo_toy_font_face_create':
(.text+0x635): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-font-face.o): In function `cairo_toy_font_face_create':
(.text+0x678): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-gstate.o): In function `_cairo_gstate_glyph_path':
(.text+0xa12): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-gstate.o): In function `_cairo_gstate_glyph_path':
(.text+0xa41): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-gstate.o): In function `_cairo_gstate_glyph_path':
(.text+0xa8d): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-gstate.o): In function `_cairo_gstate_glyph_path':
(.text+0xabc): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-gstate.o): In function `_cairo_gstate_show_text_glyphs':
(.text+0xdf7): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-gstate.o): In function `_cairo_gstate_show_text_glyphs':
(.text+0xe2f): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-image-surface.o): In function `_cairo_image_surface_finish':
(.text+0x718): undefined reference to `pixman_image_unref'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-image-surface.o): In function `_cairo_image_surface_set_attributes':
(.text+0x780): undefined reference to `pixman_image_set_transform'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-image-surface.o): In function `_cairo_image_surface_set_attributes':
(.text+0x7cc): undefined reference to `pixman_image_set_repeat'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-image-surface.o): In function `_cairo_image_surface_set_attributes':
(.text+0x812): undefined reference to `pixman_image_set_filter'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-image-surface.o): In function `_cairo_image_surface_set_attributes':
(.text+0x86a): undefined reference to `pixman_image_set_repeat'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-image-surface.o): In function `_cairo_image_surface_set_attributes':
(.text+0x88a): undefined reference to `pixman_image_set_repeat'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-image-surface.o): In function `_cairo_image_surface_set_attributes':
(.text+0x8aa): undefined reference to `pixman_image_set_repeat'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-image-surface.o): In function `_cairo_image_surface_composite_trapezoids':
(.text+0xc08): undefined reference to `pixman_add_trapezoids'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-image-surface.o): In function `_cairo_image_surface_composite_trapezoids':
(.text+0xc8c): undefined reference to `pixman_image_create_bits'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-image-surface.o): In function `_cairo_image_surface_composite_trapezoids':
(.text+0xcd2): undefined reference to `pixman_add_trapezoids'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-image-surface.o): In function `_cairo_image_surface_composite_trapezoids':
(.text+0xd50): undefined reference to `pixman_image_composite'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-image-surface.o): In function `_cairo_image_surface_composite_trapezoids':
(.text+0xd6d): undefined reference to `pixman_image_unref'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-image-surface.o): In function `_cairo_image_surface_fill_rectangles':
(.text+0xf5a): undefined reference to `pixman_image_fill_rectangles'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-image-surface.o): In function `_cairo_image_surface_composite':
(.text+0x1132): undefined reference to `pixman_image_composite'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-image-surface.o): In function `_cairo_image_surface_set_clip_region':
(.text+0x12c0): undefined reference to `pixman_image_set_clip_region32'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-image-surface.o): In function `_pixman_format_from_masks':
(.text+0x13d9): undefined reference to `pixman_format_supported_destination'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-image-surface.o): In function `_cairo_image_surface_create_for_pixman_image':
(.text+0x1529): undefined reference to `pixman_image_get_data'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-image-surface.o): In function `_cairo_image_surface_create_for_pixman_image':
(.text+0x1555): undefined reference to `pixman_image_get_width'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-image-surface.o): In function `_cairo_image_surface_create_for_pixman_image':
(.text+0x1563): undefined reference to `pixman_image_get_height'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-image-surface.o): In function `_cairo_image_surface_create_for_pixman_image':
(.text+0x1571): undefined reference to `pixman_image_get_stride'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-image-surface.o): In function `_cairo_image_surface_create_for_pixman_image':
(.text+0x157f): undefined reference to `pixman_image_get_depth'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-image-surface.o): In function `_cairo_image_surface_create_with_pixman_format':
(.text+0x17ab): undefined reference to `pixman_image_create_bits'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-image-surface.o): In function `_cairo_image_surface_create_with_pixman_format':
(.text+0x17d3): undefined reference to `pixman_image_unref'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-matrix.o): In function `_cairo_matrix_to_pixman_matrix':
(.text+0xbe7): undefined reference to `pixman_transform_point_3d'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-pattern.o): In function `_cairo_pattern_reset_static_data':
(.text+0x140): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-pattern.o): In function `_cairo_pattern_reset_static_data':
(.text+0x196): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-pattern.o): In function `_cairo_pattern_reset_static_data':
(.text+0x1a2): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-pattern.o): In function `_cairo_pattern_reset_static_data':
(.text+0x1dc): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-pattern.o): In function `_cairo_pattern_reset_static_data':
(.text+0x1f0): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-pattern.o): In function `_cairo_pattern_reset_static_data':
(.text+0x205): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-pattern.o): In function `_cairo_pattern_acquire_surface_for_solid':
(.text+0x8b5): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-pattern.o): In function `_cairo_pattern_acquire_surface_for_solid':
(.text+0x99a): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-pattern.o): In function `_cairo_pattern_acquire_surface_for_solid':
(.text+0x9e0): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-pattern.o): In function `_cairo_pattern_acquire_surface':
(.text+0x1b64): undefined reference to `pixman_image_create_radial_gradient'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-pattern.o): In function `_cairo_pattern_acquire_surface':
(.text+0x1bda): undefined reference to `pixman_image_set_filter'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-pattern.o): In function `_cairo_pattern_acquire_surface':
(.text+0x1c34): undefined reference to `pixman_image_set_transform'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-pattern.o): In function `_cairo_pattern_acquire_surface':
(.text+0x1c68): undefined reference to `pixman_image_set_repeat'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-pattern.o): In function `_cairo_pattern_acquire_surface':
(.text+0x1cd6): undefined reference to `pixman_image_composite'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-pattern.o): In function `_cairo_pattern_acquire_surface':
(.text+0x1ce4): undefined reference to `pixman_image_unref'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-pattern.o): In function `_cairo_pattern_acquire_surface':
(.text+0x21cb): undefined reference to `pixman_image_create_linear_gradient'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-pattern.o): In function `_cairo_pattern_acquire_surface':
(.text+0x2202): undefined reference to `pixman_image_unref'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-pattern.o): In function `_cairo_pattern_acquire_surface':
(.text+0x22fc): undefined reference to `pixman_image_unref'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-pattern.o): In function `_cairo_pattern_acquire_surface':
(.text+0x2503): undefined reference to `pixman_image_unref'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-pattern.o): In function `_cairo_pattern_acquire_surface':
(.text+0x2538): undefined reference to `pixman_image_unref'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-pattern.o): In function `_cairo_pattern_acquire_surface':
(.text+0x2568): undefined reference to `pixman_image_set_repeat'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-pattern.o): In function `_cairo_pattern_acquire_surface':
(.text+0x27ce): undefined reference to `pixman_image_set_repeat'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-pattern.o): In function `_cairo_pattern_acquire_surface':
(.text+0x27e9): undefined reference to `pixman_image_set_repeat'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-pattern.o): In function `_cairo_pattern_create_solid':
(.text+0x281f): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-pattern.o): In function `_cairo_pattern_create_solid':
(.text+0x285d): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-pattern.o): In function `_cairo_pattern_create_solid':
(.text+0x2898): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-pattern.o): In function `cairo_pattern_destroy':
(.text+0x3046): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-pattern.o): In function `cairo_pattern_destroy':
(.text+0x3094): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-region.o): In function `_cairo_region_contains_rectangle':
(.text+0x2e): undefined reference to `pixman_region32_contains_rectangle'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-region.o): In function `_cairo_region_union_rect':
(.text+0x92): undefined reference to `pixman_region32_union_rect'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-region.o): In function `_cairo_region_intersect':
(.text+0xcb): undefined reference to `pixman_region32_intersect'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-region.o): In function `_cairo_region_subtract':
(.text+0x10b): undefined reference to `pixman_region32_subtract'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-region.o): In function `_cairo_region_get_extents':
(.text+0x141): undefined reference to `pixman_region32_extents'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-region.o): In function `_cairo_region_get_boxes':
(.text+0x197): undefined reference to `pixman_region32_rectangles'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-region.o): In function `_cairo_region_copy':
(.text+0x264): undefined reference to `pixman_region32_copy'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-region.o): In function `_cairo_region_init_boxes':
(.text+0x341): undefined reference to `pixman_region32_init_rects'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-region.o): In function `_cairo_region_init_rect':
(.text+0x3bb): undefined reference to `pixman_region32_init_rect'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-region.o): In function `_cairo_region_translate':
(.text+0x45): undefined reference to `pixman_region32_translate'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-region.o): In function `_cairo_region_not_empty':
(.text+0x55): undefined reference to `pixman_region32_not_empty'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-region.o): In function `_cairo_region_num_boxes':
(.text+0x245): undefined reference to `pixman_region32_n_rects'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-region.o): In function `_cairo_region_fini':
(.text+0x285): undefined reference to `pixman_region32_fini'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-region.o): In function `_cairo_region_init':
(.text+0x3d5): undefined reference to `pixman_region32_init'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `_cairo_scaled_font_reset_static_data':
(.text+0x831): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `_cairo_scaled_font_reset_static_data':
(.text+0x866): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `_cairo_scaled_font_create_in_error':
(.text+0x89c): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `_cairo_scaled_font_create_in_error':
(.text+0x8b3): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `_cairo_scaled_font_create_in_error':
(.text+0x970): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `_cairo_scaled_font_map_lock':
(.text+0xa4f): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `_cairo_scaled_font_map_lock':
(.text+0xac6): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `_cairo_scaled_font_fini':
(.text+0xcef): undefined reference to `pthread_mutex_destroy'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `cairo_scaled_font_destroy':
(.text+0xdd2): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `cairo_scaled_font_destroy':
(.text+0xe66): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `_cairo_scaled_font_unregister_placeholder_and_lock_font_map':
(.text+0xef2): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `_cairo_scaled_font_unregister_placeholder_and_lock_font_map':
(.text+0xf42): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `_cairo_scaled_font_unregister_placeholder_and_lock_font_map':
(.text+0xf4e): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `_cairo_scaled_font_unregister_placeholder_and_lock_font_map':
(.text+0xf65): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `cairo_scaled_font_create':
(.text+0x10b6): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `cairo_scaled_font_create':
(.text+0x10be): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `cairo_scaled_font_create':
(.text+0x10c6): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `cairo_scaled_font_create':
(.text+0x10d2): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `cairo_scaled_font_create':
(.text+0x11b0): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `cairo_scaled_font_create':
(.text+0x1292): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `cairo_scaled_font_create':
(.text+0x12b8): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `cairo_scaled_font_create':
(.text+0x13af): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `_cairo_scaled_font_map_destroy':
(.text+0x17e0): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `_cairo_scaled_font_map_destroy':
(.text+0x1800): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `_cairo_scaled_font_map_destroy':
(.text+0x1814): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `_cairo_scaled_font_map_destroy':
(.text+0x1849): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `_cairo_scaled_font_map_destroy':
(.text+0x185d): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `_cairo_scaled_font_map_destroy':
(.text+0x189d): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `_cairo_scaled_font_show_glyphs':
(.text+0x231b): undefined reference to `pixman_image_set_component_alpha'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `cairo_scaled_font_text_to_glyphs':
(.text+0x27c5): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `cairo_scaled_font_text_to_glyphs':
(.text+0x2904): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `cairo_scaled_font_text_to_glyphs':
(.text+0x2a32): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `cairo_scaled_font_text_to_glyphs':
(.text+0x2be2): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `cairo_scaled_font_text_to_glyphs':
(.text+0x2c0b): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `cairo_scaled_font_glyph_extents':
(.text+0x2cdb): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `cairo_scaled_font_glyph_extents':
(.text+0x2e93): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `_cairo_scaled_font_register_placeholder_and_unlock_font_map':
(.text+0x307f): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `_cairo_scaled_font_register_placeholder_and_unlock_font_map':
(.text+0x30a4): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `cairo_scaled_font_destroy':
(.text+0xdc4): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-scaled-font.o): In function `_cairo_scaled_font_register_placeholder_and_unlock_font_map':
(.text+0x305e): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-surface.o): In function `_cairo_surface_show_text_glyphs':
(.text+0x81d): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-surface.o): In function `_cairo_surface_show_text_glyphs':
(.text+0x899): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_create_internal':
(.text+0x3d6): undefined reference to `XRenderQueryVersion'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_create_internal':
(.text+0x6c3): undefined reference to `XRenderFindVisualFormat'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_create_internal':
(.text+0x7dc): undefined reference to `XRenderFindStandardFormat'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_detach_display':
(.text+0xa01): undefined reference to `XFreeGC'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_detach_display':
(.text+0xa20): undefined reference to `XRenderFreePicture'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_detach_display':
(.text+0xa40): undefined reference to `XRenderFreePicture'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_detach_display':
(.text+0xa66): undefined reference to `XFreePixmap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_emit_glyphs_chunk':
(.text+0xabb): undefined reference to `XRenderCompositeText8'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_emit_glyphs_chunk':
(.text+0xad5): undefined reference to `XRenderCompositeText16'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_emit_glyphs_chunk':
(.text+0xaeb): undefined reference to `XRenderCompositeText32'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_set_gc_clip_rects':
(.text+0xd6f): undefined reference to `XSetClipMask'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_set_gc_clip_rects':
(.text+0xdc0): undefined reference to `XSetClipRectangles'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_ensure_gc':
(.text+0xe6a): undefined reference to `XCreateGC'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_draw_image_surface':
(.text+0x1072): undefined reference to `XInitImage'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_draw_image_surface':
(.text+0x1900): undefined reference to `XInitImage'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_draw_image_surface':
(.text+0x198b): undefined reference to `XPutImage'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_create_solid_pattern_surface':
(.text+0x1a5e): undefined reference to `XCreatePixmap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_create_solid_pattern_surface':
(.text+0x1ac8): undefined reference to `XFreePixmap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_is_similar':
(.text+0x1c49): undefined reference to `XRenderFindVisualFormat'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_create_similar_with_format':
(.text+0x1cfd): undefined reference to `XCreatePixmap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_create_similar_with_format':
(.text+0x1d7e): undefined reference to `XFreePixmap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_create_similar':
(.text+0x1eb8): undefined reference to `XRenderFindVisualFormat'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_create_similar':
(.text+0x1f08): undefined reference to `XCreatePixmap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_create_similar':
(.text+0x1f79): undefined reference to `XFreePixmap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_set_attributes':
(.text+0x23b9): undefined reference to `XRenderCreatePicture'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_set_attributes':
(.text+0x247d): undefined reference to `XRenderChangePicture'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_set_attributes':
(.text+0x24d2): undefined reference to `XRenderSetPictureFilter'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_set_attributes':
(.text+0x2513): undefined reference to `XRenderSetPictureTransform'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_set_attributes':
(.text+0x260c): undefined reference to `XRenderChangePicture'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_set_picture_clip_rects':
(.text+0x265d): undefined reference to `XRenderChangePicture'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_set_picture_clip_rects':
(.text+0x26a8): undefined reference to `XRenderSetPictureClipRectangles'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_ensure_dst_picture':
(.text+0x2716): undefined reference to `XRenderCreatePicture'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_remove_scaled_font':
(.text+0x27df): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_remove_scaled_font':
(.text+0x27ff): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_remove_scaled_font':
(.text+0x2858): undefined reference to `XRenderFreeGlyphSet'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_show_glyphs':
(.text+0x2b24): undefined reference to `XMaxRequestSize'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_show_glyphs':
(.text+0x2ff1): undefined reference to `XRenderCreateGlyphSet'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_show_glyphs':
(.text+0x3041): undefined reference to `XExtendedMaxRequestSize'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_show_glyphs':
(.text+0x3057): undefined reference to `XExtendedMaxRequestSize'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_show_glyphs':
(.text+0x3668): undefined reference to `XRenderAddGlyphs'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_show_glyphs':
(.text+0x3719): undefined reference to `XMaxRequestSize'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_render_free_glyphs':
(.text+0x3b34): undefined reference to `XRenderFreeGlyphs'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_scaled_font_fini':
(.text+0x3bb8): undefined reference to `XRenderFreeGlyphSet'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_create_a8_picture':
(.text+0x3eea): undefined reference to `XCreatePixmap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_create_a8_picture':
(.text+0x3f0e): undefined reference to `XRenderFindStandardFormat'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_create_a8_picture':
(.text+0x3f32): undefined reference to `XRenderCreatePicture'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_create_a8_picture':
(.text+0x3f70): undefined reference to `XRenderFillRectangle'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_create_a8_picture':
(.text+0x3f85): undefined reference to `XFreePixmap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_composite_trapezoids':
(.text+0x40bc): undefined reference to `XRenderFindStandardFormat'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_composite_trapezoids':
(.text+0x43c3): undefined reference to `XRenderCompositeTrapezoids'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_composite_trapezoids':
(.text+0x4475): undefined reference to `XRenderFindStandardFormat'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_composite_trapezoids':
(.text+0x458f): undefined reference to `XRenderFreePicture'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_composite_trapezoids':
(.text+0x4859): undefined reference to `XRenderCompositeTrapezoids'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_composite_trapezoids':
(.text+0x486e): undefined reference to `XRenderFreePicture'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_composite_trapezoids':
(.text+0x48fa): undefined reference to `XRenderComposite'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_composite_trapezoids':
(.text+0x4915): undefined reference to `XRenderFreePicture'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_fill_rectangles':
(.text+0x4a8a): undefined reference to `XRenderFillRectangles'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_fill_rectangles':
(.text+0x4c45): undefined reference to `XRenderFillRectangles'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_fill_rectangles':
(.text+0x4cb5): undefined reference to `XSetTSOrigin'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_fill_rectangles':
(.text+0x4cdd): undefined reference to `XSetTile'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_fill_rectangles':
(.text+0x4d00): undefined reference to `XSetFillStyle'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_fill_rectangles':
(.text+0x4d52): undefined reference to `XFillRectangle'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_composite':
(.text+0x4f74): undefined reference to `XRenderComposite'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_composite':
(.text+0x50b2): undefined reference to `XCopyArea'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_composite':
(.text+0x511b): undefined reference to `XSetTSOrigin'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_composite':
(.text+0x5140): undefined reference to `XSetTile'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_composite':
(.text+0x5160): undefined reference to `XSetFillStyle'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_composite':
(.text+0x519e): undefined reference to `XFillRectangle'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `cairo_xlib_surface_set_drawable':
(.text+0x5450): undefined reference to `XRenderFreePicture'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `cairo_xlib_surface_set_drawable':
(.text+0x5480): undefined reference to `XRenderFreePicture'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_get_image_surface':
(.text+0x569a): undefined reference to `XCreatePixmap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_get_image_surface':
(.text+0x56c8): undefined reference to `XSetErrorHandler'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_get_image_surface':
(.text+0x5736): undefined reference to `XGetImage'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_get_image_surface':
(.text+0x5744): undefined reference to `XSetErrorHandler'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_get_image_surface':
(.text+0x6052): undefined reference to `XCopyArea'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_get_image_surface':
(.text+0x6092): undefined reference to `XGetImage'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_get_image_surface':
(.text+0x60aa): undefined reference to `XFreePixmap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_finish':
(.text+0x61c1): undefined reference to `XFreePixmap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_finish':
(.text+0x62c6): undefined reference to `XRenderFreePicture'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_finish':
(.text+0x62f8): undefined reference to `XRenderFreePicture'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_finish':
(.text+0x6328): undefined reference to `XRenderFreePicture'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-surface.o): In function `_cairo_xlib_surface_finish':
(.text+0x6358): undefined reference to `XRenderFreePicture'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `read_png':
(.text+0x43): undefined reference to `png_create_read_struct'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `read_png':
(.text+0x56): undefined reference to `png_create_info_struct'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `read_png':
(.text+0x74): undefined reference to `png_set_read_fn'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `read_png':
(.text+0xc6): undefined reference to `png_destroy_read_struct'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `read_png':
(.text+0xe6): undefined reference to `png_read_info'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `read_png':
(.text+0x12b): undefined reference to `png_get_IHDR'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `read_png':
(.text+0x165): undefined reference to `png_get_valid'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `read_png':
(.text+0x1c8): undefined reference to `png_set_filler'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `read_png':
(.text+0x1da): undefined reference to `png_read_update_info'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `read_png':
(.text+0x21f): undefined reference to `png_get_IHDR'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `read_png':
(.text+0x287): undefined reference to `png_set_gray_to_rgb'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `read_png':
(.text+0x29f): undefined reference to `png_set_packing'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `read_png':
(.text+0x2b7): undefined reference to `png_set_tRNS_to_alpha'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `read_png':
(.text+0x2cf): undefined reference to `png_set_expand_gray_1_2_4_to_8'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `read_png':
(.text+0x2e7): undefined reference to `png_set_interlace_handling'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `read_png':
(.text+0x2ff): undefined reference to `png_set_palette_to_rgb'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `read_png':
(.text+0x317): undefined reference to `png_set_strip_16'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `read_png':
(.text+0x337): undefined reference to `png_set_read_user_transform_fn'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `read_png':
(.text+0x3f7): undefined reference to `png_read_image'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `read_png':
(.text+0x409): undefined reference to `png_read_end'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `read_png':
(.text+0x43f): undefined reference to `png_set_read_user_transform_fn'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `png_simple_warning_callback':
(.text+0x60e): undefined reference to `png_get_error_ptr'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `png_simple_error_callback':
(.text+0x643): undefined reference to `png_get_error_ptr'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `stream_read_func':
(.text+0x68c): undefined reference to `png_get_io_ptr'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `stream_read_func':
(.text+0x6bc): undefined reference to `png_get_error_ptr'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `stream_write_func':
(.text+0x70c): undefined reference to `png_get_io_ptr'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `stream_write_func':
(.text+0x73c): undefined reference to `png_get_error_ptr'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `stdio_read_func':
(.text+0x826): undefined reference to `png_get_io_ptr'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `stdio_read_func':
(.text+0x879): undefined reference to `png_get_error_ptr'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `stdio_read_func':
(.text+0x895): undefined reference to `png_error'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `write_png':
(.text+0x99f): undefined reference to `png_create_write_struct'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `write_png':
(.text+0x9b2): undefined reference to `png_create_info_struct'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `write_png':
(.text+0x9de): undefined reference to `png_destroy_write_struct'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `write_png':
(.text+0xa5d): undefined reference to `png_set_write_fn'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `write_png':
(.text+0xacd): undefined reference to `png_set_IHDR'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `write_png':
(.text+0xaf6): undefined reference to `png_set_bKGD'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `write_png':
(.text+0xb08): undefined reference to `png_write_info'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `write_png':
(.text+0xb34): undefined reference to `png_write_image'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `write_png':
(.text+0xb46): undefined reference to `png_write_end'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `write_png':
(.text+0xbd4): undefined reference to `png_set_write_user_transform_fn'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `write_png':
(.text+0xbff): undefined reference to `png_set_filler'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `write_png':
(.text+0xc28): undefined reference to `png_set_packswap'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `write_png':
(.text+0xc58): undefined reference to `png_set_write_user_transform_fn'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `stdio_write_func':
(.text+0xda6): undefined reference to `png_get_io_ptr'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `stdio_write_func':
(.text+0xdeb): undefined reference to `png_get_error_ptr'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `stdio_write_func':
(.text+0xe07): undefined reference to `png_error'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `stream_read_func':
(.text+0x6df): undefined reference to `png_error'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-png.o): In function `stream_write_func':
(.text+0x75f): undefined reference to `png_error'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-ft-font.o): In function `_get_bitmap_surface':
(.text+0x882): undefined reference to `pixman_image_set_component_alpha'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-ft-font.o): In function `cairo_ft_scaled_font_unlock_face':
(.text+0xf67): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-ft-font.o): In function `_cairo_ft_unscaled_font_map_lock':
(.text+0xf8f): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-ft-font.o): In function `_cairo_ft_unscaled_font_map_lock':
(.text+0x1003): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-ft-font.o): In function `_cairo_ft_unscaled_font_fini':
(.text+0x10e0): undefined reference to `pthread_mutex_destroy'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-ft-font.o): In function `_cairo_ft_unscaled_font_create_internal':
(.text+0x12d9): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-ft-font.o): In function `_cairo_ft_unscaled_font_create_internal':
(.text+0x1316): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-ft-font.o): In function `_cairo_ft_unscaled_font_create_internal':
(.text+0x1380): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-ft-font.o): In function `_cairo_ft_unscaled_font_destroy':
(.text+0x14fb): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-ft-font.o): In function `_cairo_ft_font_reset_static_data':
(.text+0x1910): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-ft-font.o): In function `_cairo_ft_font_reset_static_data':
(.text+0x19b4): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-ft-font.o): In function `_cairo_ft_unscaled_font_lock_face':
(.text+0x1d00): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-ft-font.o): In function `_cairo_ft_unscaled_font_lock_face':
(.text+0x1d90): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-ft-font.o): In function `_cairo_ft_unscaled_font_lock_face':
(.text+0x1de1): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-ft-font.o): In function `cairo_ft_scaled_font_lock_face':
(.text+0x3de3): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-ft-font.o): In function `_cairo_ft_unscaled_font_unlock_face':
(.text+0xef7): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-paginated-surface.o): In function `_cairo_paginated_surface_show_text_glyphs':
(.text+0x1a7): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-paginated-surface.o): In function `_cairo_paginated_surface_show_text_glyphs':
(.text+0x205): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_display_get_xrender_format':
(.text+0x2f): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_display_get_xrender_format':
(.text+0x48): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_display_get_xrender_format':
(.text+0xb0): undefined reference to `XRenderFindStandardFormat'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_remove_close_display_hook':
(.text+0xec): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_add_close_display_hook':
(.text+0x15c): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_display_notify':
(.text+0x1b2): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_display_notify':
(.text+0x1e1): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_display_notify':
(.text+0x24e): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_display_queue_work':
(.text+0x2a6): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_display_queue_work':
(.text+0x2b9): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_display_queue_resource':
(.text+0x326): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_display_queue_resource':
(.text+0x339): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_display_get':
(.text+0x3df): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_display_get':
(.text+0x445): undefined reference to `XRenderQueryVersion'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_display_get':
(.text+0x44d): undefined reference to `XAddExtension'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_display_get':
(.text+0x46b): undefined reference to `XESetCloseDisplay'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_display_get':
(.text+0x5a3): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_display_destroy':
(.text+0x6bc): undefined reference to `pthread_mutex_destroy'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_close_display':
(.text+0x711): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_close_display':
(.text+0x74a): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_close_display':
(.text+0x763): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_close_display':
(.text+0x776): undefined reference to `XSync'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_close_display':
(.text+0x782): undefined reference to `XSetErrorHandler'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_close_display':
(.text+0x795): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_close_display':
(.text+0x7da): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_close_display':
(.text+0x7ec): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_close_display':
(.text+0x7ff): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_close_display':
(.text+0x807): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_close_display':
(.text+0x819): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_close_display':
(.text+0x84f): undefined reference to `XSync'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_close_display':
(.text+0x85a): undefined reference to `XSetErrorHandler'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_close_display':
(.text+0x866): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_close_display':
(.text+0x8a4): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_close_display':
(.text+0x8da): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_remove_close_display_hook':
(.text+0x129): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_add_close_display_hook':
(.text+0x185): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-display.o): In function `_cairo_xlib_display_notify':
(.text+0x28b): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-screen.o): In function `_cairo_xlib_screen_get_visual_info':
(.text+0x26): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-screen.o): In function `_cairo_xlib_screen_get_visual_info':
(.text+0x79): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-screen.o): In function `_cairo_xlib_screen_get_visual_info':
(.text+0xad): undefined reference to `XScreenNumberOfScreen'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-screen.o): In function `_cairo_xlib_screen_get_visual_info':
(.text+0xd8): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-screen.o): In function `_cairo_xlib_screen_get_visual_info':
(.text+0x152): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-screen.o): In function `_cairo_xlib_screen_get_visual_info':
(.text+0x18f): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-screen.o): In function `_cairo_xlib_screen_put_gc':
(.text+0x20a): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-screen.o): In function `_cairo_xlib_screen_put_gc':
(.text+0x22b): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-screen.o): In function `_cairo_xlib_screen_put_gc':
(.text+0x246): undefined reference to `XFreeGC'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-screen.o): In function `_cairo_xlib_screen_put_gc':
(.text+0x274): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-screen.o): In function `_cairo_xlib_screen_get_gc':
(.text+0x34a): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-screen.o): In function `_cairo_xlib_screen_get_gc':
(.text+0x370): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-screen.o): In function `_cairo_xlib_screen_get_gc':
(.text+0x395): undefined reference to `XSetClipMask'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-screen.o): In function `get_boolean_default':
(.text+0x499): undefined reference to `XGetDefault'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-screen.o): In function `get_integer_default':
(.text+0x56a): undefined reference to `XGetDefault'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-screen.o): In function `_cairo_xlib_screen_info_get':
(.text+0x634): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-screen.o): In function `_cairo_xlib_screen_info_get':
(.text+0x681): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-screen.o): In function `_cairo_xlib_screen_info_get':
(.text+0x758): undefined reference to `XRenderQueryExtension'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-screen.o): In function `_cairo_xlib_screen_info_get':
(.text+0x7ff): undefined reference to `XScreenNumberOfScreen'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-screen.o): In function `_cairo_xlib_screen_info_get':
(.text+0x80b): undefined reference to `XRenderQuerySubpixelOrder'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-screen.o): In function `_cairo_xlib_screen_info_get':
(.text+0x8ef): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-screen.o): In function `_cairo_xlib_screen_info_get':
(.text+0x905): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-screen.o): In function `_cairo_xlib_screen_info_get':
(.text+0x94a): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-screen.o): In function `_cairo_xlib_screen_info_get':
(.text+0x9bb): undefined reference to `XRenderFindVisualFormat'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-screen.o): In function `_cairo_xlib_screen_info_get':
(.text+0xa0c): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-screen.o): In function `_cairo_xlib_screen_info_close_display':
(.text+0xabb): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-screen.o): In function `_cairo_xlib_screen_info_close_display':
(.text+0xad5): undefined reference to `XFreeGC'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-screen.o): In function `_cairo_xlib_screen_info_destroy':
(.text+0xb9a): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-screen.o): In function `_cairo_xlib_screen_info_destroy':
(.text+0xbd1): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-screen.o): In function `_cairo_xlib_screen_info_destroy':
(.text+0xbfa): undefined reference to `pthread_mutex_destroy'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-screen.o): In function `_cairo_xlib_screen_info_close_display':
(.text+0xb4d): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-visual.o): In function `_cairo_xlib_visual_info_create':
(.text+0x131): undefined reference to `XAllocColor'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-visual.o): In function `_cairo_xlib_visual_info_create':
(.text+0x177): undefined reference to `XQueryColors'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-xlib-visual.o): In function `_cairo_xlib_visual_info_create':
(.text+0x424): undefined reference to `XAllocColor'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-user-font.o): In function `_cairo_user_font_face_scaled_font_create':
(.text+0x6ad): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-user-font.o): In function `_cairo_user_font_face_scaled_font_create':
(.text+0x6f6): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libcairo.a(cairo-user-font.o): In function `_cairo_user_font_face_scaled_font_create':
(.text+0x721): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libpango-1.0.a(libpango_thai_lang_la-thai-lang.o): In function `thai_engine_break':
(.text+0x12c): undefined reference to `th_uni2tis'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libpango-1.0.a(libpango_thai_lang_la-thai-lang.o): In function `thai_engine_break':
(.text+0x17b): undefined reference to `th_brk'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libfontconfig.a(fcfreetype.o): In function `FcFreeTypeQueryFace':
(.text+0x2977): undefined reference to `FT_Get_BDF_Property'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libfontconfig.a(fcfreetype.o): In function `FcFreeTypeQueryFace':
(.text+0x2ae5): undefined reference to `FT_Get_BDF_Property'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libfontconfig.a(fcfreetype.o): In function `FcFreeTypeQueryFace':
(.text+0x2b1d): undefined reference to `FT_Get_BDF_Property'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libfontconfig.a(fcfreetype.o): In function `FcFreeTypeQueryFace':
(.text+0x2bb0): undefined reference to `FT_Get_BDF_Property'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libfontconfig.a(fcfreetype.o): In function `FcFreeTypeQueryFace':
(.text+0x2bda): undefined reference to `FT_Get_BDF_Property'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libfontconfig.a(fcfreetype.o): In function `FcFreeTypeQueryFace':
(.text+0x2e24): undefined reference to `FT_Get_X11_Font_Format'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libfontconfig.a(fcfreetype.o): In function `FcFreeTypeQueryFace':
(.text+0x2ec0): undefined reference to `FT_Get_BDF_Property'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libfontconfig.a(fcxml.o): In function `FcConfigMessage':
(.text+0xe4): undefined reference to `XML_GetCurrentLineNumber'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libfontconfig.a(fcxml.o): In function `FcConfigMessage':
(.text+0x187): undefined reference to `XML_GetCurrentLineNumber'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libfontconfig.a(fcxml.o): In function `FcConfigParseAndLoad':
(.text+0x118f): undefined reference to `XML_ParserCreate'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libfontconfig.a(fcxml.o): In function `FcConfigParseAndLoad':
(.text+0x11d9): undefined reference to `XML_SetUserData'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libfontconfig.a(fcxml.o): In function `FcConfigParseAndLoad':
(.text+0x11f1): undefined reference to `XML_SetDoctypeDeclHandler'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libfontconfig.a(fcxml.o): In function `FcConfigParseAndLoad':
(.text+0x1209): undefined reference to `XML_SetElementHandler'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libfontconfig.a(fcxml.o): In function `FcConfigParseAndLoad':
(.text+0x1219): undefined reference to `XML_SetCharacterDataHandler'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libfontconfig.a(fcxml.o): In function `FcConfigParseAndLoad':
(.text+0x122c): undefined reference to `XML_GetBuffer'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libfontconfig.a(fcxml.o): In function `FcConfigParseAndLoad':
(.text+0x126c): undefined reference to `XML_ParseBuffer'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libfontconfig.a(fcxml.o): In function `FcConfigParseAndLoad':
(.text+0x12a0): undefined reference to `XML_ParserFree'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libfontconfig.a(fcxml.o): In function `FcConfigParseAndLoad':
(.text+0x15a9): undefined reference to `XML_GetErrorCode'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libfontconfig.a(fcxml.o): In function `FcConfigParseAndLoad':
(.text+0x15b1): undefined reference to `XML_ErrorString'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgmodule-2.0.a(gmodule.o): In function `g_module_symbol':
(.text+0x2eb): undefined reference to `dlerror'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgmodule-2.0.a(gmodule.o): In function `g_module_symbol':
(.text+0x2fa): undefined reference to `dlsym'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgmodule-2.0.a(gmodule.o): In function `g_module_symbol':
(.text+0x301): undefined reference to `dlerror'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgmodule-2.0.a(gmodule.o): In function `_g_module_close':
(.text+0x44a): undefined reference to `dlclose'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgmodule-2.0.a(gmodule.o): In function `_g_module_close':
(.text+0x461): undefined reference to `dlerror'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgmodule-2.0.a(gmodule.o): In function `g_module_open':
(.text+0x7b9): undefined reference to `dlopen'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgmodule-2.0.a(gmodule.o): In function `g_module_open':
(.text+0xd34): undefined reference to `dlopen'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgmodule-2.0.a(gmodule.o): In function `g_module_open':
(.text+0xdc3): undefined reference to `dlerror'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libgmodule-2.0.a(gmodule.o): In function `g_module_open':
(.text+0xeb1): undefined reference to `dlerror'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libglib-2.0.a(gregex.o): In function `g_regex_get_string_number':
(.text+0x3af): undefined reference to `pcre_get_stringnumber'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libglib-2.0.a(gregex.o): In function `g_regex_get_capture_count':
(.text+0x446): undefined reference to `pcre_fullinfo'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libglib-2.0.a(gregex.o): In function `g_regex_get_max_backref':
(.text+0x476): undefined reference to `pcre_fullinfo'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libglib-2.0.a(gregex.o): In function `g_regex_unref':
(.text+0x787): undefined reference to `pcre_free'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libglib-2.0.a(gregex.o): In function `g_regex_unref':
(.text+0x797): undefined reference to `pcre_free'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libglib-2.0.a(gregex.o): In function `match_info_new':
(.text+0x8e0): undefined reference to `pcre_fullinfo'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libglib-2.0.a(gregex.o): In function `g_regex_match_all_full':
(.text+0x1138): undefined reference to `pcre_dfa_exec'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libglib-2.0.a(gregex.o): In function `g_regex_new':
(.text+0x1380): undefined reference to `pcre_compile2'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libglib-2.0.a(gregex.o): In function `g_regex_new':
(.text+0x13a9): undefined reference to `pcre_fullinfo'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libglib-2.0.a(gregex.o): In function `g_regex_new':
(.text+0x140d): undefined reference to `pcre_study'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libglib-2.0.a(gregex.o): In function `g_regex_new':
(.text+0x14df): undefined reference to `pcre_config'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libglib-2.0.a(gregex.o): In function `g_regex_new':
(.text+0x14f6): undefined reference to `pcre_config'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libglib-2.0.a(gregex.o): In function `g_regex_new':
(.text+0x153a): undefined reference to `pcre_fullinfo'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libglib-2.0.a(gregex.o): In function `get_matched_substring_number':
(.text+0x1b20): undefined reference to `pcre_get_stringtable_entries'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libglib-2.0.a(gregex.o): In function `get_matched_substring_number':
(.text+0x1b9b): undefined reference to `pcre_get_stringnumber'
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/libglib-2.0.a(gregex.o): In function `g_match_info_next':
(.text+0x20a5): undefined reference to `pcre_exec'
/usr/lib/gcc/i486-linux-gnu/4.3.2/libstdc++.a(locale.o): In function `__gnu_cxx::__scoped_lock::~__scoped_lock()':
(.text._ZN9__gnu_cxx13__scoped_lockD1Ev[__gnu_cxx::__scoped_lock::~__scoped_lock()]+0x18): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/libstdc++.a(locale.o): In function `std::locale::_Impl::_M_install_cache(std::locale::facet const*, unsigned int)':
(.text._ZNSt6locale5_Impl16_M_install_cacheEPKNS_5facetEj+0x2d): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/libstdc++.a(locale.o): In function `std::locale::_Impl::_M_install_cache(std::locale::facet const*, unsigned int)':
(.text._ZNSt6locale5_Impl16_M_install_cacheEPKNS_5facetEj+0x59): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/libstdc++.a(locale_init.o): In function `std::locale::locale()':
(.text._ZNSt6localeC1Ev+0x2a): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/libstdc++.a(locale_init.o): In function `std::locale::locale()':
(.text._ZNSt6localeC1Ev+0x46): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/libstdc++.a(locale_init.o): In function `std::locale::global(std::locale const&)':
(.text._ZNSt6locale6globalERKS_+0x2a): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/libstdc++.a(locale_init.o): In function `std::locale::global(std::locale const&)':
(.text._ZNSt6locale6globalERKS_+0x8e): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/libstdc++.a(locale_init.o): In function `std::locale::locale()':
(.text._ZNSt6localeC2Ev+0x2a): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/libstdc++.a(locale_init.o): In function `std::locale::locale()':
(.text._ZNSt6localeC2Ev+0x46): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/libstdc++.a(eh_alloc.o): In function `__cxa_free_exception':
(.text.__cxa_free_exception+0x6b): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/libstdc++.a(eh_alloc.o): In function `__cxa_free_exception':
(.text.__cxa_free_exception+0x86): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/libstdc++.a(eh_alloc.o): In function `__cxa_allocate_exception':
(.text.__cxa_allocate_exception+0x6f): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/libstdc++.a(eh_alloc.o): In function `__cxa_allocate_exception':
(.text.__cxa_allocate_exception+0xd7): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/libgcc_eh.a(unwind-dw2-fde-glibc.o): In function `__register_frame_info_bases':
(.text+0x60): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/libgcc_eh.a(unwind-dw2-fde-glibc.o): In function `__register_frame_info_bases':
(.text+0x77): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/libgcc_eh.a(unwind-dw2-fde-glibc.o): In function `__register_frame_info_table_bases':
(.text+0x12a): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/libgcc_eh.a(unwind-dw2-fde-glibc.o): In function `__register_frame_info_table_bases':
(.text+0x141): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/libgcc_eh.a(unwind-dw2-fde-glibc.o): In function `_Unwind_Find_FDE':
(.text+0x1858): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/libgcc_eh.a(unwind-dw2-fde-glibc.o): In function `_Unwind_Find_FDE':
(.text+0x18a8): undefined reference to `pthread_mutex_unlock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/libgcc_eh.a(unwind-dw2-fde-glibc.o): In function `__deregister_frame_info_bases':
(.text+0x1a5a): undefined reference to `pthread_mutex_lock'
/usr/lib/gcc/i486-linux-gnu/4.3.2/libgcc_eh.a(unwind-dw2-fde-glibc.o): In function `__deregister_frame_info_bases':
(.text+0x1adf): undefined reference to `pthread_mutex_unlock'
collect2: ld returned 1 exit status

```


I don't want to static link gtk, just gtkmm. Is this impossible?

---

### Post by monkeyking on 2009-01-11
Try using 
ar with the rcs argument look here 
[http://tldp.org/HOWTO/Program-Library-HOWTO/static-libraries.html](http://tldp.org/HOWTO/Program-Library-HOWTO/static-libraries.html)

But why do you want to do static linking?

---

### Post by Emill on 2009-01-11
I do not want to static link gtk, just gtkmm. In the error messages, I only see gtk "undefined references", no gtkmm-ones.
When I add "-static", the compiler doesn't want to use any shared library at all.

---

### Post by SledgeHammer_999 on 2009-01-11
After giving the "pkg-config gtkmm-2.4 --cflags --libs" command in a terminal I see that it provides info to BOTH gtkmm AND gtk. Maybe you could try to provide the info about gtkmm BEFORE the "-static" switch and the info about gtk AFTER "-static".

---

### Post by SledgeHammer_999 on 2009-01-11
Finally I found an answer!!!
Take this code for example:
```

#include <gtkmm/button.h>
#include <gtkmm/window.h>
#include <gtkmm/main.h>
#include <iostream>

class HelloWorld : public Gtk::Window
{

public:
  HelloWorld();
  virtual ~HelloWorld();

protected:
  //Signal handlers:
  virtual void on_button_clicked();

  //Member widgets:
  Gtk::Button m_button;
};

int main (int argc, char *argv[])
{
  Gtk::Main kit(argc, argv);

  HelloWorld helloworld;
  //Shows the window and returns when it is closed.
  Gtk::Main::run(helloworld);

  return 0;
}



HelloWorld::HelloWorld()
: m_button("Hello World")   // creates a new button with label "Hello World".
{
  // Sets the border width of the window.
  set_border_width(10);

  // When the button receives the "clicked" signal, it will call the
  // on_button_clicked() method defined below.
  m_button.signal_clicked().connect(sigc::mem_fun(*this,
              &HelloWorld::on_button_clicked));

  // This packs the button into the Window (a container).
  add(m_button);

  // The final step is to display this newly created widget...
  m_button.show();
}

HelloWorld::~HelloWorld()
{
}

void HelloWorld::on_button_clicked()
{
  std::cout << "Hello World" << std::endl;
}
```

Compile it with:
```
 g++ hello.cpp -o hello -Wl,-Bstatic -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -lgtkmm-2.4 -Wl,-Bdynamic  -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/cairomm-1.0 -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/atk-1.0  -lgiomm-2.4 -lgdkmm-2.4 -latkmm-1.6 -lgtk-x11-2.0 -lpangomm-1.4 -lcairomm-1.0 -lglibmm-2.4 -lsigc-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lz -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lglib-2.0
```

Explanation:
In this example only gtkmm is statically linked. All others are dynamically linked(including pangomm).
How to do it:
1. You need to pass to ld(the linker) the correct switch about static or dynamic linkage. For static the switches are "-Bstatic/-dn/-non_shared/-static". For dynamic the switches are "-Bdynamic/-dy/-call_shared"
2. Use the "-Wl" switch to pass arguments to ld from gcc/g++. 
3. Be carefull you need a comma(,) after -Wl. Example -Wl,-static(no space between the comma and the ld switch).

Have fun now.

---

### Post by PandaGoat on 2009-01-11
Do you use intrepid ibex?  I installed libgtkmm-2.4-dev, which installed all other dependencies, and successfully compiled a test file with "g++ `pkg-config gtkmm-2.4 --cflags --libs` test.c -o test".

---

### Post by Emill on 2009-01-11
Thank you very much!
The options
-Wl,-Bstatic -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -lgtkmm-2.4 -Wl,-Bdynamic  -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/cairomm-1.0 -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/atk-1.0  -lgiomm-2.4 -lgdkmm-2.4 -latkmm-1.6 -lgtk-x11-2.0 -lpangomm-1.4 -lcairomm-1.0 -lglibmm-2.4 -lsigc-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lz -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lglib-2.0
works very nice!

---

### Post by SledgeHammer_999 on 2009-01-11
> **Emill said:**
> Thank you very much!
The options
-Wl,-Bstatic -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -lgtkmm-2.4 -Wl,-Bdynamic  -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/cairomm-1.0 -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/atk-1.0  -lgiomm-2.4 -lgdkmm-2.4 -latkmm-1.6 -lgtk-x11-2.0 -lpangomm-1.4 -lcairomm-1.0 -lglibmm-2.4 -lsigc-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lz -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lglib-2.0
works very nice!

Keep in mind that many libraries(like pangomm/glibmm) aren't statically linked in my example. You choose which ones you want.


[quote=PandaGoat]
Do you use intrepid ibex? I installed libgtkmm-2.4-dev, which installed all other dependencies, and successfully compiled a test file with "g++ `pkg-config gtkmm-2.4 --cflags --libs` test.c -o test".[/quote]
Yes, intrepid. You are linking with gtkmm(and related libraries) dynamically. Emill wants static linkage.

---

