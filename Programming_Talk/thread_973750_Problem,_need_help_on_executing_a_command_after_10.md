---
title: "Problem, need help on executing a command after 10 seconds."
date: 2008-11-07
forum: Programming Talk
---

### Post by Vinno on 2008-11-07
[.scripts/awesome.sh]
```
gnome-settings-daemon &
update-notifier &
gnome-screensaver &
gnome-power-manager &
nm-applet &
firefox &
nautilus --no-desktop &
/home/vinno/bin/mylogwatch &
/home/vinno/bin/chatemail &
exec /usr/local/bin/awesome
```

[bin/chatemail]
```
#!/bin/bash
rxvt-unicode -name centerim -e centerim &
rxvt-unicode -name irssi -e irssi &
rxvt-unicode -name ncmpc -e ncmpc -c &
rxvt-unicode -name myconsole &
rxvt-unicode -name alpine -e alpine &
rxvt-unicode -name newsbeuter -e newsbeuter &
```

All works well but the problem is, the awesome command has to be last order but I want the bash of 'chatemail' to wait 10-20 secs after awesome command before doing it stuff.

How would I go about this?

---

### Post by Sorivenul on 2008-11-07
Try your "awesome" line as:
```
sleep 10 && exec /usr/local/bin/awesome
```

---

### Post by Vinno on 2008-11-07
Thanks. Used the same syntax inside the chatemail and it worked. :)

---

