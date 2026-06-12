---
title: "Problem updating/running dropbox"
date: 2018-11-20
forum: New to Ubuntu
---

### Post by don-guliano on 2018-11-20
HI!

I was affected by the known end of filesystem-diversity-support of dropbox recently. BUT: I have it installed in an Ext4-Partition, so it should acutally work. 
I re-installed the client after deleting the ".dropbox" und ".dropbox-dist" - folders. 
I used this commands: 
cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86_64" | tar xzf -
and 
~/.dropbox-dist/dropboxd

From the Dropbox-Install-Site. 
Then I get the following output: 
```
(nautilus:4743): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed

(nautilus:4743): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed

(nautilus:4743): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(nautilus:4743): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(nautilus:4743): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

```

When i close the terminal window, the dropbox icon in the system tray disappears and dropbox stops working.
Can anyone help me?

Edit: running on an ubuntu 16.04 lts, all updates installed

---

