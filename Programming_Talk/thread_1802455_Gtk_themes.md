---
title: "Gtk themes"
date: 2011-07-12
forum: Programming Talk
---

### Post by hapyfishrmn on 2011-07-12
Hey all,

 I have been trying to create a GTK theme to work on a Windows 7 machine. I have tried the GTK preference tool a little. But I wanted to create my own. I am able to set the backgound of my window. But when I attempt to assign the background of a button nothing happens? Any help would be greatly appreciated.

```
style "default-style"
{
        bg[NORMAL] = "#FF0000"
	base[NORMAL] = "#0000FF"
        fg[NORMAL] = "#00FF00"
}

widget_class "*.GtkButton.*" style "default-style"



```

---

