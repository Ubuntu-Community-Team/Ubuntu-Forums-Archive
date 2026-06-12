---
title: "[SOLVED] open programs no longer show in panel"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by le singe on 2008-08-17
So I was messing around with my panels, shortening them (unchecking "expand") and making them bigger, putting them all on top or bottom or to the side....  

anyways, that's really all I did.  I set them back to normal, and then noticed that the windows I had either open or minimized were no longer visible on the bottom panel like they always had been, and no panel properties settings seemed to bring them back.  So I deleted my bottom panel then created a new one set up like it is by default, and now my programs still don't show on either top or bottom panel.  This was after a reboot, as well.

Is there some way to make my panel useful again, to assign windows to show on either one panel or the other?

Anybody else who's still figuring ubuntu out ever find that you screw things up that you shouldn't even be able to screw up in the first place?

---

### Post by UbuntuNerd on 2008-08-17
right click on the panel you want your windows to be and click add to panel scroll down until you see (window list) highlight it and hit add that should be it.

---

### Post by K2712 on 2008-08-17
If you want to just reset your panels to default settings:


Back up panel settings first(just in case):

```
cp -R ~/.gconf/apps/panel ~/panel_bak

```

Delete current panel profiles:

```
rm -r ~/.gconf/apps/panel
```

Now log out and back in and your panels should be at their default settings and you can change them however you want.

---

### Post by le singe on 2008-08-18
ahh, thank you both!

---

