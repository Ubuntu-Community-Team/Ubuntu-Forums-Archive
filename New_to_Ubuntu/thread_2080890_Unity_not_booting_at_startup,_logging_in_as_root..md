---
title: "Unity not booting at startup, logging in as root."
date: 2012-11-05
forum: New to Ubuntu
---

### Post by xelab1090 on 2012-11-05
Alright, this happened to me yesterday. Ubuntu 12.10. Everything was fine since install, nothing special. Then all of a sudden, bam. No unity at launch. So I opened a terminal and typed in "unity", I get this in terminal:
```

root@ubuntu-is-algebraic:~# unity
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : default
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (core) - Info: Starting plugin: opengl
NVIDIA: API mismatch: the NVIDIA kernel module has version 304.51,
but this NVIDIA driver component has version 304.43.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (expo) - Warn: failed to bind image to texture
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
Error:  
 COMPILE 
Error: &#65533;&#65533;`&#65533; 
 COMPILE 
Error: &#65533;&#65533;`&#65533; 
 COMPILE 
WARN  2012-11-05 07:55:11 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/chromium-browser.desktop' is using a deprecated format for its actions that will be dropped soon.
ERROR 2012-11-05 07:55:11 unity.launcher.trashlaunchericon TrashLauncherIcon.cpp:61 Could not create file monitor for trash uri: Operation not supported
Error: &#65533;&#65533;&#65533; 
 COMPILE 
Error: @e&#65533; 
 COMPILE 
WARN  2012-11-05 07:55:12 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window18874444
WARN  2012-11-05 07:55:12 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window18874444
WARN  2012-11-05 07:55:12 unity.glib-gio <unknown>:0 g_settings_set_value: value for key 'visual-bell-type' in schema 'org.gnome.desktop.wm.preferences' is outside of valid range
ERROR 2012-11-05 07:55:12 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.drag.threshold
ERROR 2012-11-05 07:55:12 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.drag.timeout
ERROR 2012-11-05 07:55:12 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.pinch.threshold
ERROR 2012-11-05 07:55:12 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.pinch.timeout
ERROR 2012-11-05 07:55:12 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.tap.threshold
ERROR 2012-11-05 07:55:12 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.tap.timeout
ERROR 2012-11-05 07:55:12 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.rotate.threshold
ERROR 2012-11-05 07:55:12 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.rotate.timeout
ERROR 2012-11-05 07:55:12 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.drag.threshold
ERROR 2012-11-05 07:55:12 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.drag.timeout
ERROR 2012-11-05 07:55:12 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.pinch.threshold
ERROR 2012-11-05 07:55:12 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.pinch.timeout
ERROR 2012-11-05 07:55:12 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.tap.threshold
ERROR 2012-11-05 07:55:12 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.tap.timeout
ERROR 2012-11-05 07:55:12 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.rotate.threshold
ERROR 2012-11-05 07:55:12 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.rotate.timeout
ERROR 2012-11-05 07:55:12 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.drag.threshold
ERROR 2012-11-05 07:55:12 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.drag.timeout
ERROR 2012-11-05 07:55:12 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.pinch.threshold
ERROR 2012-11-05 07:55:12 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.pinch.timeout
ERROR 2012-11-05 07:55:12 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.tap.threshold
ERROR 2012-11-05 07:55:12 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.tap.timeout
ERROR 2012-11-05 07:55:12 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.rotate.threshold
ERROR 2012-11-05 07:55:12 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.rotate.timeout
WARN  2012-11-05 07:55:12 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window18874444
WARN  2012-11-05 07:55:12 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window18874444
WARN  2012-11-05 07:55:12 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window18874444
WARN  2012-11-05 07:55:12 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window18874444
WARN  2012-11-05 07:55:12 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window18874444
WARN  2012-11-05 07:55:12 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window18874444
WARN  2012-11-05 07:55:12 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window18874444
^Croot@ubuntu-is-algebraic:~# compiz (core) - Info: Stopping plugin: unityshell

(compiz:16772): GLib-CRITICAL **: g_hash_table_remove_internal: assertion `hash_table != NULL' failed

(compiz:16772): GLib-CRITICAL **: g_hash_table_remove_internal: assertion `hash_table != NULL' failed

