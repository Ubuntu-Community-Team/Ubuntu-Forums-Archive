---
title: "Removing entries for suggested applications"
date: 2012-03-29
forum: New to Ubuntu
---

### Post by 311005901 on 2012-03-29
This should be an easy fix, but I can't find anything in Google because the search always brings up results for how to remove the application completely. I've already deleted these programs (the extra entries are usually Wine programs), but the option won't go away.

How do you remove the suggested application entries in the properties menu and the context menu? I want to remove "Open with..." entries in Nautilus. 

Screenshot attached.

---

### Post by lechien73 on 2012-03-29
As far as I know, these entries are stored in the following files:

```
/usr/share/applications/mimeinfo.cache
```

and

```
~/.local/share/applications/mimeinfo.cache
```

You can edit these files to adjust the "Open With" entries.

---

### Post by 311005901 on 2012-03-29
To get rid of the extra entries in the "Open with..."->"Show More Applications" context menu, I removed some .desktop files within
```
~/.local/share/applications/
```

Apparently, there were a large number of Wine application helper files (+50) to deal with extensions. I don't know if they were created with PlayOnLinux or through the normal Wine installation, but I just deleted them and the entries have disappeared.

---

