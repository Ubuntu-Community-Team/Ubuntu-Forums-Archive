---
title: "Desktop Font Color"
date: 2011-09-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by rabideau on 2011-09-25
Does anyone out there know how to effectively alter the color of the desktop font in 11.10?  Gnome-tweak-tool does not allow for it and gconf & dconf do not seem to offer an easily identified place for that type of entry.

I think you will notice the problem I would like to fix with my desktop via the attached image.

---

### Post by lucazade on 2011-09-25
> **rabideau said:**
> Does anyone out there know how to effectively alter the color of the desktop font in 11.10?  Gnome-tweak-tool does not allow for it and gconf & dconf do not seem to offer an easily identified place for that type of entry.

I think you will notice the problem I would like to fix with my desktop via the attached image.

If you are using a theme different from ambiance or radiance then you need to fix your theme manually. This is due to a recent change in Nautilus.
If you need any pointer look at the latest light-theme release and to its changelog that fix this issue.

---

### Post by areteichi on 2011-10-01
I would like to know how to configure this as well.

I really don't like the way Ubuntu's default font color is not set to black. Even the supposedly black fonts in a document (LO Writer) do not appear black but dark grey. It's even more perplexing that when I actually set the font colors in the document to black, the fonts actually do turn black. It makes me think that the fonts are actually not black in the document.

Anyway, for these reasons, I'd be really nice if I can set the default font color to black in Ubuntu. Any advise is appreciated! :P

---

### Post by Xgen on 2011-10-01
Perhaps this might work. Backup and copy/save this to the bottom of your themes gtk-3.0 gtk-widgets.ccs file. Change the color code to whatever or use a valid color name as in the commented line below it and restart your session. The "active" and "selected" lines might/might not work. Experiment... :)

```
/*######## MODIFY DESKTOP FONT #########*/

/* desktop mode */
.nautilus-desktop.nautilus-canvas-item {
    color: #ffffff;
 /*color: white;*/
    text-shadow: 1 1 alpha (#000000, 0.8);
}

.nautilus-desktop.nautilus-canvas-item:active {
    background-image: none;
    background-color: alpha (@bg_color, 0.84);
    border-radius: 4;

    color: #ffffff;
}

.nautilus-desktop.nautilus-canvas-item:selected {
    background-image: none;
    background-color: alpha (@selected_bg_color, 0.84);
    border-radius: 4;

    color: @selected_fg_color;
}

.nautilus-desktop.nautilus-canvas-item:active,
.nautilus-desktop.nautilus-canvas-item:prelight,
.nautilus-desktop.nautilus-canvas-item:selected {
    text-shadow: none;
}

```

---

### Post by areteichi on 2011-10-02
> **Xgen said:**
> Perhaps this might work. Backup and copy/save this to the bottom of your themes gtk-3.0 gtk-widgets.ccs file. Change the color code to whatever or use a valid color name as in the commented line below it and restart your session. The "active" and "selected" lines might/might not work. Experiment... :)

Thank you very much for your suggestion!! :D

Although I managed to configure the font color settings by modifying different files from the one you named, your suggestion certainly inspired me to look for a solution in that direction!
I was able to change the desktop font color by modifying the following three files.

1. I adjusted the following value contained in the file /usr/share/themes/Ambiance/gtk-3.0/gtk.css:

```
@define-color text_color #000000;
```

2. Then the value in the file /usr/share/themes/Ambiance/gtk-3.0/settings.ini:
```
\ntext_color:#000000
```

3. Lastly /usr/share/themes/Ambiance/gtk-2.0/gtkrc:
```
\ntext_color:#000000
```

(the default value for all three is #3C3C3C)

This seems to have done the job, at least concerning the issue I was worried about. And please excuse me for hijacking the thread.
I'm not sure if the above method helps the OP in any way, but I hope my points were relevant to the discussion :)

---

