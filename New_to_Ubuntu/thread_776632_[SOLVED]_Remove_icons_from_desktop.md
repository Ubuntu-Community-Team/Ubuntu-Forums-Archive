---
title: "[SOLVED] Remove icons from desktop"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by sbonner on 2008-04-30
This should be an easy one.  I want a completely clear desktop, as much as possible.  I have faded my grey bars to full transparency, and will eventually install a doc program to reduce footprint even more.

However, there is an icon on my desktop that I do not want (gray box for a partition I will not need to get into).  How can I keep that icon from showing up?  How can I keep all icons from showing up?

I have found nothing by looking around in appearances preferences, looking on forums, etc.

Thanks for all help!

---

### Post by bilal.17 on 2008-04-30
if its a partition that shows up, then right click it then press unmount

---

### Post by sdennie on 2008-04-30
You can disable the icons by starting gconf-editor and going to /apps/nautilus/desktop.  If you disable "show_volumes" (and probably everything else), you shouldn't have anything on your desktop at all.

---

### Post by sbonner on 2008-04-30
Thanks to you both.  I went with vor's option, as mounting/unmounting is still new enough that I don't trust my ability to undo what I've done.  Worked like a charm.

Thanks!

---

