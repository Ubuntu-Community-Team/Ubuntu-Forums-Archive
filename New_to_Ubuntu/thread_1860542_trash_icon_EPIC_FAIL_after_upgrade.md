---
title: "trash icon EPIC FAIL after upgrade"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by pierreyy on 2011-10-14
hey guys i upgraded from 11.10 and now i get this message wheni try to open the trash 


 Firefox doesn't know how to open this address, because the protocol (trash) isn't associated with any program

thanks in advance!

---

### Post by mc4man on 2011-10-14
Don't know if this will help - haven't done any upgrades, only fresh installs
Try navigating to ~/.local/share/applications & deleting the mimeapps.list file

use this in a terminal if need be to open
```
nautilus ~/.local/share/applications
```

---

### Post by pierreyy on 2011-10-15
thanks alot!

---

### Post by mc4man on 2011-10-15
good to hear - 
whenever doing an upgrade it not a bad idea to remove that file - it will be reconstructed as you use the right click context menu & or set defaults for filetypes, ect.

The formating of mimeapps.list has changed a bit from lucid/maverick to natty & then again to oneiric

---

### Post by Calerid on 2011-10-15
thats the funniest error I have ever heard!

---

