---
title: "how to change trash icon?"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by WinterMadness on 2008-07-15
so i downloaded a bunch of trash icons, and you cant just click properties on it and change it. Can anyone share some insight?

---

### Post by iaculallad on 2008-07-15
> **WinterMadness said:**
> so i downloaded a bunch of trash icons, and you cant just click properties on it and change it. Can anyone share some insight?

Change it by placing your new icons to the directories listed below:

**Empty icon: **

> /usr/share/icons/Human/48x48/places/user-trash.png

**Full icon: **

> /usr/share/icons/Human/48x48/status/user-trash-full.png

Be sure to backup your old icon files before overwriting it with downloaded Trash icons.

```
gksudo nautilus
```

Then copy and paste it using the same names.

---

