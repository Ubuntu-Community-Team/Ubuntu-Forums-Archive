---
title: "Installing apps to Palm WebOS Emulator"
date: 2010-01-09
forum: Programming Talk
---

### Post by jdforsythe on 2010-01-09
When you install the Palm WebOS SDK and emulator, as described on [http://developer.palm.com](http://developer.palm.com) it does not work correctly.

You can run the emulator, but the tool "palm-install", used to install your .ipk packages to the emulator, will not run, because somewhere during the install, the novacom daemon fails to work properly.

When you try to run palm-install you'll get a "connection refused" error.

The workaround I'm using for now, if you're interested, is to manually start the novacomd before running the emulator.  I've written a simple script.

```
#!/bin/sh
/opt/Palm/novacom/novacomd
palm-emulator
```

I saved this as ~/palmdev.sh then changed the permissions to allow execution.  Then I made a launcher on the desktop to point to this script.  Now I just double-click the launcher icon and voila, the daemon starts, the emulator starts, and when I'm ready, palm-install works.

I've tried adding the novacomd to the Startup programs, but it didn't work.

If anyone has a better solution, please let me know.  I'll work on a full tutorial to install the SDK later, for now I have to go to work.

Happy developing!

---

### Post by soldier_of_light_army on 2010-02-21
the problem is with the novacomd daemon not starting at startup. You can find another nice way to fix it here [http://zootlinux.blogspot.com/2009/11/installing-webos-sdk-in-ubuntu-910.html]("http://zootlinux.blogspot.com/2009/11/installing-webos-sdk-in-ubuntu-910.html")

---

