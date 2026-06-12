---
title: "location of files deleted while superuser"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by shortridge11 on 2008-08-14
I was moving things around from my home directory (the home dir of my normal user) to a different hdd that requires superuser access.  I accidentally deleted a file while in nautilus as root, and now i can't find it.  It was called readme, so a search probably won't do much good.  Is there a trash for root or something?  If so, where is the location?

---

### Post by sayakb on 2008-08-14
The location is /root/.local/share/Trash/files
Where did you delete it from. If you used the CLI, it will be lost forever. But if you were using nautilus as root, it would be there in the trash.

---

### Post by shortridge11 on 2008-08-14
yea, that's the location.  Thanks so much!

---

### Post by sayakb on 2008-08-14
Glad I could help! :)
Please mark the thread as solved.

---

