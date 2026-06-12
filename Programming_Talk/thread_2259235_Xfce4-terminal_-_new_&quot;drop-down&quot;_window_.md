---
title: "Xfce4-terminal - new &quot;drop-down&quot; window with custom icon"
date: 2015-01-03
forum: Programming Talk
---

### Post by damien16 on 2015-01-03
Hi, 

I'm using xcfe4-terminal and wrote a shell script to automatically open multiple tabs and launch commands in them ; now, I try to open these tabs in a window with the "--drop-down" mode, but it seems to override the "--icon" parameter :/

Is there a way to open a new drop-down terminal with a custom icon ?

For example :

```

#!/bin/bash

# This line open a new window with the "drop-down" mode but with the original icon
xfce4-terminal --drop-down -T 'Title 1' --icon='/path/icon.png' -x [...]


# This line open a new standard window with the specified icon
xfce4-terminal --window -T 'Title 2' --icon='/path/icon.png' -x [...]

```

Thanks for your help :)

--
Damien

---

### Post by schragge on 2015-01-03
Since drop-down mode puts the window icon into systray (notification area), I'm afraid it's not the same icon you can change with --icon option.

---

