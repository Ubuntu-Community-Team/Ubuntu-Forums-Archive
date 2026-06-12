---
title: "Script right before logoff"
date: 2013-02-09
forum: Programming Talk
---

### Post by GameX2 on 2013-02-09
Hi,


I'm looking for a way to run this script right before I logoff (Change the background):
```

#!/bin/sh
gsettings set org.gnome.desktop.background picture-uri file:///usr/share/backgrounds/LoginWallpaper2.jpg
sleep 2
#skill -KILL -u gamex
```

I would also appreciate to run the script when I restart and power-off (I believe I've managed to do this before, but I'm not sure).

After doing some ressearch, what I found only work on older Ubuntu releases..

Thanks for the help!

---

