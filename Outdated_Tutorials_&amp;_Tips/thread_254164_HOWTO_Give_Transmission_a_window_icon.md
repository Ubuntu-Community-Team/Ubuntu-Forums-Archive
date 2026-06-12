---
title: "HOWTO: Give Transmission a window icon"
date: 2006-09-09
forum: Outdated Tutorials &amp; Tips
---

### Post by mynimal on 2006-09-09
Here's how you add a window icon to Transmission. I don't know how to make a patch but it's all pretty painless.

[list]
[*] Download the Transmission source
[*] In the gtk directory, open main.c with gedit or whatever
[*] Find this line: "gtk_window_resize(GTK_WINDOW(wind), width, height);"
[*] Below that line, add: "gtk_window_set_icon_name(GTK_WINDOW(wind), "stock_internet");"
[/list]

This will set the window icon to the icon for the "Internet" category for whatever icon theme you use.

[img]http://img525.imageshack.us/img525/819/screenshottransmissionib1.png[/img]

---

### Post by Xilon on 2006-10-04
Awesome, I'm kind of new to programming and the way linux handles images, so if I wanted to use FOOOD's transmission icon (png) how would I do that?
```
gtk_window_set_icon_name(GTK_WINDOW(wind), "./res/transmission.png");
```??

---

### Post by mynimal on 2006-10-05
Sorry, I don't think I can answer that. You can try a direct path though. This is about as far as I've gotten into C programming.

---

### Post by kpolice on 2006-10-06
I have the answer, just copy your icon to /usr/share/pixmaps and name the icon for example transmission-gtk.png

and then just use the code that mynimal wrote but instead of 

```
gtk_window_set_icon_name(GTK_WINDOW(wind), "stock_internet");
```

use:
```
gtk_window_set_icon_name(GTK_WINDOW(wind), "transmission-gtk");
```

---

### Post by Xilon on 2006-10-09
That didn't seem to work, and for the last half hour I've been trying to get gtk_window_set_icon() and gdk_pixbuf_new_from_file() to work... oh well

Anyway here's a patch that does what mynimal's post says... just type ```
patch path/to/transmission/source/gtk/main.c < window_icon_stock.txt
``` and re-compile. Much faster than scrolling down to like 367 and adding the text by hand :P

---

### Post by kpolice on 2006-10-16
Nevermind, the icon should be in your icon theme folder. For example in my case:

/home/kp/.icons/OSX/scalable/apps/transmission-gtk.png

Just look my attachment, using beryl with the scale plugin. I don't have an icon in the titlebar because I don't like them but the scale plugin shows the titlebar icon:

[[IMG]http://img261.imageshack.us/img261/5679/transmissionxs8.png[/IMG]](http://imageshack.us)

---

### Post by MaX on 2008-04-08
So who has reported a bug on this in Launchpad?
It's for sure a bug that the main torrent program of a distro doesn't have a window icon.

---

### Post by andrewsomething on 2008-04-08
[https://bugs.edge.launchpad.net/ubuntu/+source/transmission/+bug/192945](https://bugs.edge.launchpad.net/ubuntu/+source/transmission/+bug/192945)

---

