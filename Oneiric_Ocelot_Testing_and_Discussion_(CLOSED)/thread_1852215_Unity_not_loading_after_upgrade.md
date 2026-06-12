---
title: "Unity not loading after upgrade"
date: 2011-09-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by scott.smedley on 2011-09-29
Just ran an upgrade, compiz crashed and now unity won't load (just shows the menu bar for nautilus). 

I opened a terminal and ran "sudo unity --reset" and got the following output:

WARNING: no current gconf profile set, assuming unity
WARNING: Unity currently default profile, so switching to metacity while resetting the values

(metacity:3665): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...[ERROR]: Option "avoid_snap" already defined
[ERROR]: Option "snap_type" already defined
[ERROR]: Option "edges_categories" already defined
[ERROR]: Option "resistance_distance" already defined
[ERROR]: Option "attraction_distance" already defined
done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...[ERROR]: Option "next_button" already defined
[ERROR]: Option "next_key" already defined
[ERROR]: Option "prev_button" already defined
[ERROR]: Option "prev_key" already defined
[ERROR]: Option "next_all_button" already defined
[ERROR]: Option "next_all_key" already defined
[ERROR]: Option "prev_all_button" already defined
[ERROR]: Option "prev_all_key" already defined
[ERROR]: Option "next_group_button" already defined
[ERROR]: Option "next_group_key" already defined
[ERROR]: Option "prev_group_button" already defined
[ERROR]: Option "prev_group_key" already defined
[ERROR]: Option "next_no_popup_button" already defined
[ERROR]: Option "next_no_popup_key" already defined
[ERROR]: Option "prev_no_popup_button" already defined
[ERROR]: Option "prev_no_popup_key" already defined
[ERROR]: Option "next_panel_button" already defined
[ERROR]: Option "next_panel_key" already defined
[ERROR]: Option "prev_panel_button" already defined
[ERROR]: Option "prev_panel_key" already defined
[ERROR]: Option "speed" already defined
[ERROR]: Option "timestep" already defined
[ERROR]: Option "window_match" already defined
[ERROR]: Option "minimized" already defined
[ERROR]: Option "auto_change_vp" already defined
[ERROR]: Option "popup_delay" already defined
[ERROR]: Option "mouse_select" already defined
[ERROR]: Option "saturation" already defined
[ERROR]: Option "brightness" already defined
[ERROR]: Option "opacity" already defined
[ERROR]: Option "icon" already defined
[ERROR]: Option "icon_only" already defined
[ERROR]: Option "mipmap" already defined
[ERROR]: Option "row_align" already defined
[ERROR]: Option "focus_on_switch" already defined
[ERROR]: Option "bring_to_front" already defined
[ERROR]: Option "highlight_mode" already defined
[ERROR]: Option "highlight_rect_hidden" already defined
[ERROR]: Option "highlight_color" already defined
[ERROR]: Option "highlight_border_color" already defined
[ERROR]: Option "highlight_border_inlay_color" already defined
done
Initializing resize options...done
Initializing fade options...done
Initializing scale options...done
Initializing session options...done
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"


Any idea what is wrong and how I can fix? Thanks.

---

### Post by Larkspur on 2011-09-29
Just had a similar thing happen.  All I did was keep on restarting (ctrl+alt+delete) until Unity came back, which it has.  For now . . .

Does anyone use the top-left corner to reveal the launcher bar?  If so, have you found that, after the latest upgrade, that corner doesn't seem to work in the way it used to?

---

### Post by scott.smedley on 2011-09-29
> **Larkspur said:**
> Just had a similar thing happen.  All I did was keep on restarting (ctrl+alt+delete) until Unity came back, which it has.  For now . . .

Does anyone use the top-left corner to reveal the launcher bar?  If so, have you found that, after the latest upgrade, that corner doesn't seem to work in the way it used to?

Thanks Larkspur, but already tried restarting numerous times. Have also uninstalled and reinstalled both unity and compiz to no avail. Very very frustrating. How is it that Gnome 3 is extremely stable while Unity is full of so many pitfalls this close to release?

---

### Post by xyzzyman on 2011-09-29
Have you tried ctrl-alt-t for a terminal, ccsm and re-enable the unity plugin? Just fixed it for me.

---

### Post by RomeReactor on 2011-09-29
Hi. Maybe the Unity plugin has been disabled. Try installing compizconfig-settings-manager:
```
sudo apt-get install compizconfig-settings-manager
```
and then run it:
```
ccsm
```
to see if the plugin is disbled, in which case check it's box and follow the prompts (if any).

EDIT: Yeah, what xyzzyman said.

---

### Post by cariboo on 2011-09-29
> **Larkspur said:**
> Just had a similar thing happen.  All I did was keep on restarting (ctrl+alt+delete) until Unity came back, which it has.  For now . . .

Does anyone use the top-left corner to reveal the launcher bar?  If so, have you found that, after the latest upgrade, that corner doesn't seem to work in the way it used to?

This hasn't worked for a couple of weeks, if you've kept up-to-date and are using a relatively up-to-date server.

---

### Post by scott.smedley on 2011-09-30
Thanks xyzzyman and RomeReactor.

Unity started working again, although alignment of the desktop was way off. This was solved though when I ran an update.

---

### Post by pkg9991 on 2011-09-30
try sudo apt-get dist-upgrade --fix-missing

---

