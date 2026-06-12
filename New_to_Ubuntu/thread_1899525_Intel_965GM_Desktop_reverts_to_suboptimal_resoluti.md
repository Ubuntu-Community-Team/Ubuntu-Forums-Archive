---
title: "Intel 965GM: Desktop reverts to suboptimal resolution after login"
date: 2011-12-23
forum: New to Ubuntu
---

### Post by user250876 on 2011-12-23
Greetings,

This is similar to threads regarding a similar problem with NVidia drivers. However, I have an Intel 965 GM chipset that was working well till a problem with Oneiric's bluetooth module made Xserver crash.

Since then after login, which happens at the optimal 1280x800 for my laptop, the screen goes black and restarts desktop at 1024x768.

I can manually change the resolution back to 1280x800 through system preferences etc. The settings aren't saving. The problem's been back at the next 4 reboots. /etc/x11 doesn't have xorg.conf. 

I had compiz installed, which I have "apt-get purge" since then, to no avail.

Any suggestions? Thanks in advance, folks.

oneiric 11.10 on Intel/AMD64 without VT.

---

### Post by Mahkoe on 2011-12-23
Open the screen resolution dialog, set your resolution, then hit "Make Default" and enter your sudo password (normally the one you use to log in).

---

### Post by user250876 on 2011-12-24
> **Mahkoe said:**
> Open the screen resolution dialog, set your resolution, then hit "Make Default" and enter your sudo password (normally the one you use to log in).

Thank you, but I can't find an apparent "Make Default" button on the Screen Resolution dialogue. Is a screenshot available?

Cheers,

---

### Post by user250876 on 2011-12-24
This from my /home/"user"/.xsession-errors:

```
compiz (core) - Warn: no exact match for ConfigureNotify on 0x180012c!
compiz (core) - Warn: expected the following changes:
compiz (core) - Warn: sibling: 0x43ee95
compiz (core) - Warn: instead got:
compiz (core) - Warn: x: 0
compiz (core) - Warn: y: 0
compiz (core) - Warn: width: 1024
compiz (core) - Warn: height: 768
compiz (core) - Warn: above: 0
**compiz (core) - Warn: this should never happen. you should probably file a bug about this.**
```

this is part of:

```
Screen geometry changed:
   0x0x1280x800

unity-panel-service: no process found
Initializing unityshell options...done
DEBUG 2011-12-24 09:12:14 glib <unknown>:0 Setting to primary screen rect: x=0 y=0 w=1280 h=800
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


Screen geometry changed:
   0x0x1024x768


(jupiter:22961): Gdk-CRITICAL **: IA__gdk_window_thaw_toplevel_updates_libgtk_only: assertion `private->update_and_descendants_freeze_count > 0' failed
WARN  2011-12-24 09:12:14 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/files does not exist
WARN  2011-12-24 09:12:14 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/files does not exist
WARN  2011-12-24 09:12:15 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/music does not exist
WARN  2011-12-24 09:12:15 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/music does not exist
** Message: moving back from GtkStatusIcon to indicator
WARN  2011-12-24 09:12:16 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/applications does not exist
WARN  2011-12-24 09:12:16 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/applications does not exist
WARN  2011-12-24 09:12:16 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/commands does not exist
WARN  2011-12-24 09:12:16 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/commands does not exist
WARN  2011-12-24 09:12:17 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-installed.svg: Error opening file: No such file or directory
WARN  2011-12-24 09:12:17 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-available.svg: Error opening file: No such file or directory
Setting Update "texture_filter"
Setting Update "lighting"
Setting Update "command"
Setting Update "flip_left_edge"
Setting Update "directory"
Setting Update "main_menu_key"
Setting Update "run_key"
Setting Update "backlight_mode"
Setting Update "launch_animation"
Setting Update "panel_opacity"
Setting Update "launcher_opacity"
Setting Update "icon_size"

** (process:23370): WARNING **: zeitgeist-datahub.vala:218: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
/usr/lib/python2.7/dist-packages/gobject/constants.py:24: Warning: g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
  import gobject._gobject
** (nautilus:22941): DEBUG: Got notification of SyncDaemon startup in NameOwnerChanged
compiz (core) - Warn: no exact match for ConfigureNotify on 0x180012c!
compiz (core) - Warn: expected the following changes:
compiz (core) - Warn: sibling: 0x43ee95
compiz (core) - Warn: instead got:
compiz (core) - Warn: x: 0
compiz (core) - Warn: y: 0
compiz (core) - Warn: width: 1024
compiz (core) - Warn: height: 768
compiz (core) - Warn: above: 0
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
```

Should I file an official bug report?

---

### Post by fuduntu on 2011-12-24
It looks like you have Jupiter installed, you probably told Jupiter to set it to 1024x768 and then forgot that you did it.  Change it in Jupiter to the optimal resolution.

---

