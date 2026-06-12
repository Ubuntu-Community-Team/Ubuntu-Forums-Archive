---
title: "No Menus.  No Icon Tray"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by rayboston on 2008-10-26
Hi,

I seem to have screwed up my GNOME install.  When I log in I get the crane, but I don't get any menus along the top or any tray for icons at the bottom.

Ack! :-(

What did I do?

Can I reinstall GNOME?

Ray

---

### Post by Xiong Chiamiov on 2008-10-26
You probably don't need to reinstall gnome.  If you move your .gnome (.gnome2?  something similar) folder, then it will automatically regenerate when you launch gnome again, which will be equivalent to a fresh start.  You'll still have your old folder in case you need anything out of it.
```

cd 
mv .gnome .gnome.bak

```
You'll have to tab-complete .gnome, as I'm not sure exactly what it's called.

---

### Post by taqkavar on 2008-10-26
press alt+f2 then run "gnome-panel". If that did nothing press Alt+F2 again and run "gnome-terminal", then run "gnome-panel" inside the terminal and paste the output here.

---

### Post by rayboston on 2008-10-26
Running (actually installing) gnome-panel did the trick.  I uninstalled evolution. I wonder if I accidently uninstalled gnome-panel when I did that.

Oddly, I can't add the Trash to the panel.  It says that there is a problem with trash applet.  Is there any way to repair applets?

Thanks!

Ray

---

