---
title: "[SOLVED] Customize gnome toolbars"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by Mauler5858 on 2008-06-02
I would like to customize my gnome toolbars.  Basically i would like to take the functionality of the lower toolbar, and add it to the top toolbar, leaving me to be able to delete the bottom toolbar.  Does anybody have a good link that would help me to customize this.

---

### Post by sayakb on 2008-06-02
Do you mean the Panel? Just delete the bottom panel. Then right click on the panel and select Add to Panel. Add these: Window List, Show Desktop, Trash and whatever you like. To remove any applet, right click on it and select Remove from Panel.

---

### Post by Mauler5858 on 2008-06-02
Ok simple enough, ill try when i get home.  

Thanks

---

### Post by sayakb on 2008-06-02
No problems. You may also download new applets like the music-applet (which is in the repos).

---

### Post by drs305 on 2008-06-02
Once you have the panel set up the way you like, you can save (most of) these settings to a file should you need to restore the panel in the future. It certainly beats trying to manually reinstall them all.

To save the panel settings (example to a desktop file called panel_settings):
```
gconftool-2 --dump /apps/panel > **~/Desktop/panel_settings**
```

To restore saved panel settings and refresh the panel:
```
gconftool-2 --load **~/Desktop/panel_settings** && killall gnome-panel
```

---

