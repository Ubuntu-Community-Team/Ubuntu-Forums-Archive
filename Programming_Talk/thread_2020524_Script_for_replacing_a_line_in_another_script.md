---
title: "Script for replacing a line in another script"
date: 2012-07-08
forum: Programming Talk
---

### Post by BoogeyOfTheMan on 2012-07-08
I'm looking to see if its possible to create a script that takes the path in the currently focused nautilus window and outputs it as a line in another script.

I have a script that opens the folder to the current audiobook I'm listening to open on boot, but since sometimes the book I'm listening to changes frquently, I'd like to just run a script to edit my startup script instead of editing it by hand.

Is this possible?

---

### Post by epicoder on 2012-07-08
You can do this with a nautilus script and sed. Nautilus scripts have a number of context sensitive variables made available to them, such as $NAUTILUS_SCRIPT_CURRENT_URI for the current directory. So to change the variable var in the script ~/script.sh to the current directory, you would place this script in ~/.gnome2/nautilus-scripts:
```

[color=#228888]**#!/bin/sh**
# The -i.bak creates a backup of the edited file with the extension .bak[/color]
[color=#22BBBB]sed[/color] -i.bak [color=red]'s:var=.*$:var='[/color][color=#BBAA22]$NAUTILUS_SCRIPT_CURRENT_URI[/color][color=red]':'[/color] ~/script.sh

```

---

### Post by BoogeyOfTheMan on 2012-07-10
Ahh, ok. When I first read this a few days ago, it looked like gibbersih due to lack of sleep. Now I know what you mean, heh.

I just did a fresh install of 12.04 and its gonna take me a few days to get back around to setting my startup scripts again.

---

