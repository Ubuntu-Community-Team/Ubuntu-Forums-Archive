---
title: "Substitute for Aero Snap using Compiz Grid plugin"
date: 2010-05-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Old Marcus on 2010-05-04
I did see a solution on OMG!Ubuntu for doing this with the mouse, but it doesn't work very well if you use the edges of the screen for swapping workspaces or dragging windows to other workspaces. Instead I found a solution using the keyboard, which IMO is much neater. This may already be posted, but I felt I ought to add it for the Windows 7 users who want the same functionality on Ubuntu.

First, fire up the compizconfig settings manager (Preferences>CompizConfig Settings Manager) or install it in the terminal with:
```
sudo apt-get install compizconfig-settings-manager
```
If you don't already have it.

Then scroll down to the bottom of the selection and enable the grid plugin here:
[[IMG]http://i48.photobucket.com/albums/f217/Blob809/th_compiz1.png[/IMG]](http://s48.photobucket.com/albums/f217/Blob809/?action=view&current=compiz1.png)

You can view the defaults and change them once you click on the plugin button:
[[IMG]http://i48.photobucket.com/albums/f217/Blob809/th_compiz2.png[/IMG]](http://s48.photobucket.com/albums/f217/Blob809/?action=view&current=compiz2.png)

If on default, when you press Ctrl+Alt+KP4 or Ctrl+Alt+KP6 the active window will be sent to the left or the right of the screen respectively, and resized to half the width of the screen:
[[IMG]http://i48.photobucket.com/albums/f217/Blob809/th_compizgrideffect.png[/IMG]](http://s48.photobucket.com/albums/f217/Blob809/?action=view&current=compizgrideffect.png)

Again, hope this hasn't already been posted, but I discovered it (along with a million others no doubt :P) and felt I ought to share. :)

---

### Post by Bonster on 2010-05-04
if you like that you might like this even better

> grid plugin with hot corners
[http://www.youtube.com/watch?v=XvlTlyEasD8](http://www.youtube.com/watch?v=XvlTlyEasD8)

---

### Post by johnwillis on 2010-05-14
This has also been posted here:

[http://john-willis.com/2010/05/windows-7-snapping-windows-in-ubuntu-compiz/]("http://john-willis.com/2010/05/windows-7-snapping-windows-in-ubuntu-compiz/")

It is an awesome plugin and like the previous poster stated much better in my opinion than W7 - it's quicker to use the keyboard!

Regards,

John

---

### Post by stobbsm on 2010-05-14
I don't have that option in my ccsm. How do I go about getting it?

Is there an upgrade for the ccsm package that just isn't showing up on my system?

---

### Post by Bonster on 2010-05-14
> **stobbsm said:**
> I don't have that option in my ccsm. How do I go about getting it?

Is there an upgrade for the ccsm package that just isn't showing up on my system?

U have to install the compiz plugin extras

---

### Post by Bonster on 2010-05-14
> **johnwillis said:**
> This has also been posted here:

[http://john-willis.com/2010/05/windows-7-snapping-windows-in-ubuntu-compiz/]("http://john-willis.com/2010/05/windows-7-snapping-windows-in-ubuntu-compiz/")

It is an awesome plugin and like the previous poster stated much better in my opinion than W7 - it's quicker to use the keyboard!

Regards,

John


Keyboard might be alright if u dont use the default they got. The default keys require you to use two hands -- thats a waste of time, lifting and going back to the mouse to focus the next window you want to tile.

Thus tiling with the mouse is more efficient for me. Just Focus on the window and click on hot corner.

But is a user preference at the end of the day

---

### Post by tweakt on 2010-10-31
Hey guys, I took the time to automate the setup of the Grid plugin, also using the Commands plugin to provide for mouse-click control over the grid commands. 

It was first described here:
[http://www.youtube.com/watch?v=XvlTlyEasD8](http://www.youtube.com/watch?v=XvlTlyEasD8)

This script sets it all up automatically. The one issue to be aware of though is that it will reset the 'active' status of other plugins. If anyone can modify it to simply add "Grid" and "Commands" to the active_plugins list (2nd line), that would be awesome!

```

#!/bin/sh

apt-get install compizconfig-settings-manager compiz-fusion-plugins-extra xautomation
gconftool-2 --set --type list --list-type string /apps/compiz/general/allscreens/options/active_plugins [grid,commands]
gconftool-2 --set --type string /apps/metacity/keybinding_commands/command_1 "xte 'keydown Control_L' 'keydown Alt_L' 'key KP_4' 'keyup Control_L' 'keyup Alt_L'"
gconftool-2 --set --type string /apps/metacity/keybinding_commands/command_2 "xte 'keydown Control_L' 'keydown Alt_L' 'key KP_6' 'keyup Control_L' 'keyup Alt_L'"
gconftool-2 --set --type string /apps/metacity/keybinding_commands/command_3 "xte 'keydown Control_L' 'keydown Alt_L' 'key KP_7' 'keyup Control_L' 'keyup Alt_L'"
gconftool-2 --set --type string /apps/metacity/keybinding_commands/command_4 "xte 'keydown Control_L' 'keydown Alt_L' 'key KP_9' 'keyup Control_L' 'keyup Alt_L'"
gconftool-2 --set --type string /apps/metacity/keybinding_commands/command_5 "xte 'keydown Control_L' 'keydown Alt_L' 'key KP_1' 'keyup Control_L' 'keyup Alt_L'"
gconftool-2 --set --type string /apps/metacity/keybinding_commands/command_6 "xte 'keydown Control_L' 'keydown Alt_L' 'key KP_3' 'keyup Control_L' 'keyup Alt_L'"
gconftool-2 --set --type string /apps/compiz/plugins/commands/allscreens/options/run_command0_button '<LeftEdge>Button1'
gconftool-2 --set --type string /apps/compiz/plugins/commands/allscreens/options/run_command1_button '<RightEdge>Button1'
gconftool-2 --set --type string /apps/compiz/plugins/commands/allscreens/options/run_command2_button '<TopLeftEdge>Button1'
gconftool-2 --set --type string /apps/compiz/plugins/commands/allscreens/options/run_command3_button '<TopRightEdge>Button1'
gconftool-2 --set --type string /apps/compiz/plugins/commands/allscreens/options/run_command4_button '<BottomLeftEdge>Button1'
gconftool-2 --set --type string /apps/compiz/plugins/commands/allscreens/options/run_command5_button '<BottomRightEdge>Button1'



```

---

