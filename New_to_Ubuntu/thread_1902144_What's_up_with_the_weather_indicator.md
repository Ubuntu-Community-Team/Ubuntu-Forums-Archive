---
title: "What's up with the weather indicator?"
date: 2011-12-30
forum: New to Ubuntu
---

### Post by jermza on 2011-12-30
So I'm going along nicely, with my weather indicator giving me the weather.

[IMG]http://i.imgur.com/ORhGu.png[/IMG]

For no reason, during the middle of some usual task that I'm busy with, the indicator simply disappears as if it were never there to begin with. So I have to find it in my dash and reactivate it.

This has happened a few times before, but not often.

Any idea as to why this occurs?

---

### Post by The Cog on 2011-12-30
I have no idea if this is relevant, but there has just been an update released for the Xubuntu weather applet. Maybe there's a general fix, so it might be worth checking for updates with your update manager.

---

### Post by Frogs Hair on 2011-12-30
Try restarting it by locating the icon in dash if using 11.10 . If it was updated in some way you may have to set to start automatically again .

---

### Post by rosswmcgee on 2012-04-25
This happens to me at least twice a day, the weather indicator leaves the panel and

has to be found in dash and then put back on the panel.

---

### Post by Toz on 2012-04-25
The next time it happens, have a look at the .xsession-errors file in your home directory (its a hidden file). Towards the bottom of that file you might find some clues (errors) as to why its happening.

---

### Post by rosswmcgee on 2012-04-25
I cannot find the file. Tried it first in Ubuntu and then in Classic, no luck.

---

### Post by Toz on 2012-04-25
Its a hidden file in your home directory. From a terminal window, type this:
```
cat ~/.xsession-errors
```
...to view the file in the terminal, or:
```
gedit ~/.xsession-errors
```
...to view it in the text editor.

---

### Post by rosswmcgee on 2012-05-17
I do not see any clues there. I use the Ubuntu rather than classic, but the classic

weather app has the radar, forecast and current conditions all in one. Instead in ubuntu 12.04 you have two different apps. And yes the weather app does leave the panel at least once a day, not a problem to restore it , but it was an error not to use
the app used in classic, in my opinion.

---

### Post by Toz on 2012-05-17
Feel free to post back the contents of that file after the weather applet crashed. Perhaps a second set of eyes can identify a cause.

---

### Post by rosswmcgee on 2012-05-17
```
Here goes:
/usr/bin/indicator-weather:1932: Warning: g_variant_ref_sink: assertion `value->ref_count > 0' failed
  gtk.main()
/usr/bin/indicator-weather:1932: Warning: g_variant_ref: assertion `value->ref_count > 0' failed
  gtk.main()
/usr/bin/indicator-weather:1932: Warning: g_variant_get_type_string: assertion `value != NULL' failed
  gtk.main()


Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done

(gnome-settings-daemon:17452): GLib-CRITICAL **: g_variant_new_string: assertion `string != NULL' failed

(gnome-settings-daemon:17452): GLib-GIO-CRITICAL **: g_settings_schema_key_type_check: assertion `value != NULL' failed

