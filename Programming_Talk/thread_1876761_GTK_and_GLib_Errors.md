---
title: "GTK and GLib Errors"
date: 2011-11-06
forum: Programming Talk
---

### Post by shashank86 on 2011-11-06
Hello,

On running the following command

```


bitbake -c menuconfig virtual/kernel


```

I end up with the following errors

```


Log data follows:
| + do_menuconfig
| + export 'TERMWINDOWTITLE=linux-omap-psp Configuration'
| + TERMWINDOWTITLE='linux-omap-psp Configuration'
| + export 'SHELLCMDS=make menuconfig'
| + SHELLCMDS='make menuconfig'
| + gnome-terminal --disable-factory -t 'linux-omap-psp Configuration' -x make menuconfig
| 
| (gnome-terminal:10922): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1230:46: Couldn't recognize the image file format for file '/usr/share/themes/Ambiance/gtk-3.0/assets/slider.png'
| 
| (gnome-terminal:10922): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1234:55: Couldn't recognize the image file format for file '/usr/share/themes/Ambiance/gtk-3.0/assets/slider_prelight.png'
| 
| (gnome-terminal:10922): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1238:55: Couldn't recognize the image file format for file '/usr/share/themes/Ambiance/gtk-3.0/assets/slider_vertical.png'
| 
| (gnome-terminal:10922): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1242:64: Couldn't recognize the image file format for file '/usr/share/themes/Ambiance/gtk-3.0/assets/slider_prelight_vertical.png'
| 
| (gnome-terminal:10922): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1298:73: Couldn't recognize the image file format for file '/usr/share/themes/Ambiance/gtk-3.0/assets/scrollbar_handle_vertical.png'
| 
| (gnome-terminal:10922): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1315:64: Couldn't recognize the image file format for file '/usr/share/themes/Ambiance/gtk-3.0/assets/scrollbar_handle.png'
| 
| (gnome-terminal:10922): GLib-GIO-CRITICAL **: Settings schema 'org.gnome.system.proxy' is not installed
| 
| 
| (gnome-terminal:10922): GLib-GIO-CRITICAL **: Settings schema 'org.gnome.desktop.interface' is not installed
| 
| 
| (gnome-terminal:10922): GLib-GIO-CRITICAL **: g_settings_get_key_info: assertion `settings->priv->schema != NULL' failed
| 
| (gnome-terminal:10922): GLib-CRITICAL **: g_variant_get_va: assertion `value != NULL' failed
| 
| (gnome-terminal:10922): GLib-CRITICAL **: g_variant_unref: assertion `value != NULL' failed
| 
| (gnome-terminal:10922): Pango-CRITICAL **: pango_font_description_from_string: assertion `str != NULL' failed
| **
| ERROR:terminal-app.c:1450:terminal_app_init: assertion failed: (app->system_font_desc != NULL)
| /home/embedded/bb/build/tmp-angstrom_2008_1/work/beagleboard-angstrom-linux-gnueabi/linux-omap-psp-2.6.32-r100g+gitr5fc29e7b2a76a64a739f857858ef0b98294aa155/temp/run.do_menuconfig.10920: line 94: 10922 Aborted                 gnome-terminal --disable-factory -t "$TERMWINDOWTITLE" -x $SHELLCMDS
NOTE: package linux-omap-psp-2.6.32-r100g+gitr5fc29e7b2a76a64a739f857858ef0b98294aa155: task do_menuconfig: Failed
ERROR: Function 'do_menuconfig' failed (see /home/embedded/bb/build/tmp-angstrom_2008_1/work/beagleboard-angstrom-linux-gnueabi/linux-omap-psp-2.6.32-r100g+gitr5fc29e7b2a76a64a739f857858ef0b98294aa155/temp/log.do_menuconfig.10920 for further information)
ERROR: Task 7 (/home/embedded/bb/sources/openembedded/recipes/linux/linux-omap-psp_2.6.32.bb, do_menuconfig) failed with exit code '1'
ERROR: '/home/embedded/bb/sources/openembedded/recipes/linux/linux-omap-psp_2.6.32.bb' failed
embedded@embedded-VirtualBox:~/bb$ 



```

I gathered that this is an issue with the OS from [askubuntu](http://askubuntu.com/questions/74075/gtk-glib-errors)

Running the solution proposed on [askubuntu](http://askubuntu.com/questions/74075/gtk-glib-errors) ran into the same errors. Can this be circumnavigated or do i have to run on a 11.04 installation?

My current setup is:

OS : Oneiric Ocelot 11.10
VM : VirtuaBox

Thanks,
Shashank

---

### Post by crdlb on 2011-11-06
The settings schema errors are probably caused by not having gsettings-desktop-schemas installed. That's a dependency of the gnome-terminal package, so I'm not sure how that could happen.

I'm not entirely sure what's causing the theme parsing errors, but you could try: ```
sudo apt-get --reinstall install libgdk-pixbuf2.0-0
```

Are you using GNOME (including Unity), or some other desktop enviroment?

---

### Post by forumcash on 2012-04-13
I have same error after upgrade. Last time, I fixed by a command. I don't remember that, but problem was apps use old library. If somebody can tell, it will work. Following command doesn't work

> **crdlb said:**
> ```
sudo apt-get --reinstall install  libgdk-pixbuf2.0-0
```

---

### Post by cmcanulty on 2012-08-07
I have same issue started today
```
(nautilus:7606): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:62:15: Not using units is deprecated. Assuming 'px'.

```

---

