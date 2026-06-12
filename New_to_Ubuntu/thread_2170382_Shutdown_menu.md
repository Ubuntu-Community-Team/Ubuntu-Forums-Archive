---
title: "Shutdown menu"
date: 2013-08-26
forum: New to Ubuntu
---

### Post by kend650 on 2013-08-26
Since I've upgraded to 13.04, the shutdown command from the menu seldom works properly.  Sometimes when I select shutdown from the menu, my system immediatelly starts to shutdown.  Sometimes, the panel with the shutdow/restart buttons appear, and I can sellect shutdown and the system shuts down, sometimes selecting the shutdown button, causes a restart.  There is no consistency.

Does anyone else have this issue, and does anyone have any ideas on how to make it work properly?  I didn't have this problem with 12.10...

Thanks,
ken

---

### Post by Jonathan Precise on 2013-08-26
It maybe the fact that now the shutdown options are offered in a different GUI. Try:

```
gnome-session-quit --power-off
```

If it works with that command, then try

```
gnome-desktop-item-edit --create-new /home/**user**/Desktop/
```

Replace **user** with your username.

Then in the command, put in gnome-session-quit --power-off
This makes a desktop icon for the shut down menu.

---

