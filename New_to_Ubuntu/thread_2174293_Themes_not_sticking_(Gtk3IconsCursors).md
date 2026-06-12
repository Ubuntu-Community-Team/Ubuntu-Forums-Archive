---
title: "Themes not sticking (Gtk3/Icons/Cursors)"
date: 2013-09-13
forum: New to Ubuntu
---

### Post by Jonathan Precise on 2013-09-13
Hello all!

I'm running ubuntu 13.04 and i'm noticing that when I change the theme through gnome-tweak-tool, ubuntu-tweak, or the appearance section of gnome-control-center, the themes will not change. I tried logging-out and logging-in, and still no change.:(

Example: I changed my icon-theme to "gnome", and it changes. Re-login, and I try to change it back to "Humanity". No change. Re-login, still no change. Same happens with Gtk3 themes.

Example 2: I try changing the cursor theme. No change. Re-login. No change. However, when something is loading, the theme I chose does appear. When it is done loading, back to the default DMZ-White.

Example 3: I change the session to KDE. Re-login to the default Ubuntu session, and the oxygen-gtk theme sticks. And so do the icons. Changing them is unsuccessful.

KDE-theme-switching is not affected.

Only gnome-based sessions (using Gtk3, icons in "/usr/share/icons", and cursors in "/usr/share/icons") are affected.
What's going on?

Update: Looks like it's kde "sticky" settings. Since I have found the source of the problem, I shall mark this as solved.

---

### Post by Jonathan Precise on 2013-09-17
Update: I have reported a bug on this ([lpbug]1226847[/lpbug])

---

### Post by Isamu715 on 2013-09-18
Try changing the theme from the command line and see if it returns any errors.
For ex.:
```
gsettings set org.gnome.desktop.interface gtk-theme Radiance
```

---

### Post by Jonathan Precise on 2013-09-18
No errors!!!

Edit: The theme has not changed, though.

---

