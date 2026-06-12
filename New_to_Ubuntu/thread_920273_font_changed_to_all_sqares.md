---
title: "font changed to all sqares"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by redhue on 2008-09-15
font changed to all sqares after downloading and installing updates.what do I need to do to reverse the effects or at least change the text to something readable?

---

### Post by Pro-reason on 2008-09-15
> **redhue said:**
> font changed to all sqares after downloading and installing updates.what do I need to do to reverse the effects or at least change the text to something readable?

That's usually something that happens after you install a font without making sure it has it has global read permissions.  But I don't know why that would happen after an update.

---

### Post by knattlhuber on 2008-09-15
You could try going to System > Preference > Appearance > Fonts tab and change the application/document/desktop fonts there.
What fonts exactly are not working? The ones for the title bar, the menus, documents, or all together?

---

### Post by nowshining on 2008-09-15
open up a terminal

become root with sudo /bin/bash

then issue the following and logout and backin
```

pango-querymodules > '/usr/local/etc/pango/pango.modules'
```

edit: Remember your pw won't show as you type it and this is normal

---

### Post by Pro-reason on 2008-09-15
> **nowshining said:**
> 
edit: Remember your pw won't show as you type it and this is normal

Well, not only that, but he won't be able to see anything he is typing.

---

