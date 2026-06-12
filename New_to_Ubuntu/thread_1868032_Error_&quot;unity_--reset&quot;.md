---
title: "Error &quot;unity --reset&quot;"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by Garrote2010r on 2011-10-23
Hi all,

I recently upgraded to 11.10 but I somehow did something that made  my top right menu and unity bar disappear.  I entered the above command but I received an error.  Any help would be appreciated:

```
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : false
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
Initializing gnomecompat options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing move options...done
Initializing snap options...done
Initializing obs options...done
Initializing resize options...done
Initializing place options...done
Initializing grid options...done
Initializing commands options...done
Initializing animation options...done
Initializing wall options...done
Initializing session options...done
Initializing workarounds options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing kdecompat options...[ERROR]: Option "plasma_thumbnails" already defined
[ERROR]: Option "present_windows" already defined
[ERROR]: Option "window_blur" already defined
[ERROR]: Option "sliding_popups" already defined
[ERROR]: Option "slide_in_duration" already defined
[ERROR]: Option "slide_out_duration" already defined
done
Initializing animationaddon options...done
Initializing ezoom options...done
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
Initializing fade options...done
Initializing scale options...done
Setting Update "open_effects"
Setting Update "open_durations"
Setting Update "close_effects"
Setting Update "close_durations"
Setting Update "airplane_path_length"
Setting Update "airplane_fly_to_taskbar"
Setting Update "fire_particles"
Setting Update "fire_size"
Setting Update "fire_slowdown"
Setting Update "fire_color"
Setting Update "fire_direction"
Setting Update "skewer_direction"
Setting Update "skewer_gridx"
Setting Update "skewer_gridy"
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2e00044

```

---

### Post by mahmoud.l on 2011-10-23
I think that's what happened to me, the only thing that i could see is the Nautilus bar, but I could access Ubuntu 2D just fine
Try purging compiz and then reinstalling it

sudo apt-get purge compiz

then

sudo apt-get install compiz

---

### Post by computerandu on 2011-10-23
What happens after a restart?

---

### Post by Garrote2010r on 2011-10-23
> **computerandu said:**
> What happens after a restart?

Nothing is fixed after a restart, still no menus.

---

### Post by mc4man on 2011-10-23
Could you run this in the ubuntu login  - you should be able to get a terminal - try - 
 Crtl+Alt+T
```
cat ~/.config/compiz-1/compizconfig/config
```
If it returns nothing that's fine, otherwise post what is shown

---

### Post by mbelos on 2011-10-23
I had a similar problem this morning. It seemed that Compiz crashed on me and took Unity 3d with it... Here are some of the steps I took to fix it:

[LIST=1]
[*]Move (not copy) your ~/.gconf, ~/.gconfd and ~/.gnome2 to another directory (I suggest a "Backup" folder or something)
[*]Run the following command in a terminal window: ```
killall nautilus
```
[*]Run the following command in a terminal window: ```
unity --reset
```
[/LIST]

I also tried reinstalling "ubuntu-desktop" by doing the following:
```
sudo apt-get install --reinstall ubuntu-desktop
```But I can't remember exactly when I did it. Try the above first then resort to this if needed.

Note that your gconf settings will all be reset, so all of your apps will probably need reconfiguring.

---

### Post by Garrote2010r on 2011-10-23
> **mc4man said:**
> Could you run this in the ubuntu login  - you should be able to get a terminal - try - 
 Crtl+Alt+T
```
cat ~/.config/compiz-1/compizconfig/config
```
If it returns nothing that's fine, otherwise post what is shown

Here is what I got.  I am thinking this problem has to do with my animations also being disabled (I downloaded the GNOME Shell so that's what I'm using now):

```

[gnome_session]
profile = 
backend = ini

[general_ubuntu]
plugin_list_autosort = true
integration = false
profile = 

```

---

### Post by mc4man on 2011-10-24
Go 
```
gedit ~/.config/compiz-1/compizconfig/config
```
Remove all of this, save & exit gedit, the terminal
> [general_ubuntu]
plugin_list_autosort = true
integration = false
profile =

then Ctrl+Alt+delete should give you a log out.
log out & then back into ubuntu session

If not returned to unity then open a terminal again - now this will work
unity --reset

To note - you should be doing this in the **ubuntu** login

---

### Post by Garrote2010r on 2011-10-26
Thank you, mc4man.  Worked perfectly.

---

### Post by Chris Mousset on 2011-10-27
Thanks!

---

### Post by David006 on 2011-11-01
Replacing **~/.config/compiz-1/compizconfig/config** as suggested, only caused worse issues.

That lost me all of Unity, top status, menu bar .. (basically: just wallpaper)


STILL LOOKING for a quick fix when Unity loses its sanity.

---

