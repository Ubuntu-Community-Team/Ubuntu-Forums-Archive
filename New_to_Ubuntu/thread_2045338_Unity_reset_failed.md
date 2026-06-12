---
title: "Unity reset failed"
date: 2012-08-21
forum: New to Ubuntu
---

### Post by MibunoOokami on 2012-08-21
Hi everyone. My wife also uses Ubuntu 12.04, about a week ago her applications disappeared from dash. I finally got around to searching for solutions online today since rebooting didn't work. I tried this command 
```
unity --reset &
``` from this thread first.
[http://askubuntu.com/questions/69456/no-programs-or-applications-show-up-in-dash](http://askubuntu.com/questions/69456/no-programs-or-applications-show-up-in-dash)
There's been some sort of problem so I've not tried other solutions found in other threads yet because I want to know what happened. 
This is what was spat out during the during the reset. Applications are still missing from dash.
```
WARNING: Unity currently default profile, so switching to metacity while resetting the values
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1e00004

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2200006

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x4250fcb

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x42000b8

Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
Initializing resize options...done
Initializing place options...done
Initializing move options...done
Initializing wall options...done
Initializing grid options...done
Initializing session options...done
Initializing gnomecompat options...done
Initializing animation options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing workarounds options...done
Initializing scale options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing ezoom options...done

(compiz:11703): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
Initializing unityshell options...done
compiz (core) - Warn: unhandled ConfigureNotify on 0x140009e!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x14000a1!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x14000a4!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x14000a7!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x14000a7!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
WARN  2012-08-21 17:43:10 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-08-21 17:43:10 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-calc.desktop' is using a deprecated format for its actions that will be dropped soon.
Initializing staticswitcher options...done
ERROR 2012-08-21 17:43:13 unity.glib-gobject <unknown>:0 g_object_unref: assertion `G_IS_OBJECT (object)' failed
Setting Update "main_menu_key"
Setting Update "run_key"
WARN  2012-08-21 17:43:25 unity.glib.dbusproxy GLibDBusProxy.cpp:283 Calling method "Sync" on object path: "/com/canonical/Unity/Panel/Service" failed: GDBus.Error:org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
???@???:~$ WARN  2012-08-21 17:44:35 unity.glib.dbusproxy GLibDBusProxy.cpp:182 Unable to connect to proxy: Error calling StartServiceByName for com.canonical.Unity.Lens.Applications: Timeout was reached
WARN  2012-08-21 17:44:35 unity.glib.dbusproxy GLibDBusProxy.cpp:182 Unable to connect to proxy: Error calling StartServiceByName for com.canonical.Unity.Lens.Applications: Timeout was reached
WARN  2012-08-21 17:45:12 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application283295483

WARN  2012-08-21 17:45:12 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application283295483

ERROR 2012-08-21 17:45:14 unity.glib-gobject <unknown>:0 g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
WARN  2012-08-21 17:45:26 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application283295483

WARN  2012-08-21 17:45:29 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application283295483

ERROR 2012-08-21 17:45:31 unity.glib-gobject <unknown>:0 g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
```A few moments later there was an internal error message, unfortunately I accidentally hit continue before jotting down the path of the error. I don't know if this is serious or not, so I'd appreciate any help with this. Thanks.

---

