---
title: "gnome-open command equivalent?"
date: 2011-10-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by mschering on 2011-10-11
I just noticed the gnome-open console command is not there anymore in 11.10. Is there an equivalent like unity-open for example?

I really need this because of a java program I developed that needs a console command to open a file with the default program.

"see" is not working optimal because it opens different default programs.

Thanks for any answer!

Regards,

Merijn Schering

---

### Post by ilovelinux33467 on 2011-10-11
Does xdg-open work?

---

### Post by mschering on 2011-10-11
Thanks, that seems to work perfectly!

I understand this should also work in KDE etc. so it's even better.

Regards,
Merijn

---

### Post by ilovelinux33467 on 2011-10-11
You're welcome :)

---

### Post by hugmenot on 2011-10-11
gvfs-open is the successor of gnome-open, which was deprecated.

---

### Post by Johnb0y on 2011-10-11
please remember to mark as solved if solved. thanks.

---

### Post by mschering on 2011-10-11
Does xdg-open do the same as gvfs-open but more cross-platform/desktop?

---

### Post by ilovelinux33467 on 2011-10-11
Yes. xdg-open is part of freedesktop.org which is cross desktop compatible. It is actually just a script which calls gvfs-open, kde-open, etc... depending on the desktop environment being run.

---

### Post by mschering on 2011-10-11
Great! Thank you for all the replies.

---

