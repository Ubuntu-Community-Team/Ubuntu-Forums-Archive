---
title: "Window size annoyance on Eee PC"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by Sii on 2008-08-25
Hi Guys,

While trying to learn how to use Ubuntu, one thing I am finding difficult is the fact that half the time, I can't see the bottom of the window I am trying to work with on the Eee PC.  Dragging or trying to resize doesn't seem to work, and I find myself trying to navigate by 'blind tabbing'.  One example was trying to stop the 'assault' of the Log In sound.  I found the preferences window I needed to work with, but the part I wanted was off the bottom of the screen.  I eventually managed to do it by luck, as I clicked something at the top of the window, which made the top disappear, then by navigating with the Tab key, I managed to get to the right part to configure.  This doesn't seem to be the most effective of navigation methods, so if someone could tell me what I'm doing wrong, it would be appreciated.  :)

Simon.

---

### Post by nonpc on 2008-08-25
Did not really understand, you could make a screenshot.
But if I DIT understand, you can move a window by holding ALT and click and drag. Anywhere on the window. Should help. Or maybe not. You could try resizing so a scrollbar appears.

---

### Post by Sii on 2008-08-25
OK, here's a screenshot.  As can be seen, the Log in option is off the bottom of the screen.  If I try to resize the window goes purple, but the edges don't seem to move, except to expand sideways, which isn't much use.

---

### Post by mellowd on 2008-08-25
I assume you have the 701?

---

### Post by Sii on 2008-08-25
Yes.

---

### Post by slowferrari on 2008-08-25
I'm also having this problem, i managed to get around it by setting my compiz to make windows fullscreen by hitting super+f11 (firefox does it by default just by hitting f11). this is kind of a cheap fix because i have display problems still using this method (if i mouse over a button the whole screen starts flashing, ...n stuff). I'm still hoping to find a better fix. like a way to set my windows to default to 800x480 max. I know its a newb question, but plz halp.

---

### Post by khajavi on 2009-10-16
> **Sii said:**
> OK, here's a screenshot.  As can be seen, the Log in option is off the bottom of the screen.  If I try to resize the window goes purple, but the edges don't seem to move, except to expand sideways, which isn't much use.

I have the same Issue, what should we do?!!

---

### Post by mocoloco on 2009-10-16
> **nonpc said:**
> Did not really understand, you could make a screenshot.
But if I DIT understand, you can move a window by holding ALT and click and drag. Anywhere on the window. Should help. Or maybe not. You could try resizing so a scrollbar appears.

Did you guys see this?  Hold ALT, then you can grab anywhere on the window and move it.

---

### Post by starcannon on 2009-10-16
I have some of the old 7xx series asus eeepc's.
Alt+Mouse drag will let you drag windows off screen so you can see the bottoms; if you want desktop effects turned on you will need to fix a setting in gconf-editor to allow you to drag above the top of the screen:

[LIST=1]
[*]Alt+F2
[LIST=1]
[*]Type: gconf-editor
[*]Go to: /apps/compiz/plugins/move/allscreens/options/constrain_y
[*]Uncheck "constrain_y" option.
[/LIST]
 
