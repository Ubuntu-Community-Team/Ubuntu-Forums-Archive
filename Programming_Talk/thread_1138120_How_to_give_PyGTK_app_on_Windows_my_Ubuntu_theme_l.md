---
title: "How to give PyGTK app on Windows my Ubuntu theme look?"
date: 2009-04-26
forum: Programming Talk
---

### Post by FalFire on 2009-04-26
I want my PyGTK app to have the same look on windows as on my Ubuntu box. Is there a way to make it look like the custom theme I am using on Ubuntu (Gnome) by making a gtkrc file out of it? If I go to /home/myuser/.themes/mycustomtheme/index.theme then this is the information inside the file:

```
[Desktop Entry]
Name=Custom Dust
Type=X-GNOME-Metatheme
Comment=

[X-GNOME-Metatheme]
GtkTheme=New Wave
MetacityTheme=Dust
IconTheme=Human
GtkColorScheme=fg_color:#101010101010,bg_color:#d999d999d999,text_color:#1a1a1a1a1a1a,base_color:#e666e666e666,selected_fg_color:#1a1a1a1a1a1a,selected_bg_color:#ffff8f8f4c4c,tooltip_fg_color:#333306060606,tooltip_bg_color:#ffffe6e6c4c4
CursorTheme=whiteglass
CursorSize=16
```

Where is the other information about this theme stored? If I go to C:/locationofgtk/share/themes in Windows then there are different folders with gtkrc files in them. I want to make such a file out of my Ubuntu theme.

---

