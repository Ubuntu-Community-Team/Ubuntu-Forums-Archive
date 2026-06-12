---
title: "[openbox] Can't launch openbox"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by paul_mcl on 2008-09-19
HELP! Can't launch openbox (simple 'startx' without editing of '~/.xinitrc' works).

```
Errors from xkbcomp are not fatal to the X server
Openbox-Message: Unable to find a valid menu file "/var/lib/openbox/debian-menu.xml"
Openbox-Message: Unable to find a valid menu file "debian-menu.xml"
```

After startx, it just shows shitty desktop wallpaper (even without small console in top-left corner) and X-cross mouse pointer. Only Control+Alt+F2 saved me from rebooting.

---

### Post by nowshining on 2008-09-19
you could of tried ctrl+alt+backspace

the openbox program is looking for debian-menu.xml and can't find the file and in a terminal due

sudo updatedb

then

locate debian-menu.xml

do u find it??

---

### Post by paul_mcl on 2008-09-19
```

# updatedb
-bash: updatedb: command not found
# locate debian-menu.xml
-bash: locate: command not found
# find / -name debian-menu.xml -print
#

```

---

