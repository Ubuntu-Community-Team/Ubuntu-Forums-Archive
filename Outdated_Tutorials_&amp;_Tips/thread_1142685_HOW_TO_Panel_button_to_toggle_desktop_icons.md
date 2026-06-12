---
title: "HOW TO: Panel button to toggle desktop icons"
date: 2009-04-29
forum: Outdated Tutorials &amp; Tips
---

### Post by vexorian on 2009-04-29
Just a quick hack.
**Requirements**
Your desktop environment must use Nautilus for the desktop, and a panel that allows custom launchers. I.E: Default ubuntu setup.

Save the next script somewhere:

```

#!/bin/sh
# click to start, click to stop

# Read the current configuration :
state=$(gconftool-2 --get /apps/nautilus/preferences/show_desktop)
if [ "$state" = "false" ];
then
    # icons currently disabled:
    # enable them:
    gconftool-2 --type boolean --set /apps/nautilus/preferences/show_desktop true
    
    # next line was not needed in hardy, if you are in hardy you might have to remove it
    # nautilus in jaunty (and possibly intrepid)  auto closes if there are no windows
    # open and desktop icons are disabled, so we probably should run it again:
    nautilus --no-default-window &
else
    # disable the icons:
    gconftool-2 --type boolean --set /apps/nautilus/preferences/show_desktop false
fi

```
i.e : /home/yourusername/scripts/toggle_desktop.sh

Don't forget to mark  the file as executable after you saved it (use nautilus to go to the folder, then right click on the file, properties, etc)

Now make a custom launcher in your  panel , 
type: application
command: The location of the script file: (i.e: /home/yourusername/scripts/toggle_desktop.sh )
comment/name: Toggle desktop icons.

You can choose a good icon later.

Congratulations, now whenever you click the launcher, desktop icons are toggled.

---

