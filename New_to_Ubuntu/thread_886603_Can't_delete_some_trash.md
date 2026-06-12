---
title: "Can't delete some trash"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by niccholaspage on 2008-08-11
I was following a Live CD tutorial,And I finished and deleted the folders I didn't need anymore.Than I emptied my trash(No errors doing it) and the icon displayed it still had items.Then I opened it with nautilus and I still had the items and I tried to delete them And I just couldn't.It said I don't have permissions.I'm running Ubuntu 8.04 Hardy.(Sorry for the wrong prefix....)

EDIT:Sorry,Found the answer 4 minutes after posting.

---

### Post by Ryadt on 2008-08-11
try to delete it by doing```
gksudo nautilus
```and then look for trash and delete them.

---

### Post by tuxxy on 2008-08-11
```
gksudo nautilus /home/<your_username>/.local/share/Trash
```

---

### Post by Ryadt on 2008-08-11
> **niccholaspage said:**
> 
EDIT:Sorry,Found the answer 4 minutes after posting.
Please mark the thread as solved.:popcorn:

---

