---
title: "[SOLVED] Running gOS from USB boot error"
date: 2008-06-12
forum: Other OS Talk
---

### Post by FooAtari on 2008-06-12
I have installed gOS as per instructions here;
[URL="http://www.pendrivelinux.com/2008/05/27/usb-gos-persistent-install-from-live-cd/"]
USB gOS persistent install from Live CD[/URL]

Everything seemed to go OK until it came to rebooting.  The system attempts to boot from the USB but I am then presented with the following error;

[B]Could not find kernel image: linux
boot:[/B]

I have tried to install this twice now without success does anyone have any ideas whats going on?

---

### Post by FooAtari on 2008-06-12
Nevermind, fixed it I think.

Seems when I got to this step;
```
# Type cd /media/gOS
# Type wget pendrivelinux.com/downloads/gOS/syslinux.cfg
```

The file wasn't copied on the USB drive.

I downloaded the file and copied it over to the gOS (boot?) partition myself and it seems to be working fine now.

---