(gnome-settings-daemon:17452): GLib-CRITICAL **: g_variant_get_type_string: assertion `value != NULL' failed

(gnome-settings-daemon:17452): GLib-GIO-CRITICAL **: g_settings_set_value: key 'picture-uri' in 'org.gnome.desktop.background' expects type 's', but a GVariant of type '(null)' was given
Initializing composite options...done
Cannot get client list properties. 
(_NET_CLIENT_LIST or _WIN_CLIENT_LIST)
Cannot get client list properties. 
(_NET_CLIENT_LIST or _WIN_CLIENT_LIST)
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 55
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 56
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 59
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 58
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30
Initializing opengl options...done
Initializing decor options...done
/usr/lib/python2.7/dist-packages/gobject/constants.py:24: Warning: g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
  import gobject._gobject
Initializing vpswitch options...done
Initializing snap options...done
Initializing resize options...done
Initializing animation options...done
** Message: applet now removed from the notification area
Cannot get client list properties. 
(_NET_CLIENT_LIST or _WIN_CLIENT_LIST)
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
** Message: using fallback from indicator to GtkStatusIcon
Initializing workarounds options...done
Initializing gnomecompat options...done
Initializing mousepoll options...done
Initializing wall options...done
Initializing move options...done
Initializing grid options...done
Initializing place options...done
Initializing ezoom options...done
Initializing unitymtgrabhandles options...done
Initializing fade options...done
I/O warning : failed to load external entity "/home/rosswmcgee/.compiz/session/103613703acfd0c192133722217194173500000173900037"
Initializing session options...done
Initializing scale options...done
Cannot get client list properties. 
(_NET_CLIENT_LIST or _WIN_CLIENT_LIST)

(compiz:17458): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
Cannot get client list properties. 
(_NET_CLIENT_LIST or _WIN_CLIENT_LIST)
Initializing unityshell options...done
Initializing staticswitcher options...done
** Message: moving back from GtkStatusIcon to indicator
Setting Update "icon_size"
Setting Update "edge_responsiveness"
Setting Update "main_menu_key"
Setting Update "run_key"

** (zeitgeist-datahub:17953): WARNING **: zeitgeist-datahub.vala:227: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!

** (nautilus:17473): WARNING **: Error calling current_status: Method "current_status" with signature "" on interface "com.ubuntuone.SyncDaemon.Status" doesn't exist


** (nautilus:17473): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (opera:17712): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:17712): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:17712): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:17712): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:17712): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:17712): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:17712): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:17712): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:17712): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:17712): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:17712): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:17712): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:17712): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:17712): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:17712): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

(evolution-alarm-notify:18070): evolution-alarm-notify-WARNING **: alarm.c:260: Requested removal of nonexistent alarm!
compiz (core) - Warn: failed to receive ConfigureNotify event on 0xe00008


(gcalctool:18051): Gtk-WARNING **: Invalid text buffer iterator: either the iterator is uninitialized, or the characters/pixbufs/widgets in the buffer have been modified since the iterator was created.
You must use marks, character numbers, or line numbers to preserve a position across buffer modifications.
You can apply tags and insert marks without invalidating your iterators,
but any mutation that affects 'indexable' buffer contents (contents that can be referred to by character offset)
will invalidate all outstanding iterators
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  20 (X_GetProperty)
  Resource id in failed request:  0xe00008
  Serial number of failed request:  10
  Current serial number in output stream:  10
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  20 (X_GetProperty)
  Resource id in failed request:  0xe00008
  Serial number of failed request:  10
  Current serial number in output stream:  10

** (opera:16220): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:16220): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:16220): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:16220): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:16220): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:16220): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:16220): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:16220): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:16220): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:16220): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:16220): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:16220): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:16220): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:16220): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:16220): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:16220): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:16220): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:16220): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:16220): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:16220): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:16220): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:16220): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:16220): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:16220): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
/usr/lib/python2.7/dist-packages/gobject/constants.py:24: Warning: g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
  import gobject._gobject

(indicator-weather:25795): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(gcalctool:26734): Gtk-WARNING **: Invalid text buffer iterator: either the iterator is uninitialized, or the characters/pixbufs/widgets in the buffer have been modified since the iterator was created.
You must use marks, character numbers, or line numbers to preserve a position across buffer modifications.
You can apply tags and insert marks without invalidating your iterators,
but any mutation that affects 'indexable' buffer contents (contents that can be referred to by character offset)
will invalidate all outstanding iterators
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  20 (X_GetProperty)
  Resource id in failed request:  0x2c00008
  Serial number of failed request:  10
  Current serial number in output stream:  10

** (opera:26030): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:26030): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:26030): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:26030): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:26030): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:26030): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:26030): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:26030): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:26030): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:26030): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:26030): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:26030): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:26030): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:26030): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:26030): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:26030): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:26030): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:26030): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:26030): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:26030): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:26030): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:26030): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:26030): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:26030): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed
DEBUG: (0x8625e60) GritsViewer: set_offline - 0
DEBUG: (0x8625e60) GritsPrefs: save
DEBUG: (0x8625e60) AWeatherGui: get_widget - name=update
DEBUG: (0x8625e60) AWeatherGui: get_widget - name=update
DEBUG: (0x8625e60) AWeatherGui: get_widget - name=fullscreen
DEBUG: (0x8625e60) AWeatherGui: load_plugins
DEBUG: (0x8625e60) GritsPlugins: available
DEBUG: (0x8625e60) pluginsdir=/usr/lib/grits4
DEBUG: (0x8625e60)             checking /usr/lib/aweather
DEBUG: (0x8625e60)             checking /usr/lib/grits4
DEBUG: (0x8625e60) GritsPlugins: load env
DEBUG: (0x8625e60) GritsPlugins: load - trying /usr/lib/aweather/env.so
DEBUG: (0x8625e60) GritsPlugins: load - trying /usr/lib/grits4/env.so
DEBUG: (0x8625e60) GritsPluginEnv: new
DEBUG: (0x8625e60) GritsPluginEnv: class_init
DEBUG: (0x8625e60) GritsPluginEnv: plugin_init
DEBUG: (0x8625e60) GritsPluginEnv: init
DEBUG: (0x8625e60) GritsCallback: init
DEBUG: (0x8625e60) GritsPlugins: load map
DEBUG: (0x8625e60) GritsPlugins: load - trying /usr/lib/aweather/map.so
DEBUG: (0x8625e60) GritsPlugins: load - trying /usr/lib/grits4/map.so
DEBUG: (0x8625e60) GritsPluginMap: new
DEBUG: (0x8625e60) GritsPluginMap: class_init
DEBUG: (0x8625e60) GritsPluginMap: plugin_init
DEBUG: (0x8625e60) GritsPluginMap: init
DEBUG: (0x8625e60) GritsTile: class_init
DEBUG: (0x8625e60) GritsHttp: new - osmtile/
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _update_tiles
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 00.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 00.00.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 00.01.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 00.10.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 00.10.00.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 00.10.01.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 00.10.01.10.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 00.10.01.11.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 00.10.10.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 00.10.10.01.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 00.10.10.11.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 00.10.11.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 00.10.11.00.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 00.10.11.01.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 00.10.11.10.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 00.10.11.11.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 00.11.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 00.11.00.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 00.11.00.10.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 00.11.01.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 00.11.10.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 00.11.10.00.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 00.11.10.01.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 00.11.10.10.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 00.11.10.11.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 00.11.11.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 01.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 01.10.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 01.11.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 10.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 10.00.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 10.00.00.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 10.00.01.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 10.01.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 10.01.00.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 10.01.01.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 11.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginMap: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 11.00.png mode=1
DEBUG: (0x8625e60) GritsPluginMap: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPlugins: load radar
DEBUG: (0x8625e60) GritsPlugins: load - trying /usr/lib/aweather/radar.so
DEBUG: (0x8625e60) GritsPlugins: load - trying /usr/lib/aweather/radar.so
DEBUG: (0x8625e60) GritsPluginRadar: new
DEBUG: (0x8625e60) GritsPluginRadar: class_init
DEBUG: (0x8625e60) GritsPluginRadar: plugin_init
DEBUG: (0x8625e60) GritsPluginRadar: class_init
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/conus/
DEBUG: (0x8625e60) GritsPluginRadar: _load_colormap - /usr/share/aweather/colors/dz.clr
DEBUG: (0x8625e60) GritsPluginRadar: _load_colormap - /usr/share/aweather/colors/vr.clr
DEBUG: (0x8625e60) GritsPluginRadar: _load_colormap - /usr/share/aweather/colors/sw.clr
DEBUG: (0x8625e60) GritsPluginRadar: _load_colormap - /usr/share/aweather/colors/dr.clr
DEBUG: (0x8625e60) GritsPluginRadar: _load_colormap - /usr/share/aweather/colors/ph.clr
DEBUG: (0x8625e60) GritsPluginRadar: _load_colormap - /usr/share/aweather/colors/rh.clr
DEBUG: (0x8625e60) GritsCallback: init
DEBUG: (0x8625e60) GritsPluginRadar: _update_hidden - 0..1 = 0
DEBUG: (0x8625e60) GritsViewer: get_time
DEBUG: (0x8625e60) Conus: update - 1337276230
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsMarker: class_init
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x884ad20) Conus: update_thread - nearest
DEBUG: (0x884ad20) GritsViewer: get_offline - 0
DEBUG: (0x884ad20) Conus: update_thread - fetch
DEBUG: (0x884ad20) GritsHttp: fetch - Conus_20120517_1728_N0Ronly.gif mode=1
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x884ad20) GritsHttp: fetch - Caching file Conus_20120517_1728_N0Ronly.gif
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: new - /nexrad/level2/
DEBUG: (0x8625e60) AWeatherGui: get_widget - name=main_tabs
DEBUG: (0x8625e60) GritsPlugins: load sat
DEBUG: (0x8625e60) GritsPlugins: load - trying /usr/lib/aweather/sat.so
DEBUG: (0x8625e60) GritsPlugins: load - trying /usr/lib/grits4/sat.so
DEBUG: (0x8625e60) GritsPluginSat: new
DEBUG: (0x8625e60) GritsPluginSat: class_init
DEBUG: (0x8625e60) GritsPluginSat: plugin_init
DEBUG: (0x8625e60) GritsPluginSat: init
DEBUG: (0x8625e60) GritsWms: new - [http://www.nasa.network.com/wms](http://www.nasa.network.com/wms)
DEBUG: (0x8625e60) GritsHttp: new - bmng/
DEBUG: (0x8625e60) GritsPluginSat: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - jpg mode=1
DEBUG: (0x8625e60) GritsPluginSat: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsPluginSat: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - jpg mode=1
DEBUG: (0x8625e60) GritsPluginSat: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginSat: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 00.jpg mode=1
DEBUG: (0x8625e60) GritsPluginSat: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginSat: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 00.00.jpg mode=1
DEBUG: (0x8625e60) GritsPluginSat: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginSat: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 00.01.jpg mode=1
DEBUG: (0x8625e60) GritsPluginSat: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginSat: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 00.10.jpg mode=1
DEBUG: (0x8625e60) GritsPluginSat: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginSat: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 00.11.jpg mode=1
DEBUG: (0x8625e60) GritsPluginSat: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsPluginSat: _load_tile start 0x8625e60
DEBUG: (0x8625e60) GritsHttp: fetch - 10.jpg mode=1
DEBUG: (0x8625e60) GritsPluginSat: _load_tile end 0x8625e60
DEBUG: (0x8625e60) GritsOpenGL: on_realize
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) AWeatherGui: get_widget - name=fullscreen
DEBUG: (0x8625e60) AWeatherGui: on_configure - 600x400
DEBUG: (0x8625e60) AWeatherGui: on_configure - 600x400
DEBUG: (0x8625e60) AWeatherGui: on_configure - 600x400
DEBUG: (0x8625e60) AWeatherGui: on_configure - 600x400
DEBUG: (0x8625e60) GritsPluginRadar: _update_hidden - 0..1 = 0
DEBUG: (0x8625e60) GritsOpenGL: on_configure
DEBUG: (0x8625e60) RoamSphere: update_errors - polys=8
DEBUG: (0x8625e60) RoamPoint: Projected 0 points
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x884ad20) Conus: update_thread - done
DEBUG: (0x8625e60) GritsPrefs: save
DEBUG: (0x8625e60) AWeatherGui: on_configure - 600x400
DEBUG: (0x8625e60) RoamPoint: Projected 14 points
DEBUG: (0x8625e60) GritsOpenGL: on_configure
DEBUG: (0x8625e60) RoamSphere: update_errors - polys=1336
DEBUG: (0x8625e60) RoamPoint: Projected 2059 points
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) RoamPoint: Projected 1776 points
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) Conus: update_end
DEBUG: (0x8625e60) Conus: update_end_split
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=152,16
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=154,35
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=157,54
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=159,73
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=162,90
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=164,107
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=167,122
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=172,137
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=177,152
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=182,167
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=187,180
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=192,193
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=197,206
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=202,219
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=207,232
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=212,243
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=214,254
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=217,265
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=220,276
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=220,287
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=223,293
DEBUG: (0x8625e60) GritsOpenGL: on_configure
DEBUG: (0x8625e60) RoamSphere: update_errors - polys=2004
DEBUG: (0x8625e60) RoamPoint: Projected 2043 points
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginSat: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginSat: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginSat: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginSat: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginSat: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginSat: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginSat: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginSat: _load_tile_cb start
DEBUG: (0x8625e60) AWeatherGui: on_configure - 600x400
DEBUG: (0x8625e60) GritsPrefs: save
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) AWeatherGui: on_configure - 600x400
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=231,290
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=227,276
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=225,262
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=222,249
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=220,236
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=219,222
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=217,208
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=217,194
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=215,183
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=213,173
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=213,166
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=211,161
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=211,157
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=211,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=211,155
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=210,155
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=209,155
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=208,155
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=207,155
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=205,155
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=203,155
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=201,155
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=198,155
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=195,155
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=191,155
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=187,155
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=183,155
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=179,155
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=174,155
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=170,155
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=167,155
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=163,155
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=161,155
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=159,155
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=157,155
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=155,155
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=152,155
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=149,155
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=147,155
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=146,155
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=145,155
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=144,155
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=143,155
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=142,155
DEBUG: (0x8625e60) GritsViewer: zoom
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.00.11.png mode=1
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0xb6c04950) GritsPluginSat: _update_tiles
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.01.10.png mode=1
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.11.00.11.png mode=1
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) GritsViewer: zoom
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.10.00.11.png mode=1
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.10.01.01.png mode=1
DEBUG: (0xb6c04950) GritsPluginSat: _update_tiles
DEBUG: (0xb6c04950) GritsPluginSat: _load_tile start 0xb6c04950
DEBUG: (0xb6c04950) GritsHttp: fetch - 00.10.01.jpg mode=1
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x8625e60) GritsPrefs: save
DEBUG: (0x8625e60) GritsViewer: zoom
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.10.01.00.png mode=1
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.10.11.01.00.png mode=1
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=142,156
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.10.11.01.01.png mode=1
DEBUG: (0xb6c04950) GritsPluginSat: _load_tile end 0xb6c04950
DEBUG: (0xb6c04950) GritsPluginSat: _update_tiles
DEBUG: (0xb6c04950) GritsPluginSat: _load_tile start 0xb6c04950
DEBUG: (0xb6c04950) GritsHttp: fetch - 00.11.00.jpg mode=1
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.10.11.01.10.png mode=1
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.10.11.01.11.png mode=1
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.11.00.00.png mode=1
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0xb6c04950) GritsPluginSat: _load_tile end 0xb6c04950
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=142,157
DEBUG: (0x8625e60) RoamSphere: update_errors - polys=2004
DEBUG: (0x8625e60) RoamPoint: Projected 2739 points
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=142,158
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginSat: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginSat: _load_tile_cb start
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) GritsViewer: zoom
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.10.01.11.10.png mode=1
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.10.01.11.11.png mode=1
DEBUG: (0xb6c04950) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.10.11.00.01.png mode=1
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.10.11.00.11.png mode=1
DEBUG: (0x8625e60) GritsViewer: zoom
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0xb6c04950) GritsPluginSat: _update_tiles
DEBUG: (0xb6c04950) GritsPluginSat: _load_tile start 0xb6c04950
DEBUG: (0xb6c04950) GritsHttp: fetch - 00.00.11.jpg mode=1
DEBUG: (0x8625e60) GritsViewer: zoom
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=143,158
DEBUG: (0x8625e60) GritsViewer: zoom
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.11.10.00.00.png mode=1
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.11.10.00.10.png mode=1
DEBUG: (0xb6c04950) GritsPluginSat: _load_tile end 0xb6c04950
DEBUG: (0xb6c04950) GritsPluginSat: _load_tile start 0xb6c04950
DEBUG: (0xb6c04950) GritsHttp: fetch - 00.10.11.jpg mode=1
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.10.01.10.11.png mode=1
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.10.01.11.00.png mode=1
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.10.01.11.01.png mode=1
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.10.11.11.00.png mode=1
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.10.11.11.01.png mode=1
DEBUG: (0xb6c04950) GritsPluginSat: _load_tile end 0xb6c04950
DEBUG: (0xb6c04950) GritsPluginSat: _update_tiles
DEBUG: (0xb6c04950) GritsPluginSat: _load_tile start 0xb6c04950
DEBUG: (0xb6c04950) GritsHttp: fetch - 00.01.10.jpg mode=1
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.11.00.10.10.png mode=1
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.11.10.00.01.png mode=1
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.11.10.00.11.png mode=1
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.11.10.10.00.png mode=1
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0xb6c04950) GritsPluginSat: _load_tile end 0xb6c04950
DEBUG: (0xb6c04950) GritsPluginSat: _load_tile start 0xb6c04950
DEBUG: (0xb6c04950) GritsHttp: fetch - 00.11.10.jpg mode=1
DEBUG: (0xb6c04950) GritsPluginSat: _load_tile end 0xb6c04950
DEBUG: (0xb6c04950) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=141,158
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=139,158
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=137,158
DEBUG: (0x8625e60) RoamPoint: Projected 2006 points
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=136,158
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) RoamPoint: Projected 3312 points
DEBUG: (0x8625e60) RoamSphere: update_errors - polys=2146
DEBUG: (0x8625e60) RoamPoint: Projected 1408 points
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) GritsViewer: on_button_press - 1
DEBUG: (0x8625e60) RoamPoint: Projected 2937 points
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.027, sideways=  -0.034, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=137,159
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.068, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=139,159
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.027, sideways=  -0.068, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=141,160
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.068, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=143,160
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.102, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=146,160
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.136, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=150,160
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.170, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=155,160
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.170, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=160,160
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.204, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=166,160
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.305, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.10.11.10.01.png mode=1
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=175,160
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.373, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.10.11.00.00.png mode=1
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=186,160
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.407, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=198,160
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.441, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.10.11.00.10.png mode=1
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=211,160
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.543, up=   0.000
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=227,160
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.543, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.00.10.png mode=1
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=243,160
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.543, up=   0.000
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=259,160
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.543, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=275,160
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.509, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.10.01.10.01.png mode=1
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.10.01.10.10.png mode=1
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=290,160
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.441, up=   0.000
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=303,160
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.407, up=   0.000
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=315,160
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.509, up=   0.000
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=330,160
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.509, up=   0.000
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=345,160
DEBUG: (0x8625e60) GritsViewer: pan - forward=   0.053, sideways=  -0.509, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=360,158
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.509, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=375,158
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.441, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.10.00.01.png mode=1
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=388,158
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.441, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=401,158
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.373, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=412,158
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.271, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=420,158
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.271, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=428,158
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) GritsViewer: pan - forward=   0.053, sideways=  -0.305, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x9346580) GritsPluginSat: _load_tile start 0x9346580
DEBUG: (0x9346580) GritsHttp: fetch - 00.10.00.jpg mode=1
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=437,156
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.271, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.10.10.00.png mode=1
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=445,156
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.271, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=453,156
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.204, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=459,156
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.102, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=462,156
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x9346580) GritsPluginSat: _load_tile end 0x9346580
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x9346580) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) GritsViewer: on_button_release
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=461,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=460,156
DEBUG: (0x8625e60) RoamSphere: update_errors - polys=2000
DEBUG: (0x8625e60) RoamPoint: Projected 378 points
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginSat: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginSat: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginSat: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginSat: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginSat: _load_tile_cb start
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=458,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=455,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=451,156
DEBUG: (0x8625e60) RoamPoint: Projected 1744 points
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=446,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=440,156
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=432,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=422,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=409,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=393,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=377,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=361,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=343,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=325,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=306,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=290,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=275,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=260,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=247,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=236,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=228,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=219,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=213,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=210,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=209,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=208,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=207,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=205,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=203,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=200,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=197,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=195,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=193,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=191,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=189,156
DEBUG: (0x8625e60) RoamPoint: Projected 2690 points
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=187,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=185,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=184,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=183,156
DEBUG: (0x8625e60) GritsViewer: on_button_press - 1
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.027, sideways=   0.000, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0xb6c049b0) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=183,157
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.027, sideways=  -0.068, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0xb6c049b0) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=185,158
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.102, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0xb6c049b0) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=188,158
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.170, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0xb6c049b0) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=193,158
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.271, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0xb6c049b0) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=201,158
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.441, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0xb6c049b0) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=214,158
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.577, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.10.10.01.01.png mode=1
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.10.11.10.00.png mode=1
DEBUG: (0xb6c049b0) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=231,158
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.645, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0xb6c049b0) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=250,158
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.645, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.10.10.01.11.png mode=1
DEBUG: (0xb6c049b0) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=269,158
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.645, up=   0.000
DEBUG: (0xb6c049b0) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=288,158
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.645, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0xb6c049b0) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=307,158
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.645, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0xb6c049b0) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=326,158
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.577, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.10.00.11.11.png mode=1
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.10.01.10.00.png mode=1
DEBUG: (0xb6c049b0) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=343,158
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.509, up=   0.000
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.10.00.10.png mode=1
DEBUG: (0xb6c049b0) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=358,158
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.509, up=   0.000
DEBUG: (0xb6c049b0) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=373,158
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.373, up=   0.000
DEBUG: (0xb6c049b0) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=384,158
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.305, up=   0.000
DEBUG: (0xb6c049b0) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=393,158
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.204, up=   0.000
DEBUG: (0xb6c049b0) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=399,158
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.136, up=   0.000
DEBUG: (0xb6c049b0) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=403,158
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x868d580) GritsPluginMap: _load_tile start 0x868d580
DEBUG: (0x868d580) GritsHttp: fetch - 00.10.10.10.png mode=1
DEBUG: (0x868d580) GritsPluginMap: _load_tile end 0x868d580
DEBUG: (0x868d580) GritsPluginMap: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) RoamSphere: update_errors - polys=2000
DEBUG: (0x8625e60) RoamPoint: Projected 375 points
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.068, up=   0.000
DEBUG: (0xb6c049b0) GritsPluginMap: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x9346550) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=405,158
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.102, up=   0.000
DEBUG: (0xb6c049b0) GritsPluginMap: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x9346550) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=408,158
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.102, up=   0.000
DEBUG: (0xb6c049b0) GritsPluginMap: _update_tiles
DEBUG: (0x9346550) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=411,158
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.102, up=   0.000
DEBUG: (0xb6c049b0) GritsPluginMap: _update_tiles
DEBUG: (0x9346550) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=414,158
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.136, up=   0.000
DEBUG: (0xb6c049b0) GritsPluginMap: _update_tiles
DEBUG: (0x9346550) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=418,158
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.102, up=   0.000
DEBUG: (0xb6c049b0) GritsPluginMap: _update_tiles
DEBUG: (0x9346550) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=421,158
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.068, up=   0.000
DEBUG: (0xb6c049b0) GritsPluginMap: _update_tiles
DEBUG: (0x9346550) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=423,158
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.034, up=   0.000
DEBUG: (0xb6c049b0) GritsPluginMap: _update_tiles
DEBUG: (0x9346550) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=424,158
DEBUG: (0x8625e60) GritsViewer: pan - forward=  -0.000, sideways=  -0.034, up=   0.000
DEBUG: (0xb6c049b0) GritsPluginMap: _update_tiles
DEBUG: (0x9346550) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=425,158
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) RoamPoint: Projected 2114 points
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) RoamPoint: Projected 2152 points
DEBUG: (0x8625e60) RoamSphere: update_errors - polys=2004
DEBUG: (0x8625e60) RoamPoint: Projected 384 points
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) GritsViewer: on_button_release
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=423,158
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=420,158
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=417,158
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=413,158
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=409,158
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=405,158
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=401,158
DEBUG: (0x8625e60) RoamPoint: Projected 2726 points
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=397,158
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=392,158
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=388,158
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=385,157
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=379,157
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=375,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=371,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=367,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=364,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=361,156
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=358,155
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=356,155
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=355,155
DEBUG: (0x8625e60) GritsViewer: zoom
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0xb6c049b0) GritsPluginMap: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x936c4f0) GritsPluginSat: _update_tiles
DEBUG: (0x936c4f0) GritsPluginSat: _load_tile start 0x936c4f0
DEBUG: (0x936c4f0) GritsHttp: fetch - 00.00.10.jpg mode=1
DEBUG: (0x936c4f0) GritsPluginSat: _load_tile end 0x936c4f0
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) GritsViewer: zoom
DEBUG: (0xb6c049b0) GritsPluginMap: _update_tiles
DEBUG: (0x936c4f0) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsViewer: zoom
DEBUG: (0xb6c049b0) GritsPluginMap: _update_tiles
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile start 0xb6c049b0
DEBUG: (0xb6c049b0) GritsHttp: fetch - 00.10.11.00.01.00.png mode=1
DEBUG: (0x936c4f0) GritsPluginSat: _update_tiles
DEBUG: (0x936c4f0) GritsPluginSat: _load_tile start 0x936c4f0
DEBUG: (0x936c4f0) GritsHttp: fetch - 00.10.01.00.jpg mode=1
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile end 0xb6c049b0
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile start 0xb6c049b0
DEBUG: (0xb6c049b0) GritsHttp: fetch - 00.10.11.00.01.01.png mode=1
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile end 0xb6c049b0
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile start 0xb6c049b0
DEBUG: (0xb6c049b0) GritsHttp: fetch - 00.10.11.00.01.10.png mode=1
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile end 0xb6c049b0
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile start 0xb6c049b0
DEBUG: (0xb6c049b0) GritsHttp: fetch - 00.10.11.00.01.11.png mode=1
DEBUG: (0x936c4f0) GritsPluginSat: _load_tile end 0x936c4f0
DEBUG: (0x936c4f0) GritsPluginSat: _load_tile start 0x936c4f0
DEBUG: (0x936c4f0) GritsHttp: fetch - 00.10.01.10.jpg mode=1
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile end 0xb6c049b0
DEBUG: (0x936c4f0) GritsPluginSat: _load_tile end 0x936c4f0
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) RoamSphere: update_errors - polys=2020
DEBUG: (0x8625e60) RoamPoint: Projected 247 points
DEBUG: (0x8625e60) GritsPluginSat: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginSat: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginSat: _load_tile_cb start
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=355,156
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) GritsViewer: zoom
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0xb6c049b0) GritsPluginMap: _update_tiles
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile start 0xb6c049b0
DEBUG: (0xb6c049b0) GritsHttp: fetch - 00.10.00.11.01.png mode=1
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile end 0xb6c049b0
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile start 0xb6c049b0
DEBUG: (0xb6c049b0) GritsHttp: fetch - 00.10.01.10.10.11.png mode=1
DEBUG: (0x936c520) GritsPluginSat: _update_tiles
DEBUG: (0x936c520) GritsPluginSat: _load_tile start 0x936c520
DEBUG: (0x936c520) GritsHttp: fetch - 00.10.01.01.jpg mode=1
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile end 0xb6c049b0
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile start 0xb6c049b0
DEBUG: (0xb6c049b0) GritsHttp: fetch - 00.10.01.10.11.10.png mode=1
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile end 0xb6c049b0
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile start 0xb6c049b0
DEBUG: (0xb6c049b0) GritsHttp: fetch - 00.10.01.10.11.11.png mode=1
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile end 0xb6c049b0
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile start 0xb6c049b0
DEBUG: (0xb6c049b0) GritsHttp: fetch - 00.10.11.00.00.01.png mode=1
DEBUG: (0x8625e60) GritsViewer: zoom
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsViewer: zoom
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsViewer: zoom
DEBUG: (0x8625e60) GritsOpenGL: on_view_changed
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile end 0xb6c049b0
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile start 0xb6c049b0
DEBUG: (0xb6c049b0) GritsHttp: fetch - 00.10.11.00.00.11.png mode=1
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile end 0xb6c049b0
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile start 0xb6c049b0
DEBUG: (0xb6c049b0) GritsHttp: fetch - 00.10.11.01.00.00.png mode=1
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile end 0xb6c049b0
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile start 0xb6c049b0
DEBUG: (0xb6c049b0) GritsHttp: fetch - 00.10.11.01.00.10.png mode=1
DEBUG: (0x936c520) GritsPluginSat: _load_tile end 0x936c520
DEBUG: (0x936c520) GritsPluginSat: _load_tile start 0x936c520
DEBUG: (0x936c520) GritsHttp: fetch - 00.10.01.11.jpg mode=1
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile end 0xb6c049b0
DEBUG: (0xb6c049b0) GritsPluginMap: _update_tiles
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile start 0xb6c049b0
DEBUG: (0xb6c049b0) GritsHttp: fetch - 00.10.01.10.10.01.png mode=1
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile end 0xb6c049b0
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile start 0xb6c049b0
DEBUG: (0xb6c049b0) GritsHttp: fetch - 00.10.01.10.10.10.png mode=1
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile end 0xb6c049b0
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile start 0xb6c049b0
DEBUG: (0xb6c049b0) GritsHttp: fetch - 00.10.01.10.11.00.png mode=1
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile end 0xb6c049b0
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile start 0xb6c049b0
DEBUG: (0xb6c049b0) GritsHttp: fetch - 00.10.01.10.11.01.png mode=1
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile end 0xb6c049b0
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile start 0xb6c049b0
DEBUG: (0xb6c049b0) GritsHttp: fetch - 00.10.01.11.10.00.png mode=1
DEBUG: (0x936c520) GritsPluginSat: _load_tile end 0x936c520
DEBUG: (0x936c520) GritsPluginSat: _update_tiles
DEBUG: (0x936c520) GritsPluginSat: _load_tile start 0x936c520
DEBUG: (0x936c520) GritsHttp: fetch - 00.00.11.10.jpg mode=1
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile end 0xb6c049b0
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile start 0xb6c049b0
DEBUG: (0xb6c049b0) GritsHttp: fetch - 00.10.01.11.10.10.png mode=1
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile end 0xb6c049b0
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile start 0xb6c049b0
DEBUG: (0xb6c049b0) GritsHttp: fetch - 00.10.11.00.00.00.png mode=1
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile end 0xb6c049b0
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile start 0xb6c049b0
DEBUG: (0xb6c049b0) GritsHttp: fetch - 00.10.11.00.00.10.png mode=1
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile end 0xb6c049b0
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile start 0xb6c049b0
DEBUG: (0xb6c049b0) GritsHttp: fetch - 00.10.11.00.10.01.png mode=1
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile end 0xb6c049b0
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile start 0xb6c049b0
DEBUG: (0xb6c049b0) GritsHttp: fetch - 00.10.11.00.11.00.png mode=1
DEBUG: (0x936c520) GritsPluginSat: _load_tile end 0x936c520
DEBUG: (0x936c520) GritsPluginSat: _load_tile start 0x936c520
DEBUG: (0x936c520) GritsHttp: fetch - 00.00.11.11.jpg mode=1
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile end 0xb6c049b0
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile start 0xb6c049b0
DEBUG: (0xb6c049b0) GritsHttp: fetch - 00.10.11.00.11.01.png mode=1
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile end 0xb6c049b0
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile start 0xb6c049b0
DEBUG: (0xb6c049b0) GritsHttp: fetch - 00.10.11.01.10.00.png mode=1
DEBUG: (0xb6c049b0) GritsPluginMap: _load_tile end 0xb6c049b0
DEBUG: (0xb6c049b0) GritsPluginMap: _update_tiles
DEBUG: (0xb6c049b0) GritsPluginMap: _update_tiles
DEBUG: (0x936c520) GritsPluginSat: _load_tile end 0x936c520
DEBUG: (0x936c520) GritsPluginSat: _update_tiles
DEBUG: (0x936c520) GritsPluginSat: _update_tiles
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) RoamPoint: Projected 1901 points
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) RoamPoint: Projected 3140 points
DEBUG: (0x8625e60) RoamSphere: update_errors - polys=2040
DEBUG: (0x8625e60) RoamPoint: Projected 1186 points
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginSat: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginSat: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginSat: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginMap: _load_tile_cb start
DEBUG: (0x8625e60) GritsPluginSat: _load_tile_cb start
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 2,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 140,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsPluginRadar: _draw_hud
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=355,157
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=355,158
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=355,159
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=355,160
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=355,162
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=355,163
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=355,165
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=355,167
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=354,169
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=353,172
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=351,175
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=350,178
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=347,181
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=342,185
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=334,191
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=323,197
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=309,204
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=296,210
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=282,218
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=265,227
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=249,236
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=233,244
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=218,253
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=204,260
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=189,267
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=174,274
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=167,279
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=156,284
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=147,289
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=143,293
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=142,293
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=142,294
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=142,295
DEBUG: (0x8625e60) GritsOpenGL: on_motion_notify - hits=0 ev=142,296
DEBUG: (0x8625e60) AWeatherGui: dispose
DEBUG: (0x8625e60) GritsPlugins: free
DEBUG: (0x8625e60) GritsPlugin: freeing sat refs=1->0
DEBUG: (0x8625e60) GritsPluginSat: dispose
DEBUG: (0x8625e60) GritsPluginSat: finalize
DEBUG: (0x8625e60) GritsWms: free - [http://www.nasa.network.com/wms](http://www.nasa.network.com/wms)
DEBUG: (0x8625e60) GritsHttp: free - bmng/
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: 0x933c258
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: 0x878c928
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: 0x9456ee8
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: 0x8754d88
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: 0x93949f0
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: 0x94a6cf0
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: 0x87769e0
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: 0x94b0bd0
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: 0x9449d68
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: 0x87ca648
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: 0x93a40f0
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: 0x94732e8
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: 0x94935f0
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: 0x87a3298
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: 0x8770cd8
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: 0x86878b8
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: 0x89749b0
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: 0x87725c0
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: 0x8761ef0
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: 0x8777db8
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: (nil)
DEBUG: (0x8625e60) GritsPluginSat: _free_tile: 0x939e5f0
DEBUG: (0x8625e60) GritsPlugin: freeing radar refs=1->0
DEBUG: (0x8625e60) GritsPluginRadar: dispose
DEBUG: (0x8625e60) GritsCallback: finalize
DEBUG: (0x8625e60) GritsPluginRadar: finalize
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/conus/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsHttp: free - /nexrad/level2/
DEBUG: (0x8625e60) GritsPlugin: freeing map refs=1->0
DEBUG: (0x8625e60) GritsPluginMap: dispose
DEBUG: (0x8625e60) GritsOpenGL: on_configure
DEBUG: (0x8625e60) RoamSphere: update_errors - polys=2040
DEBUG: (0x8625e60) RoamPoint: Projected 2699 points
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 0,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 0,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 0,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 0,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 0,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 0,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 0,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 0,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) RoamPoint: Projected 2922 points
DEBUG: (0x8625e60) GritsOpenGL: on_expose - begin
DEBUG: (0x8625e60) GtkGl: begin
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=-100
DEBUG: (0x8625e60) GritsPluginEnv: expose
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 1,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=0   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 0,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=2   
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 0,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=100 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 0,0 objects
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - level=200 
DEBUG: (0x8625e60) GritsOpenGL: _draw_level - drew 0,0 objects
DEBUG: (0x8625e60) GtkGl: end
DEBUG: (0x8625e60) GritsOpenGL: on_expose - end

DEBUG: (0x8625e60) GritsPluginMap: finalize
DEBUG: (0x8625e60) GritsHttp: free - osmtile/
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x8683138
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x9399bf0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87642e8
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x949fff0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x8666d68
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x8781090
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x877e7b8
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x879a720
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87c2df0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x878ba20
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x86970a8
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x93631c0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x8788bc0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87604c8
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x9388e00
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87cd7d8
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x92f8668
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x86a4ce0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x94a72f0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x8795eb8
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x875eee8
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x877a8a8
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x8893f80
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x93a17f0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x879d718
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x8775948
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x8774328
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x941e2b8
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x933e7a8
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x94595f0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x8792d88
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x8799290
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x86ab9d0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x94a79f0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x9444600
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x94aa108
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87d6210
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87c24a0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x8793e58
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87a0e40
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x877c828
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87d85b0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87a5128
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x868d7f8
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x9446338
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87a91c0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87ae4c8
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x9398bf0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x94a2ff0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87a1970
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x93f4be0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87c7510
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87c2c28
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x934aec0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x8788190
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x878ef90
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x877b298
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x878e598
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x94765f0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87c0fc0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x93ed688
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x931ac70
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x875b930
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x878c998
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x8778d38
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87b14c0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87ac4e8
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x88e3c28
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87b7750
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87ac0b8
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x931cc20
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x8763a60
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87132a8
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87780f0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87d2510
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87ae7c0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87a6a78
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87ccfd0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87ca060
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x875f0e0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x8770068
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87d7cd8
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87c7bf0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87c5750
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87a5090
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87c4a70
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87c14d0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87cb260
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x877f0f0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87a8278
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x93192f8
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87b9028
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87b6fb8
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x877e580
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x939cdf0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x936c188
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x9395af0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x93a61f0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x936cac8
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x93a71f0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87b52f0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x87c5418
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x93a8af0
DEBUG: (0x8625e60) GritsPluginMap: _free_tile: 0x874cfc8
DEBUG: (0x8625e60) GritsPlugin: freeing env refs=1->0
DEBUG: (0x8625e60) GritsPluginEnv: dispose
DEBUG: (0x8625e60) GritsCallback: finalize
DEBUG: (0x8625e60) GritsPrefs: dispose
DEBUG: (0x8625e60) GritsPrefs: save
DEBUG: (0x8625e60) GritsOpenGL: dispose
DEBUG: (0x8625e60) GritsOpenGL: dispose
DEBUG: (0x8625e60) GritsOpenGL: finalize
DEBUG: (0x8625e60) RoamSphere: free
DEBUG: (0x8625e60) RoamPoint: Projected 906 points
DEBUG: (0x8625e60) GritsViewer: finalize
DEBUG: (0x8625e60) GritsViewer: finalize - done
DEBUG: (0x8625e60) AWeatherGui: dispose
DEBUG: (0x8625e60) AWeatherGui: finalize

** (opera:9312): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:9312): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:9312): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:9312): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:9312): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:9312): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:9312): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:9312): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:9312): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:9312): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:9312): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:9312): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:9312): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:9312): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:9312): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:9312): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:9312): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:9312): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:9312): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:9312): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:9312): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:9312): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:9312): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:9312): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed
/usr/lib/python2.7/dist-packages/gobject/constants.py:24: Warning: g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
  import gobject._gobject

** (opera:31056): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:31056): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:31056): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:31056): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:31056): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:31056): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:31056): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:31056): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:31056): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:31056): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:31056): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:31056): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:31056): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:31056): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:31056): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:31056): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:31056): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:31056): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:31056): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:31056): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:31056): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:31056): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:31056): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:31056): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

(indicator-weather:30998): LIBDBUSMENU-GLIB-CRITICAL **: dbusmenu_menuitem_property_get_variant: assertion `DBUSMENU_IS_MENUITEM(mi)' failed

