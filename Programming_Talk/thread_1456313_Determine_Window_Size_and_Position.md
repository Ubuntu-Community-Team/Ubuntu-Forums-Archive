---
title: "Determine Window Size and Position"
date: 2010-04-17
forum: Programming Talk
---

### Post by DBQ on 2010-04-17
Hi everybody.  Is there a way in Ubuntu to determine the X,Y coordinates of a window on the screen and its size? Thank You!

---

### Post by byStanderone on 2010-04-17
...hi,
i just hope you are not in some kind of programming..lolo, cause all i can suggest at the moment is gimp image editor, have an image scaling feature, perhaps it would serve the purpose.

---

### Post by cdekter on 2010-04-17
There are multiple ways to do this. Maybe if you give some more background information you'll get a specific answer...

---

### Post by DBQ on 2010-04-19
>There are multiple ways to do this. Maybe if you give some more >background information you'll get a specific answer...

I need to be able to locate a window coordinates and size. What are some of these ways? I prefer to stick to the X Sever methods (if possible), but if not any method will do.

I prefer to do it programmatically (from C, perl or what not).  If this is not possible, any way will do.

---

### Post by kaibob on 2010-04-19
> **DBQ said:**
> Hi everybody.  Is there a way in Ubuntu to determine the X,Y coordinates of a window on the screen and its size? Thank You!

I don't know anything about the C or perl programming languages. I'm sure someone will be able to help you with that.

In the any-way-will-do category, you can use the wmctrl utility. Columns 3 to 6 contain x-offset, y-offset, width, and height. For example,

```
$ wmctrl -G -l
0x01200003 -1 0    1984 1280 32   dell Bottom Expanded Edge Panel
0x01200026 -1 0    0    1280 34   dell Top Expanded Edge Panel
0x01a0001c -1 0    0    1280 1024 dell x-nautilus-desktop
0x02000004  0 269  204  801  662  dell Bash Terminal Window
0x01a007b1  0 76   166  1150 700  dell autosave - File Browser
```

The xwininfo utility will provide pretty much the same information.

---

### Post by DBQ on 2010-04-19
Also, is there any way to hide a window?

---

### Post by cdekter on 2010-04-19
I would look into wcmtrl as posted above. It can do everything you have requested so far.

---

### Post by DBQ on 2010-04-19
I already tried to using wmctrl. However, it does not provide functionality for completely hiding a given window. Any other ideas?

Thank you.

---

### Post by nikefalcon on 2011-02-04
Try xdotool:
```
sudo apt-get install xdotool
man xdotool
```

---

