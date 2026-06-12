---
title: "Set Wallpaper From Terminal"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by abeisgreat on 2008-10-21
I need the bash command to change my desktop wallpaper. 

Thanks abe

---

### Post by eternalnewbee on 2008-10-21
I don't know, but I found this site. Hope it's of use to you.
[http://www.ubuntu-unleashed.com/2007/12/video-howto-ubuntu-terminal-commands.html](http://www.ubuntu-unleashed.com/2007/12/video-howto-ubuntu-terminal-commands.html)

---

### Post by bodhi.zazen on 2008-10-21
I use fluxbox, so ...

fbsetbg -f /path/to/background.png

You can use that (install fluxbox, works in gnome)

Or if you prefer to stay in gnome you can use the slightly more verbose command :

```
gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/path/to/background.png"
```

Note: backgrounds are often in /usr/share/backgrounds

---

