---
title: "Uninstalling a source.list/reverting to a previous source.list"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by WiseMaturin on 2008-12-02
I just need to get rid of a source.list file I tried to install, because after I installed it Amarok wouldn't work and was lagging my computer very, very badly.

So how can I uninstall it, and/or revert to the source.list I had before?

---

### Post by oldos2er on 2008-12-02
Copy the older one to /etc/apt/sources.list . You'll need to do this as root (using sudo).

---

### Post by -Zeus- on 2008-12-02
i'm guessing that you didn't make a backup... would you post the results of ```
ls /etc/apt/sources.*
```

---

### Post by WiseMaturin on 2008-12-11
The files that I have in /etc/apt:
sources.list
sources.list-20080119-3v1no-backup
sources.list-20081201-3v1no-backup
sources.list.distUpgrade
sources.list.save

And that is all. The folder '/etc/apt/sources.list.d' has no files in it at all.


I guess I have to start from scratch then? lol

---

