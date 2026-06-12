---
title: "xfce recent files"
date: 2014-11-28
forum: New to Ubuntu
---

### Post by Kevin McCready on 2014-11-28
I find the 'recent files' facility pretty random.

Is there a way I can set it to always point to /Documents and show the last 50 files?

---

### Post by slickymaster on 2014-11-28
xfce4-places-plugin lists files from **~/local/share/recently-used.xbel** which is used by most of GTK apps and I don't think you can change its behavior.

---

### Post by Toz on 2014-11-28
For gtk2 apps, you can tweak some of the gtkfilechooser settings. (See ["Configuration Options"]("https://developer.gnome.org/gtk2/stable/GtkFileChooser.html")).

The config file is located at ~/.config/gtk-2.0/gtkfilechooser.ini. You can change:
[LIST=1]
[*]"SortColumn=modified" & "SortOrder=descending" (to sort the file list based on the last modified (most recent) date)
 
[*]"StartupMode=cwd" (to default to the current working directory instead of the recent files list). 
This doesn't get you to ~/Documents though unless you start the program from within the ~/Documents directory (e.g. terminal) or change the Exec line in the program's desktop file to start in the Documents folder (e.g. Exec=bash -c "cd ~/Documents && mousepad %F").
[/LIST]

One caveat though, I find the implementation buggy (at least on my system). Something keeps resetting this file and I haven't figured out what it is yet.

File contents:
```
[Filechooser Settings]
LocationMode=filename-entry
ShowHidden=true
ShowSizeColumn=true
GeometryX=646
GeometryY=68
GeometryWidth=720
GeometryHeight=540
SortColumn=modified
SortOrder=descending
StartupMode=cwd

```

EDIT: For GTK3 apps, the settings are configured through dconf at org.gtk.settings.file-chooser. You can use the dconf-editor (or gsettings commands) to get/set these values.

---

