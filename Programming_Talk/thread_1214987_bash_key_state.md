---
title: "bash key state"
date: 2009-07-16
forum: Programming Talk
---

### Post by zhocchao on 2009-07-16
Hi
How can I make my bash script to notice a keyboard stroke or a mouse click. I want the script to exit when Alt is up or the mouse is clicked.

---

### Post by MadCow108 on 2009-07-16
I don't know if you can react to alt or mouseclicks
but you can trap signals to break loops
```

#!/bin/bash

pass=1
echo "start"
trap "echo exiting;break;" SIGINT SIGTERM
while :
do
   echo "looping $pass"
   let "pass++"
   sleep 1
done
echo "end"

```

cancel this with ctrl-c

---

### Post by zhocchao on 2009-07-17
unfortunately this does not help me. I made a window moving script. Moving the window (the pointer) at the left or right screenedge resizes it to half screen. This works quite good. But when clicking to move the window somewhere else the script continues. Maybe I should use some timeout/ a loop like your example.

```

#!/bin/bash
xte 'keydown Alt_L' ;xte 'key F7' ;xte 'keyup Alt_L'
xa1=5
xa2=1270
dskb=1256 
dskh=800 
while :; do
akposx=$(xmousepos |awk '{print $1}')
akposy=$(xmousepos |awk '{print $2}')
 if [ $akposx -lt $xa1 ]; then
xte 'mouseclick 1'
wmctrl -r :ACTIVE:  -e "0,0,0,$(($dskb/2)),$(($dskh))"
exit;
fi
 if [ $akposx -gt $xa2 ]; then
xte 'mouseclick 1'
wmctrl -r :ACTIVE:  -e "0,$(($dskb/2)),0,$(($dskb/2)),$(($dskh))"
exit;
fi
done

```

---

