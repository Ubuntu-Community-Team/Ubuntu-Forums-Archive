---
title: "Issue with nautilus"
date: 2015-12-14
forum: New to Ubuntu
---

### Post by alessandro32 on 2015-12-14
Hey,
I have just installed the last version of Ubuntu.
If I digit nautilus on terminal, I obtain this message:

(nautilus:2084): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(nautilus:2084): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(nautilus:2084): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

Can I know what is the problem?

Another question: if I search the item var/log in file system, no result. But if I search only var, this folder is founded.

Thanks!

---

### Post by Bucky Ball on 2015-12-14
Welcome. Generally there the terminal will show some kind of error when you launch most things from it. Does Nautilus launch and run fine? If so, wouldn't worry about the terminal messages. What command are you using to launch Nautilus? Just 'nautilus'?

You search for /var/log. Not var/log. You don't need to search to far. In your root directory. :)

---

