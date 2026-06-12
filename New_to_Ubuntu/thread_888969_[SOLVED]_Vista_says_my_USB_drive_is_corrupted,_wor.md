---
title: "[SOLVED] Vista says my USB drive is corrupted, works fine on Ubuntu"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by tprzepiorka on 2008-08-13
Now I know, this may not be a problem with ubuntu and rather with Vista. Either way hopefully I can find some help resolving the issue here.

I was copying some files onto my usb thumb drive and once they finished I right-clicked on the side bar of nautilus and chose "unmount". Pulled out the drive and put it in another computer running vista. The drive showed uo (F:\), but when I try to open it all i get is an error: The file or directory is corrupted or unreadable. But I can put the drive back into Ubuntu and it works fine. 

I tried restarting the Vista computer, but that didn't help.

EDIT: I just formatted the drive and now it works fine.

---

### Post by Methuselah on 2008-08-13
When it comes up in Ubuntu right-click the desktop icon and choose properties.
On the first tab (Basic) it should say at the bottom what the filesystem is.
If it says msdos, windows should be able to read it.
This is usually how such small removable drives are formatted.

---

