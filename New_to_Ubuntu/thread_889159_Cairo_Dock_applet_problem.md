---
title: "Cairo Dock applet problem"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by HittingSmoke on 2008-08-13
I finally got this Cairo Dock running but I cant seem to remove some applets. I cant get rid of the CPU monitor, the weather or the Compiz button. When I try it just crashes and restarts. Same thing happens if I try to clear the check box next to an applet in the config.

I have no idea what this means but here is what shows up in terminal when it crashes

```
cairo_dock_remove_module_instance ()
1 instance(s) a arreter
cairo_dock_deactivate_module_instance_and_unload ()
g_timer_destroy: assertion `timer != NULL' failed
g_hash_table_destroy: assertion `hash_table != NULL' failed
warning :  (cairo-dock.c:_cairo_dock_intercept_signal:277)
  Attention : Cairo-Dock has crashed (sig 11).
It will be restarted now.
Feel free to report this bug on cairo-dock.org to help improving the dock !
cairo_dock_load_gauge (96x96)
cd_cpusage_read_data: assertion `fTimeElapsed > 0.1' failed
warning :  (applet-load-icons.c:_load_icons:91)
  couldn't detect any drives
cairo_dock_fm_add_monitor_full: assertion `cURI != NULL' failed
warning :  (applet-load-icons.c:_load_icons:95)
  Attention : can't monitor drives
warning :  (applet-load-icons.c:_load_icons:139)
  Attention : can't monitor bookmarks
weather : applet : 86bad40, icon : 86aa028, subdock <- 81f0a60
                                                               
```

Its really annoying cause I love this thing but I have some useless icons on there that I dont want and cant get rid of. Any help is appreciated.

I've tried reinstalling it and even deleting the folder for the specific applet that I'm trying to get rid of and nothing works.

---

### Post by fenT1 on 2008-08-13
did you right click on the dock and hit configure?

---

### Post by HittingSmoke on 2008-08-13
Yep. I noticed it because I was playing around and added the Compiz applet and decided I didnt need it. When I tried to remove it the dock crashed and restarted. I also tried going back into the congif and clearing the check box next to it and the same thing happens. Its happening when I try to remove anything other than a launcher.

---

### Post by fabounet on 2008-08-14
you're using the SVN, which has been quite unstable recently due to some deep work on it.
it's becoming stable again, but I would recommend to use the packages on the cairo-dock repository.

---

