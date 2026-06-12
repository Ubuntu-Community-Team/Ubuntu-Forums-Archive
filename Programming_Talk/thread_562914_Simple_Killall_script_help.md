---
title: "Simple Killall script? help"
date: 2007-09-29
forum: Programming Talk
---

### Post by jadonchristensen on 2007-09-29
I just want to make a simple kill script. What am I doing wrong?

```

#!/bin/sh
/usr/bin/killall gnome-system-monitor
/usr/bin/killall konqueror
/usr/bin/killall knetworkmanager
/usr/bin/killall kmix
/usr/bin/killall katapult
/usr/bin/killall kbluetoothd
/usr/bin/killall NetworkManagerD
/usr/bin/killall gnome*
/usr/bin/killall dolphin

```

I get:
comp3@cp:~/SCRIPTS$ sh program-killer.sh
gnome-system-mo: no process killed
konqueror: no process killed
knetworkmanager: no process killed
kmix: no process killed
katapult: no process killed
kbluetoothd: no process killed
NetworkManagerD: no process killed

---

### Post by LPomfrey on 2007-09-29
Have you tried:
```
sudo sh program-killer.sh
```

---

### Post by jadonchristensen on 2007-09-29
That works. Looks like I need to use sudo.

Thank you

---