(indicator-weather:30998): LIBDBUSMENU-GLIB-CRITICAL **: dbusmenu_menuitem_property_get_variant: assertion `DBUSMENU_IS_MENUITEM(mi)' failed

(indicator-weather:30998): LIBDBUSMENU-GLIB-CRITICAL **: dbusmenu_menuitem_property_get_variant: assertion `DBUSMENU_IS_MENUITEM(mi)' failed

(indicator-weather:30998): LIBDBUSMENU-GLIB-CRITICAL **: dbusmenu_menuitem_property_get_variant: assertion `DBUSMENU_IS_MENUITEM(mi)' failed

(indicator-weather:30998): LIBDBUSMENU-GLIB-CRITICAL **: dbusmenu_menuitem_get_children: assertion `DBUSMENU_IS_MENUITEM(mi)' failed

(indicator-weather:30998): LIBDBUSMENU-GLIB-CRITICAL **: dbusmenu_menuitem_get_children: assertion `DBUSMENU_IS_MENUITEM(mi)' failed

** (opera:18942): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:18942): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:18942): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:18942): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:18942): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:18942): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:18942): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:18942): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:18942): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:18942): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:18942): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:18942): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:18942): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:18942): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:18942): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:18942): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:18942): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:18942): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:18942): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:18942): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:18942): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

** (opera:18942): CRITICAL **: os_bar_hide: assertion `OS_IS_BAR (bar)' failed

