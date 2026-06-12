---
title: "Fluxbox"
date: 2008-08-23
forum: Philippine Team
---

### Post by initial_m on 2008-08-23
Hi Guys, I try to used fluxbox, but when i click on the Nautilus under the File Manager menu,  the default wallpaper of gnome came up, when i try to right click again on the menu, it seems that i'm already in gnome because the right click default menus of gnome is now appearing, not the Fluxbox menus. Another prob is when i'm clicking on exit under the fluxbox menu my sytems hangs, so i need to restart again my pc.

another thing if can someone give me ideas on how to change my themes aside from the styles that already included in the setup, and some shortcut keys for fluxbox.

Any ideas/suggestions are highly appreciated. tnx ;D

Btw thanks to sir Loell for the headsup on how to setup Fluxbox.

---

### Post by loell on 2008-08-23
to run nautilus without those gnome panels

you can execute ```
nautilus --no-desktop
```

but.. nautilus is actually heavy for fluxbox, you can install **pcmanfm** as you file manager, its very lightweight :)

```
sudo apt-get install pcmanfm
```

---

### Post by Nhatz on 2008-08-23
initial_m dude tama si loell...

heto yung code..

ASTIG!!!:guitar:

```
[exec] (Nautilus) {nautilus --browser --no-desktop}
```

---

### Post by loell on 2008-08-23
aheheheh, may --browser pa pala na parameter. :lolflag:

---

