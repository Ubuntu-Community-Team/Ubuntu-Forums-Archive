---
title: "Kubuntu repository help."
date: 2006-02-12
forum: Repositories &amp; Backports
---

### Post by Mith on 2006-02-12
I've fiddled with regular Ubuntu but GNOME was not my style. I like KDE but I'm a n00b. Anyway, I keep trying to edit the repositories but konsole is telling me that gedit is invalid or something. Is there a different command for Kubuntu?

---

### Post by ajgreeny on 2006-02-12
You need to use kdesu kate /etc/apt/sources.list to open your file that lists repositories.  Using sudo as you would for gedit gives all sorts of error messages.  This is the case for most if not all kde progs, it seems to me.
I hope I understood your problem, but if not post again and we'll see what can be done.

---

### Post by noigeaR on 2006-02-12
kwrite or kate are the most common editors in kde. you can also use nano from a konsole.

if you use konqueror you can easily edit files in root mode with kate.
right click the file you wish to edit -> actions -> edit as root
enter your password and you can edit the file with root privileges.

---

