---
title: "Custom Drop-Down Menus"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by adobrakic on 2008-08-01
Is it possible for me to make a drop-down menu on my panel with shortcuts to codes such as 

```

sudo killall firefox

```

```

sudo reboot now

```

etc.

---

### Post by superbenny on 2008-08-01
You can use the application Alacarte to customize your main menus. I don't know if this is what you mean, but it will work.

Use Alt+F2 to bring up a run dialogue box, and type "alacarte" (without the quotes) and hit enter. Then you can make your own menu item.

---

### Post by Temposs on 2008-08-01
The GUI way to do this is to right-click your main menu and click "Edit Menus".  

This brings up the same alacarte program.

---

### Post by adobrakic on 2008-08-01
Yeah, this is basically what I want, but is it possible to add the drop-down menu to the right of System. So it shows as follows:

Applications | Places | System | Custom Drop-down Menu

---

### Post by superbenny on 2008-08-01
Not sure. If there is, it would probably be in gconf-editor (Alt-F2, then run "gconf-editor")

---

