---
title: "Every Folder i open with Shortcut, opens MoviePlayer"
date: 2011-10-18
forum: New to Ubuntu
---

### Post by shareMenaPeace on 2011-10-18
I just upgraded to 11.10 and now all Shortcuts seem to open MoviePlayer and MoviePlayer opens every single file.


Ideas?

I use System Monitor and kill the "totem" process to get rid of this bug.

---

### Post by mc4man on 2011-10-18
Open a terminal & run

```
gedit ~/.local/share/applications/mimeapps.list
```

In the [Default Applications] section there will be a line starting with
inode/directory=
Delete the line

---

### Post by shareMenaPeace on 2011-10-21
> **mc4man said:**
> Open a terminal & run

```
gedit ~/.local/share/applications/mimeapps.list
```

In the [Default Applications] section there will be a line starting with
inode/directory=
Delete the line


Thanks mc4man!

Though the line was in the section "Added Associations"

---

### Post by mc4man on 2011-10-21
If this starts up again then open mimeapps.list & in the **[Default Applications] section** put this line in. This will always keep nautilus as the default with the proper .desktop

```
inode/directory=nautilus-home.desktop
```

---