(compiz:16772): GLib-CRITICAL **: g_hash_table_remove_internal: assertion `hash_table != NULL' failed

(compiz:16772): GLib-CRITICAL **: g_hash_table_remove_internal: assertion `hash_table != NULL' failed

(compiz:16772): GLib-CRITICAL **: g_hash_table_remove_internal: assertion `hash_table != NULL' failed

(compiz:16772): GLib-CRITICAL **: g_hash_table_remove_internal: assertion `hash_table != NULL' failed

(compiz:16772): GLib-CRITICAL **: g_hash_table_remove_internal: assertion `hash_table != NULL' failed

(compiz:16772): GLib-CRITICAL **: g_hash_table_remove_internal: assertion `hash_table != NULL' failed

(compiz:16772): GLib-CRITICAL **: g_hash_table_remove_internal: assertion `hash_table != NULL' failed

(compiz:16772): GLib-CRITICAL **: g_hash_table_remove_internal: assertion `hash_table != NULL' failed

(compiz:16772): GLib-CRITICAL **: g_hash_table_remove_internal: assertion `hash_table != NULL' failed

(compiz:16772): GLib-CRITICAL **: g_hash_table_remove_internal: assertion `hash_table != NULL' failed

(compiz:16772): GLib-CRITICAL **: g_hash_table_remove_internal: assertion `hash_table != NULL' failed

(compiz:16772): GLib-CRITICAL **: g_hash_table_remove_internal: assertion `hash_table != NULL' failed

(compiz:16772): GLib-CRITICAL **: g_hash_table_remove_internal: assertion `hash_table != NULL' failed

(compiz:16772): GLib-CRITICAL **: g_hash_table_remove_internal: assertion `hash_table != NULL' failed

(compiz:16772): GLib-CRITICAL **: g_hash_table_remove_internal: assertion `hash_table != NULL' failed

(compiz:16772): GLib-CRITICAL **: g_hash_table_remove_internal: assertion `hash_table != NULL' failed

(compiz:16772): GLib-CRITICAL **: g_hash_table_remove_internal: assertion `hash_table != NULL' failed

(compiz:16772): GLib-CRITICAL **: g_hash_table_remove_internal: assertion `hash_table != NULL' failed

(compiz:16772): GLib-CRITICAL **: g_hash_table_remove_internal: assertion `hash_table != NULL' failed

(compiz:16772): GLib-CRITICAL **: g_hash_table_remove_internal: assertion `hash_table != NULL' failed

(compiz:16772): GLib-CRITICAL **: g_hash_table_remove_internal: assertion `hash_table != NULL' failed

(compiz:16772): GLib-CRITICAL **: g_hash_table_remove_internal: assertion `hash_table != NULL' failed
compiz (core) - Info: Unloading plugin: unityshell
compiz (core) - Info: Stopping plugin: ezoom
compiz (core) - Info: Unloading plugin: ezoom
compiz (core) - Info: Stopping plugin: expo
compiz (core) - Info: Unloading plugin: expo
compiz (core) - Info: Stopping plugin: scale
compiz (core) - Info: Unloading plugin: scale
compiz (core) - Info: Stopping plugin: workarounds
compiz (core) - Info: Unloading plugin: workarounds
compiz (core) - Info: Stopping plugin: unitymtgrabhandles
compiz (core) - Info: Unloading plugin: unitymtgrabhandles
compiz (core) - Info: Stopping plugin: fade
compiz (core) - Info: Unloading plugin: fade
compiz (core) - Info: Stopping plugin: animation
compiz (core) - Info: Unloading plugin: animation
compiz (core) - Info: Stopping plugin: gnomecompat
compiz (core) - Info: Unloading plugin: gnomecompat
compiz (core) - Info: Stopping plugin: session
compiz (core) - Info: Unloading plugin: session
compiz (core) - Info: Stopping plugin: imgpng
compiz (core) - Info: Unloading plugin: imgpng
compiz (core) - Info: Stopping plugin: regex
compiz (core) - Info: Unloading plugin: regex
compiz (core) - Info: Stopping plugin: grid
compiz (core) - Info: Unloading plugin: grid
compiz (core) - Info: Stopping plugin: wall
compiz (core) - Info: Unloading plugin: wall
compiz (core) - Info: Stopping plugin: move
compiz (core) - Info: Unloading plugin: move
compiz (core) - Info: Stopping plugin: place
compiz (core) - Info: Unloading plugin: place
compiz (core) - Info: Stopping plugin: resize
compiz (core) - Info: Unloading plugin: resize
compiz (core) - Info: Stopping plugin: mousepoll
compiz (core) - Info: Unloading plugin: mousepoll
compiz (core) - Info: Stopping plugin: snap
compiz (core) - Info: Unloading plugin: snap
compiz (core) - Info: Stopping plugin: vpswitch
compiz (core) - Info: Unloading plugin: vpswitch
compiz (core) - Info: Stopping plugin: decor
compiz (core) - Info: Unloading plugin: decor
compiz (core) - Info: Stopping plugin: compiztoolbox
compiz (core) - Info: Unloading plugin: compiztoolbox
compiz (core) - Info: Stopping plugin: opengl
compiz (core) - Info: Unloading plugin: opengl
compiz (core) - Info: Stopping plugin: composite
compiz (core) - Info: Unloading plugin: composite
compiz (core) - Info: Stopping plugin: ccp
compiz (core) - Info: Unloading plugin: ccp
compiz (core) - Info: Stopping plugin: core
compiz (core) - Info: Unloading plugin: core

