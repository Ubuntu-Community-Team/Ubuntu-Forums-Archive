---
title: "mplayer in firefox?"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by Andrew79 on 2008-07-23
okay, so maybe an update changed something? I now have this strange mplayer when I try to open a link. it used to just play a normal whatever it was. I can't remeber. but all i know is i do not want mplayer to be my default player in firefox, how do i get rid of it?

---

### Post by RomeReactor on 2008-07-23
Hi. You can uninstall Mplayer and install Totem or VLC:
```
sudo aptitude purge mozilla-mplayer && sudo aptitude install totem-mozilla
```
Or:
```
sudo aptitude purge mozilla-mplayer && sudo aptitude install mozilla-plugin-vlc
```

---

### Post by tuxxy on 2008-07-23
OPen Firefox preferences, select the applications tab - now select which apps for each filetype

---

