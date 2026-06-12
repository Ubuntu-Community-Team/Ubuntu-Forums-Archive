---
title: "Icons in bottom panel (of activities overview) are inconsistent sizes?"
date: 2012-12-26
forum: New to Ubuntu
---

### Post by E Li on 2012-12-26
**Problem:** Icons in bottom panel of activities overview have wonky dimensions. Some look 50x50, while others look 16x16.

**Ideal Fix:** Make all the icons 50x50. Either that, or remove the bottom panel altogether.

**Actual Fix:** ??? :(

For some reason, I couldn't take a screenshot while of my Activities view, so I took a picture and marked the area I'm trying to fix right now.

I'm using Ubuntu 12.10, with Gnome 3.6 and using the gnome-shell theme Nord 1.6. I'm certain this problem has nothing to do with the theme though, because the problem was there even before I started using custom user themes.

Any help would be greatly appreciated!

---

### Post by E Li on 2012-12-26
After much trial and error, I found a fix to remove the whole panel.

Open up gnome-shell css. In terminal, enter:
[PHP]sudo gedit /usr/share/gnome-shell/theme/gnome-shell.css
[/PHP]

Look for #message-tray by using CTRL+F. When you find it, you should see:
[PHP]#message-tray {
    background: #2e3436 url("img/message-tray-background.png");
    background-repeat: repeat;
    transition-duration: 200;
    height: 72px;
}[/PHP]

What you see will probably different from the above, but the important thing is to change the height property from whatever it is to 1px, so instead of "height: 72px;" it should say "height: 1px;".

Save, close, and restart (Alt+F2, type 'r').
The bottom panel should be gone altogether.

Notification icons can be important sometimes though, so if anyone knows of a fix to change the icon sizes so that they're all the same, that would be even better.

---