[/LIST]
Next, I find it useful to scale the UI size down; there is already a nice little script to do it all for you:
```

#!/bin/sh
# Changes:
# - 20071211 fix volume control to mute on hotkey
#            disabled gnome-brightness related things
# - 20071208 disabled dim screen on AC
#            added gnome notifications for wifi/overclocking
#            options to keep compiz (--compiz)

echo "* Setting smaller font sizes"
gconftool-2 --set /apps/nautilus/preferences/desktop_font --type string "Sans 8"
gconftool-2 --set /desktop/gnome/interface/document_font_name --type string "Sans 8"
gconftool-2 --set /desktop/gnome/interface/font_name --type string "Sans 8"
gconftool-2 --set /apps/metacity/general/titlebar_font --type string "Sans Bold 8"
gconftool-2 --set /desktop/gnome/interface/monospace_font_name --type string "Monospace 9"

echo "* All applications can go fullscreen by hitting <Alt>-F11"
gconftool-2 --set /apps/metacity/window_keybindings/toggle_fullscreen --type string "<Alt>F11"

echo "* Smaller toolbars using icons only"
gconftool-2 --set /desktop/gnome/interface/toolbar_style --type string "icons"

echo "* Disabling UI sounds"
gconftool-2 --set /desktop/gnome/sound/event_sounds --type bool 0

echo "* Fixing the mute key"
gconftool-2 --set /desktop/gnome/sound/default_mixer_tracks --type list --list-type string "[PCM]"

echo "* Fixing vfat mounting when using kernel 2.6.21.4-eee"
gconftool-2 --set /system/storage/default_options/vfat/mount_options --type list --list-type string "[shortname=mixed,uid=,utf8,umask=077,exec]"

echo "* Setting suspend when closing lid, blank screen"
gconftool-2 --set /apps/gnome-power-manager/actions/sleep_type_battery --type string "suspend"
gconftool-2 --set /apps/gnome-power-manager/actions/sleep_type_ac --type string "suspend"
gconftool-2 --set /apps/gnome-power-manager/buttons/lid_battery --type string "suspend"
gconftool-2 --set /apps/gnome-power-manager/buttons/lid_ac --type string "blank"
gconftool-2 --set /apps/gnome-power-manager/timeout/sleep_computer_ac --type int 0
gconftool-2 --set /apps/gnome-power-manager/timeout/sleep_computer_battery --type int 300
gconftool-2 --set /apps/gnome-power-manager/timeout/sleep_display_ac --type int 300
gconftool-2 --set /apps/gnome-power-manager/timeout/sleep_display_battery --type int 60
#gconftool-2 --set /apps/gnome-power-manager/backlight/brightness_ac --type int 85
#gconftool-2 --set /apps/gnome-power-manager/backlight/idle_dim_ac --type bool 1
#gconftool-2 --set /apps/gnome-power-manager/backlight/idle_dim_battery --type bool 1

echo "* Do not display the battery warning"
gconftool-2 --set /apps/gnome-power-manager/notify/low_capacity --type bool 0

#if [ "x$1" != "x--compiz" ]
#then
#echo "* Disabling desktop effects"
#gconftool-2 --type string --set /apps/gnome-session/rh/window_manager &#8220;metacity&#8221;
#metacity --replace &
#fi

echo "* Unconstraining windows to the top of the screen"
gconftool-2 --type bool --set /apps/compiz/plugins/move/allscreens/options/constrain_y 0

echo "* Installing OSD notifications for wifi and overclocking"
gconftool-2 --set /apps/metacity/keybinding_commands/command_9 --type string "/etc/acpi/notify-overclock.py off"
gconftool-2 --set /apps/metacity/keybinding_commands/command_10 --type string "/etc/acpi/notify-overclock.py on"
gconftool-2 --set /apps/metacity/keybinding_commands/command_11 --type string "/etc/acpi/notify-wifi.py off"
gconftool-2 --set /apps/metacity/keybinding_commands/command_12 --type string "/etc/acpi/notify-wifi.py on"
gconftool-2 --set /apps/metacity/global_keybindings/run_command_9 --type string "XF86Launch4"
gconftool-2 --set /apps/metacity/global_keybindings/run_command_10 --type string "XF86Launch3"
gconftool-2 --set /apps/metacity/global_keybindings/run_command_11 --type string "XF86Launch2"
gconftool-2 --set /apps/metacity/global_keybindings/run_command_12 --type string "XF86Launch1"
echo "Done."

```You may save that code as an shell script, or save the attachment I am putting in with this post.

Be sure to go to [http://array.org/ubuntu/](http://array.org/ubuntu/) and get the custom kernel, it is well worth it; I also have mine set up to set the front side bus up to allow full CPU speed, a raging 900mhz :) I can post a tutorial on that as well if needed.
Enjoy.

P.S.
I did not write this script, it was part of a now defunct script pack that I got from Google Code: [http://code.google.com/p/eee-ubuntu-support/](http://code.google.com/p/eee-ubuntu-support/)

---

### Post by winotree on 2009-10-16
Make that **alt+left click** and then drag anywhere on the window...  :)  That technique has worked well for two years on *this* 701 model.

EDIT - oh, lots of info added just above while doing a spell check -- have to bookmark and read it later.

---

### Post by kerry_s on 2009-10-16
i would use maximus, it will maximize all windows to the screen.

---

### Post by starcannon on 2009-10-16
Hey there, I forgot to mention that I also use the Littlefox theme for Firefox on my 701 and 702.
[https://addons.mozilla.org/en-US/firefox/addon/307](https://addons.mozilla.org/en-US/firefox/addon/307)

Enjoy.

---

