---
title: "can't delete user dir"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by Redbeard09 on 2008-05-09
Trying to delete a user's directory in home. when I use 'sudo rm -rf /home/user/' it tells me 'rm: cannot remove `/home/user/.gvfs': Permission denied'

what does this mean, and how do I delete it?

---

### Post by gn2 on 2008-05-09
Have you tried pressing Alt + F2 and typing: gksudo nautilus

***This will open the file browser with full root permissions so be very careful what you edit or delete and close it immediately you are finished.***

---

### Post by scorp123 on 2008-05-09
"GVFS" is the "GNOME Virtual Filesystem", a component of your desktop. So this folder ".gvfs" most likely contains your settings for that component. Are you really really sure you want to delete that? Why?

[http://en.wikipedia.org/wiki/GVFS](http://en.wikipedia.org/wiki/GVFS)

---

### Post by Redbeard09 on 2008-05-09
> **gn2 said:**
> Have you tried pressing Alt + F2 and typing: gksudo nautilus

***This will open the file browser with full root permissions so be very careful what you edit or delete and close it immediately you are finished.***

Error while deleting.

Files in the folder "user" cannot be handled
because you do not have permission to see them.

---

### Post by gn2 on 2008-05-09
Why do you want to delete /home/user/.gvfs ?

---

