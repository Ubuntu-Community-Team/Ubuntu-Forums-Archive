---
title: "mini9's gnome panel v.2.22.2 locked down"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by Hijinx on 2008-11-02
i was rearranging my panels and they went into "some of these properties are locked down" mode.  is there a patch? any suggestions? its really pissing me off to not be able to move my panels...

thanks
hijinx

---

### Post by Zerok60 on 2008-11-02
Well, when exactly does it show you this?

---

### Post by Hijinx on 2008-11-02
i want to move my panels around.  i reach up with the mouse and grab it.  try to drag it and nothing happens.  hmmm... must be locked or something i say to myself. right click panel click properties.  under general first thing it says is "some of the properties have been locked down".  orientation is grayed out in the standard 'if you click this nothing will happen' grayscale. speaking of this grayscale, in the first right click menu, add to panel, properties, and delete panel are also grayed out.

---

### Post by Zerok60 on 2008-11-02
Right click on empty part of panel. See option that says "Allow panel to move"? Click it.

---

### Post by Hijinx on 2008-11-02
i appreciate the question but give me some more credit than that.  i dont have the allow panel to move option.  i think its the version that is on here.  what version do you have that has that option?

---

### Post by Zerok60 on 2008-11-02
Ummm... update gnome. Go to the terminal and write this: ```
sudo apt-get update
```

---

### Post by Zerok60 on 2008-11-02
Followed by: ```
sudo apt-get install gnome-desktop-environment 
```

---

### Post by Hijinx on 2008-11-02
nothing happens...

---

### Post by LaneLester on 2008-11-04
I'm not sure what mini9 is, but my new Ubuntu Intrepid is not expanding. I have "Allow Panel to be Moved" checked, and I have "Properties / Expand" checked. But separators between groups of icons do not do any expanding. Everything stays where I manually place it.

Lane

---

### Post by sanzfc on 2010-02-23
Hi all…

To solve this problem only do this:

In ~/.gconf/apps/panel/toplevels/top_panel_screen0/background rename the file “%gconf.xml.new” to “%gconf.xml” and voilá…

All the panel properties are unlocked!

---

