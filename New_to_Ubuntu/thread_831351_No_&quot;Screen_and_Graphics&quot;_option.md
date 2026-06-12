---
title: "No &quot;Screen and Graphics&quot; option"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by EvenOlder on 2008-06-16
Hello all.  I'm lovin' me some ubuntu right now.

I can't figure out how to tell ubuntu the type of monitor/max res for it.

I've got the miniITX Intel board 210gly, with SiS662/mirage graphics.\
Thanks to these forums, I've downloaded the binaries/drivers posted here.
I've successfully exited the graphics engine and nano'd the xorg.conf to use the drivers.
And of course, it reads "out of range" on my monitor.
So I set the driver to be "vesa" and it picked 1280x1024 for the max res.
The monitor is a simple flat screen 19" widescreen that does 1440x900.
But I can't find anywhere to tell ubuntu that fact, despite the various references to something in system/preferences, it's not there.

Thank for any help,
steve

---

### Post by avtolle on 2008-06-16
To get the graphic version from menus. Right click Applications, select "Edit Menus". Go down to Other; in the right window, there will be several choices, including "Screens and Graphics". Check this application, close out, and it will be in the Applications menu.

OR

From the terminal```
sudo displayconfig-gtx
``` gets you there as well. HTH.

---

### Post by EvenOlder on 2008-06-16
Avtolle:
You Sir, are a great person.
Thank you.
steve

If i knew how to post a thanks, I would.

---

### Post by avtolle on 2008-06-16
No problem. Glad to help.

---

