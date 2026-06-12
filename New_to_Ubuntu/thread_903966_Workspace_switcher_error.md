---
title: "Workspace switcher error"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by einstein2001 on 2008-08-28
I am having a problem adding the workspace switcher to the gnome panel. I removed the switcher when I was trying the gDesklet switcher then decided to put it back.
Now when I add it to the panel it only shows one window. When i right click>preferences an error window pops up.

An error occurred while loading or saving configuration information for gnome-panel. Some of your configuration settings may not work properly.

Details:
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_workspace_names' specified for `/apps/panel/applets/applet_1/prefs/display_workspace_names' stores a non-schema value
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_all_workspaces' specified for `/apps/panel/applets/applet_1/prefs/display_all_workspaces' stores a non-schema value
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/num_rows' specified for `/apps/panel/applets/applet_1/prefs/num_rows' stores a non-schema value

The option to select "show current workspace or show all workspaces" is greyed out and I cannot change. My number of workspaces is set at 4.

Sound like there is something simple I'm missing here. Please help.

---

### Post by iaculallad on 2008-08-28
Try restoring your panels it if could work:

```
sudo gnome-session-remove gnome-panel
sudo gconftool-2 --recursive-unset /apps/panel
sudo gnome-panel &
```

---

### Post by einstein2001 on 2008-08-28
Error: could not connect to the session manager

---

### Post by Lizard_King on 2008-09-09
I have the same problem.

---

