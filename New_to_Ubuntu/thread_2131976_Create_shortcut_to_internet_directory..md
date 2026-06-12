---
title: "Create shortcut to internet directory."
date: 2013-04-03
forum: New to Ubuntu
---

### Post by jamesaepp on 2013-04-03
In windows os, there is a way while in a folder with the explorer to right click -> new -> shortcut

What is the equivalent procedure/steps for this?

No bash scripting!

---

### Post by vanadium on 2013-04-03
Rightclick "Make Link". Beware that symlinks are much more powerfull than Windows shortcuts. For practical purposes, they behave like a real directory. You can use them to create convenient access to the same data from different locations.

---

### Post by mamamia88 on 2013-04-03
Also you can cd to the path you want the link in and type ln -s /path/to/fileorfolder.

---

### Post by jamesaepp on 2013-04-03
> **vanadium said:**
> Rightclick "Make Link". Beware that symlinks are much more powerfull than Windows shortcuts. For practical purposes, they behave like a real directory. You can use them to create convenient access to the same data from different locations.


I am not seeing this "Make Link" option.....perhaps it is because I am using gnome-shell? Sorry, I didn't necessarily mean "a directory" it's more like I want it to link to a specific page. My bad. :S

---

### Post by lykwydchykyn on 2013-04-03
Symlinks aren't really analogous to a Windows shortcut.  On most Linux desktops, the ".desktop" file is a closer match.

I don't use GNOME or nautilus, but if it has an equivalent function, it's probably a template under "create new".  This is where it is on my file manager (dolphin).

If all else fails, a shortcut like this is nothing more than a text file with the following inside:
```

[Desktop Entry]
Icon=text-html
Type=Link
URL[$e]=http://www.example.com

```

---

### Post by zrdc28 on 2013-04-03
Minimize the file manager window, drag and drop the file on the desktop!

---

