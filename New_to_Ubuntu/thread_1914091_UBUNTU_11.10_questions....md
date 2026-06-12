---
title: "UBUNTU 11.10 questions..."
date: 2012-01-23
forum: New to Ubuntu
---

### Post by shmotzy on 2012-01-23
How can I put a shortcut to my hard drive on my desktop?  Also, how can I put a "my computer" icon similar to windows on my desktop?  Also, I downloaded and installed Crossover games from the website and I do not know where it installed exactly!!

---

### Post by lechien73 on 2012-01-23
You can put a computer icon on the desktop by doing the following:

1. Click on the Ubuntu icon in the launcher and type:

```
dconf-editor
```

in the search box.

2. Navigate to **org -> gnome -> desktop -> background**

3. Check the box that says **show-desktop-icons**

4. Navigate to **org -> gnome -> nautilus -> desktop**

5. Check the box that says **computer-icon-visible** (if it's already checked, then uncheck it and check it again).

---

