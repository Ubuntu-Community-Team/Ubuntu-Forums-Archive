---
title: "Ubuntu Tweak Screwed Up"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by toasty_ghosty on 2008-09-18
Hello

I've been using Ubuntu for awhile but thought I would try out Ubuntu Tweak. I didn't do much besides change it so it would not display the trash bin as well as the home folder. Now, it doesn't display anything including files such as recent downloads. How can I go about manually changing this?

Thanks.

---

### Post by frankleeee on 2008-09-18
If you are using the desktop as the destination of downloads look in system-desktop, if not there they may be in your home folder.

---

### Post by toasty_ghosty on 2008-09-18
They are there but the icons are not showing up, and I cannot find the command to change it back so the icons show.

---

### Post by Nepherte on 2008-09-18
Open up gconf-editor
```
gconf-editor
```
and navigate to apps > nautilus > desktop. Enable the check boxes you want.

---

