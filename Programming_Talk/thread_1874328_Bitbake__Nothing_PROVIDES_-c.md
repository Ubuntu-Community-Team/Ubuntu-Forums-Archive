---
title: "Bitbake : Nothing PROVIDES -c"
date: 2011-11-02
forum: Programming Talk
---

### Post by shashank86 on 2011-11-02
Hello,

I am trying to cross compile an Angstrom Distro on my ubuntu 11.10. Once the toolchain and the kernel have been downloaded, i need to run

```


bitbake virtual/kernel -c menuconfig


```

However i get the following errors after the cache loads:
```


ERROR: Nothing PROVIDES '–c'
ERROR: Command execution failed: Traceback (most recent call last):
  File "/home/embedded/bb/sources/bitbake/lib/bb/command.py", line 102, in runAsyncCommand
    commandmethod(self.cmds_async, self, options)
  File "/home/embedded/bb/sources/bitbake/lib/bb/command.py", line 200, in buildTargets
    command.cooker.buildTargets(pkgs_to_build, task)
  File "/home/embedded/bb/sources/bitbake/lib/bb/cooker.py", line 753, in buildTargets
    taskdata.add_provider(localdata, self.status, k)
  File "/home/embedded/bb/sources/bitbake/lib/bb/taskdata.py", line 353, in add_provider
    self.add_provider_internal(cfgData, dataCache, item)
  File "/home/embedded/bb/sources/bitbake/lib/bb/taskdata.py", line 373, in add_provider_internal
    raise bb.providers.NoProvider(item)
NoProvider: –c



```

I assume this would be an issue with bitbake as the -c switch is not being handled. I could not find any documents that i could rely on. Was wondering if someone familiar could help.

Thanks

---

### Post by shashank86 on 2011-11-05
^ bounce ^ [hope bouncing threads is legal on this forum]

Thanks.

---

### Post by CharlesA on 2011-11-05
Moved to PT.

---

### Post by ofnuts on 2011-11-05
There is  a long standing tradition in Linux utilities to have the flags first and the name of the file on which the command runs last, and bitbake doesn't see to be an exception to this rule according to [http://bitbake.berlios.de/manual/ch04s02.html#id870093](http://bitbake.berlios.de/manual/ch04s02.html#id870093)

Did you try this: "bitbake -c menuconfig virtual/kernel" ?

---

### Post by shashank86 on 2011-11-05
Thanks ofnuts. That got me ahead. 
Also, now i am running into an issue with xterm if i am not mistaken!

The log data after the last task run (362 : do_menuconfig) :

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

From what i know, after the bitbake menuconfig command is run, a terminal with configuration options should be activated. I assume, the background tasks are done, but the issue with xterm might be holding the terminal from being rendered.

Thanks.

---

