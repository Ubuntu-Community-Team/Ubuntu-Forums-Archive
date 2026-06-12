---
title: "[SOLVED] How Do I Change the Color of Text on a Panel?"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by bobsmith2 on 2008-09-16
I have a panel running across the bottom of my screen (I moved the top panel to the bottom). I want it to be a very dark blue - like my desktop. However, I can't read the clock or the minimized program buttons if I make a dark background. Is there a way to change the color of text on a panel from black to white? Thanks.

---

### Post by Pro-reason on 2008-09-16
I believe that such colours are governed by themes.

---

### Post by mike1234 on 2008-09-16
> **bobsmith2 said:**
> I have a panel running across the bottom of my screen (I moved the top panel to the bottom). I want it to be a very dark blue - like my desktop. However, I can't read the clock or the minimized program buttons if I make a dark background. Is there a way to change the color of text on a panel from black to white? Thanks.


 Right click on your desktop select "change desktop background" -> theme tab -> customize -> select "colors" tab. This allows you to modify your theme. Note: some themes can't be modified.

M.

---

### Post by bobsmith2 on 2008-09-16
Thanks Pro-reason and mike1234. One more question... I don't like any of the default themes that come with Ubuntu 8.04. After reading your comments I found my way to gnome-look.org. There's a ton of stuff available there, but I don't know what it all means. For example, I found a theme I really like (Shiki-Colors) under the heading "GTK 2.X". I don't know what that is. There's also a "GTK 1.X", and Metacity, and Compiz - all of them have themes. Can I use any of those? All of those? If I download them and install them, will they appear in the list of themes available when I right click the desktop? Your help is greatly appreciated.

---

### Post by frankleeee on 2008-09-17
If your talking about the desktop applications panels you can change the color by right clicking on properties then backgrounds then tick solid color then tick on the bar and set your color with the color wheel. If your using Hardy you can install gnome color chooser from synaptic and do a bunch of changing including the drop down menus and folders on the desktop as well as the color when your cursor crosses a application or folder.

---

### Post by mike1234 on 2008-09-17
> **bobsmith2 said:**
> Thanks Pro-reason and mike1234. One more question... I don't like any of the default themes that come with Ubuntu 8.04. After reading your comments I found my way to gnome-look.org. There's a ton of stuff available there, but I don't know what it all means. For example, I found a theme I really like (Shiki-Colors) under the heading "GTK 2.X". I don't know what that is. There's also a "GTK 1.X", and Metacity, and Compiz - all of them have themes. Can I use any of those? All of those? If I download them and install them, will they appear in the list of themes available when I right click the desktop? Your help is greatly appreciated.

 Metacity is standard Ubuntu theme. Gtk will also install if you download these themes and drag and dropm it into appearance -> preferences -> themes. Emerald requires Compiz. I use compiz fusion in synaptic.

M.

---

### Post by Pro-reason on 2008-09-17
> **mike1234 said:**
> Metacity is standard Ubuntu theme. Gtk will also install if you download these themes and drag and dropm it into appearance -> preferences -> themes. Emerald requires Compiz. I use compiz fusion in synaptic.

M.

That's not very accurate.  [Metacity]("http://en.wikipedia.org/wiki/Metacity") is the default [window manager]("http://en.wikipedia.org/wiki/Window_manager") for GNOME.  It can be replaced by another if you like.  It is most commonly replaced by Enlightenment, [Openbox]("http://en.wikipedia.org/wiki/Openbox") or [Compiz]("http://en.wikipedia.org/wiki/Compiz").

To handle themes and suchlike, each window manager has a window decorator. Compiz uses one called [Emerald]("http://en.wikipedia.org/wiki/Emerald_(window_decorator)").

When you download a theme, you apply that theme to a certain window manager/decorator.  Applying a Metacity theme will have little effect on my computer, because Compiz/Emerald is my window manager/decorator. 

[Gtk+]("http://en.wikipedia.org/wiki/Gtk+") (currently at version 2) is a toolkit used to write graphical software.  It is used for GNOME, Metacity, Compiz and many others.  [KDE]("http://en.wikipedia.org/wiki/KDE") and Kwin, on the other hand, use Qt.

---

