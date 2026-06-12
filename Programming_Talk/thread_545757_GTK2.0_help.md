---
title: "GTK2.0 help"
date: 2007-09-08
forum: Programming Talk
---

### Post by isaacj87 on 2007-09-08
I have a custom .gtkrc2.0 file for pidgin to display a background image within pidgin's window. 

Here's the gtkrc file

```

pixmap_path "/home/isaac/Pictures/Extras"
style "my-blist" {
bg_pixmap[NORMAL] = "pidgin_bg.jpg"
text[NORMAL] = "#000000"
bg[NORMAL] = "#F5D8BC"
base[NORMAL] = "#F5D8BC"
GtkTreeView::odd_row_color = ""
GtkTreeView::even_row_color = ""
}
widget "*pidgin_blist_treeview" style "my-blist"

```

The problem is that bg_pixmap tiles the image so when I scroll down my buddy list the image becomes distorted (it's like it is overlapping itself). I was looking at the GTK2.0 documentation but I couldn't any about un-tiling the image. I would like to make it static regardless of scrolling, I guess everytime I scroll it's like the picture is shifting down to accommodate, it's leaving a trail behind...Can someone help me out?

---

### Post by isaacj87 on 2007-09-08
Maybe I should phrase this better. The image I've set is a 300x750 jpg...So there's plenty of space to scroll before the image starts over, I'm wanting to keep the image fixed so that when I scroll, I'm just looking at a different part of the image. Not the background constantly trying to reposition itself everytime I move down and up, which is causing a trail-like effect.

I put some screenshots up to better illustrate my point.

the first one is correct obviously.

---

### Post by isaacj87 on 2007-09-08
bump...is there no one that knows? I find that hard to believe! :)

---

