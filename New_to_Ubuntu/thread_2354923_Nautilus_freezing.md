---
title: "Nautilus freezing"
date: 2017-03-07
forum: New to Ubuntu
---

### Post by lysander6662 on 2017-03-07
My second thread of the day, sorry. For the second [or maybe third] time Nautilus isn't working. I click on the Files icon and it just hangs. Logging off and back on solves it but I'd rather have something longer term. Any ideas what to do about this or what could be causing it?

---

### Post by howefield on 2017-03-08
Don't be sorry for posting questions :)

Does the file manager manager open when you right click the icon and select an option from there ?

---

### Post by lysander6662 on 2017-03-08
I think I tried that yesterday and that came up with nothing either... from what I can remember anyway.

---

### Post by vanadium on 2017-03-08
Mention the version of your OS and nautilus. Try starting nautilus from the command line, with the command "nautilus". Error messages that may appear there may provide some clue on what is going wrong.
Try logging in to a guest account (or create a new temporary account). Does the problem happen there? If not, then it is an issue with your user configuration.

---

### Post by lysander6662 on 2017-03-08
> **vanadium said:**
> Mention the version of your OS and nautilus. Try starting nautilus from the command line, with the command "nautilus". Error messages that may appear there may provide some clue on what is going wrong.
Try logging in to a guest account (or create a new temporary account). Does the problem happen there? If not, then it is an issue with your user configuration. 

Interesting. This is the output from the guest account:

```
guest-jhqqyt@psychopig-xxiii:~$ nautilus

(nautilus:24192): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed


(nautilus:24192): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed



```

And from my account:

```
lysander@psychopig-xxiii:~$ nautilus

(nautilus:23095): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed


(nautilus:23095): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed


(nautilus:23095): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed


(nautilus:23095): GLib-GObject-WARNING **: invalid (NULL) pointer instance


(nautilus:23095): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed
```

EDIT: It's a bug with Nautilus. 

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1569970](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1569970)

Upgrading the package didn't do anything.

This is the temporary solution

```
sudo killall nautilus && setsid nautilus
```

This also didn't work for me, same error afterwards:

[https://ubuntuforums.org/showthread.php?t=2319175&p=13464670#post13464670](https://ubuntuforums.org/showthread.php?t=2319175&p=13464670#post13464670)

---

### Post by lysander6662 on 2017-03-10
I'm going to mark this as solved since I don't think it's going to go any further, and I imagine we will just have to wait for this to be resolved by Canonical going forward.

---

