---
title: "Upgrade problem with 12.04 and Compiz"
date: 2012-05-15
forum: New to Ubuntu
---

### Post by upgrade12 on 2012-05-15
Hello
I've been running Ubuntu 11.04 and just upgraded to 12.04. The upgrade went fairly smooth until the reboot and startup of the new version.  It loaded the icons I had on the desktop, but did not load the top system taskbar, or the sidebar. I then got the warning that "The application Compiz has closed unexpectedly" Am I going to have to download the iso and burn it to disk?

---

### Post by Lisiano on 2012-05-15
It's recomended that you do. Either way, one easy way to fix this is to reset compiz. Switch to a TTY (Ctrl+Alt+F1-F6) and login using your username and password (The password will not be visible) then type out these commands.
```
killall -9 compiz
rm -r ~/.config/compiz-1
```
After that you can type ```
exit
``` to log out and switch back to X (Ctrl+Alt+F7) and login as normal.

As a side note, I'd burn a disk just in case something happens and you need to use a LiveCD, always good to have a recent one lying around.

EDIT: Do it in a TTY because after the first command, compiz will stop and you will not be able to type in a terminal.

---