(compiz:16772): GLib-WARNING **: /build/buildd/glib2.0-2.34.0/./glib/gmain.c:1817: ref_count == 0, but source was still attached to a context!
```

So, not only am I logging in as root by default now, but Unity will not boot and gives me tons of errors. Any help?

---

### Post by Gone fishing on 2012-11-05
I think the problem is the nvidia driver I found this

> 
sudo apt-get purge nvidia*

then after the process was complete...

sudo apt-get install nvidia-current-updates-dev

and then, after this process was complete I rebooted and everything worked perfectly!

I would suggest from a terminal running ```
sudo apt-get purge nvidia*
``` rebooting and you should get into Unity and the either ```
 sudo apt-get install nvidia-current-updates-dev
``` or reinstalling the Nvidia driver via the drivers tool

---

### Post by philinux on 2012-11-05
Something weird if you suddenly logging in as root. What did you do?

(Also I added code tags to your first post. Thats the # option in post edit mode. Highlight text and hit the # button.)

---

### Post by Gone fishing on 2012-11-05
> Something weird if you suddenly logging in as root. What did you do?

I thought that wierd too you would expect to be dropped out at a login prompt if Unity crashes - maybe this is occuring as the system crashes after completing init 1?

---

### Post by xelab1090 on 2012-11-13
I did 

```
unity
```

 in terminal, nothing happens, I do ```
sudo unity
```
, type in my password and unity boots, but now instead of my login at the beginning of terminal it says "root@"....so yeah..

---

### Post by philinux on 2012-11-13
xelab,

Login to ubuntu as normal. Open a terminal ctrl + Alt +t.

And follow this. [http://ubuntuguide.net/how-to-reset-unity-in-ubuntu-12-10-quantal](http://ubuntuguide.net/how-to-reset-unity-in-ubuntu-12-10-quantal)

---

### Post by audiomick on 2012-11-13
> **philinux said:**
> Something weird if you suddenly logging in as root. What did you do?

Could it be that the OP is landing in the recovery mode? That is root user, isn't it?

---

### Post by fslezak on 2012-11-13
Try to reinstall Unity.

Or go back to 10.04 and Grub2!

---

### Post by snowpine on 2012-11-13
Welcome to Linux, where error messages are actually useful/informative!

```
NVIDIA: API mismatch: the NVIDIA kernel module has version 304.51,
but this NVIDIA driver component has version 304.43.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
```

Googling this error I found many answers such as the following:

[http://askubuntu.com/questions/145195/nvidia-driver-problem-after-updating-to-12-04](http://askubuntu.com/questions/145195/nvidia-driver-problem-after-updating-to-12-04)
[http://askubuntu.com/questions/37590/nvidia-drivers-not-working-after-upgrade-why-can-i-only-see-terminal](http://askubuntu.com/questions/37590/nvidia-drivers-not-working-after-upgrade-why-can-i-only-see-terminal)

DISCLAIMER: I am not a Nvidia user! I have no idea if these fixes will actually work, just trying to steer you in the right direction.

Also it goes without saying that logging in as root can cause all sorts of permissions problems and really is not recommended on these forums. Here are instructions to lock the root account and revert to default Ubuntu security settings: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

