---
title: "command line to know actual gnome window manager ?"
date: 2008-08-28
forum: Programming Talk
---

### Post by segalion on 2008-08-28
Id like to kwnow a command line to discover the actual windowmanager active in Ubuntu.

Thats to conmute between metacity and compiz...


Thanks

---

### Post by mali2297 on 2008-08-28
You can use **pgrep** to perform a search among the running processes.

Try a script like
```

#!/bin/sh

if [ "$(pgrep metacity)" ]; then
        echo "Metacity is running."
fi

```

---

### Post by rangalo on 2008-08-28
I think you need to install wmctrl

On my workstation,
```

$ wmctrl -m
Name: Fluxbox
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: N/A

```

regards,
Hardik

---

### Post by dtmilano on 2008-08-28
```
gconftool-2 --get /desktop/gnome/applications/window_manager/current
 gconftool-2 --get /desktop/gnome/applications/window_manager/default

```

---

### Post by segalion on 2008-08-29
Thanks a lot.
For me, seems that 
gconftool-2 --get /desktop/gnome/applications/window_manager/current
allways play compiz, even when metacity is actual windowmanager running.

---

