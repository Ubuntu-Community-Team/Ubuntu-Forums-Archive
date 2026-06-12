---
title: "[SOLVED] Desktop wallpaper gone!!"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by arashiko28 on 2008-06-08
I was using my laptop on batteries and when it discharged, it turned of. The problem is that when I turned it back on, my wallpaper was gone, and I can't select any, I can, but it does not activate, just stays the brown color, not even the default 8.04 wallpaper, I can change the color, but can't make it shows any wallpaper. What happened?:confused:

---

### Post by starcannon on 2008-06-08
I'm thinking perhaps your .gconf files are corrupted.

If it were me I'd likely try,

```
rm -r ~/.gconf 
```

reboot

and see if that does it, no guarantees, but at least you'll have a fresh oem desktop to start from, you will have add your applets and things back to your gnome-panels as this will reset your desktop back to default.

---

