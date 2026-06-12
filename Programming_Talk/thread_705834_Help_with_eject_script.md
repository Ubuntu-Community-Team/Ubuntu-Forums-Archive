---
title: "Help with eject script"
date: 2008-02-23
forum: Programming Talk
---

### Post by autocrosser on 2008-02-23
I have a HowTo to open/close CD drives with one key & someone asked me about having the media-eject.png show like the eject-only keyboard default.

My script looks like:

#!/bin/bash

tray_status=`cat .tray_status0.sh`
if [ "$tray_status" == "Closed" ]
then
    eject /dev/scd0
    echo "Open" > .tray_status0.sh
elif [ "$tray_status" == "Open" ]
then
    eject -t /dev/scd0
    echo "Closed" > .tray_status0.sh
else
    eject /dev/scd0
    echo "Open" > .tray_status0.sh
fi

Ideas on how to display the .png during tray open/close?

---

### Post by Gen2ly on 2008-02-23
dang... memory is...  really slow.  zenity I believe is a gnome program that can dispaly windows and popups.  Been a bit though - better look it up ;)

---

