---
title: "Add a program to acivities/applications menu"
date: 2015-07-09
forum: New to Ubuntu
---

### Post by misterbreadcrum on 2015-07-09
I've just installed Android Studio and Sublme Text and neither are showing up on the applications menu.  So If I close out of them now, how would I get back to them without re-installing them via the wizard?  I've looked around in usr/bin and usr/share for these files, but I don't see them anywhere.  Could some one point me in the right direction?

---

### Post by jason_gibson2 on 2015-07-09
How did you install them? If from the package manager or a .deb file then they should be there. If you installed any other way then you might have to create a .desktop file for them and put it in ~/.local/share/applications or /usr/share/applications for them to show up in the standard menus.

---

### Post by misterbreadcrum on 2015-07-09
So for the android manager I went to the site and downloaded the zip.  I went into bin and ran studio.sh in terminal as per the instructions on the install page.  There doesn't seem to be an entry in the software manager for android studios or sublime text, so I don't know how I would have gotten them through there.

How would I go about creating a desktop file for such a thing?  The problem I'm finding with this is taht the process being shown on the system monitor is called studio.sh, but that itself is just a setup wizard for the studio.  So I'm still pretty lost.

---

### Post by sandyd on 2015-07-09
For android studio, go to Tools, and click on create desktop entry.

How did you install sublime?

---

