---
title: "Nautilus-actions not showing after reinstall"
date: 2018-04-19
forum: New to Ubuntu
---

### Post by ghdez on 2018-04-19
I had Nautilus actions installed and configured with some custom  actions, but due to some problems with the file explorer I had to  compile Nautilus and install it again (version 3.14) now my custom  actions disappeared but they still appear in the Nautilus actions  configuration tool, I'm also missing the "open terminal", restore  files", "Extract Here" buttons from right click menu in the file explorer. I managed to  get back some of those with sudo apt-get install nautilus-open-terminal but I'm still missing the Nautilus-actions button.  How can I restore this? I tried uninstalling and purging nautilus  actions, then rebooting and reinstalling but no luck, also I tried  deleting the actions in the config tool and adding some new ones but  that doesn't work either.


  I'm using Ubuntu 16.04


  Also when I click the home button to open the file explorer all the desktop icons disappear


EDIT: Also If I run nautilus --no-desktop &  on startup, I get this:

(nautilus:2227): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed

(nautilus:2227): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed

(nautilus:2227): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(nautilus:2227): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(nautilus:2227): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

---

### Post by logix2 on 2018-04-20
If you compiled Nautilus, you may need to also build some of its extensions or else they won't work (and if you had some extensions installed, you may need to remove them or else they may affect Nautilus, that's why you're probably encountering errors). That's because some extensions need to be compiled against your specific Nautilus version.

---

### Post by ghdez on 2018-04-20
Is there a way to list my installed nautilus extensions so I can compile them again one by one?

---

### Post by logix2 on 2018-04-26
Nautilus doesn't list installed extensions itself, as far as I know (Nemo does). You could search for "nautilus extension" in Synaptic and see which extensions are installed from the Ubuntu repositories.

---