(opera:18942): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (opera:18942): CRITICAL **: os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed
/usr/bin/indicator-weather:1932: Warning: g_variant_ref_sink: assertion `value->ref_count > 0' failed
  gtk.main()
/usr/bin/indicator-weather:1932: Warning: g_variant_ref: assertion `value->ref_count > 0' failed
  gtk.main()
/usr/bin/indicator-weather:1932: Warning: g_variant_get_type_string: assertion `value != NULL' failed
  gtk.main()
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  20 (X_GetProperty)
  Resource id in failed request:  0x3600259
  Serial number of failed request:  19
  Current serial number in output stream:  19
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  20 (X_GetProperty)
  Resource id in failed request:  0x3600259
  Serial number of failed request:  19
  Current serial number in output stream:  19
```

---

### Post by Toz on 2012-05-17
It looks like it may be this bug: [https://bugs.launchpad.net/weather-indicator/+bug/836741]("https://bugs.launchpad.net/weather-indicator/+bug/836741"). I don't have a solution to recommend, but perhaps you could add your name to the bug report,

---

### Post by rosswmcgee on 2012-05-20
I think I discovered why the weather app would not stay in the 

panel after I removed the indicator msgs. It would work for awhile and then disappear,

and ubuntu would leave an error msg..  Here is what I think the problem is. 

I had in terminal removed the indicator messages after switching to evolution. 

Now that I have restored them, no more problems with the weather indicator, and I am back to using

T-Bird.

---

### Post by rosswmcgee on 2012-05-21
Nope I was wrong. Weather indicator left the panel twice today// along with a 

ubuntu error msg...

---

