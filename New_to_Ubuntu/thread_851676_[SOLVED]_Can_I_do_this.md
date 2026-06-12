---
title: "[SOLVED] Can I do this?"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by T2manner on 2008-07-06
Can I get temporary root privileges when browsing files?

---

### Post by gila_monster on 2008-07-06
Well, how temporary? You can run Nautilus using sudo (from the command line) or with gksudo, and that instance of Nautilus would have root privileges for as long as it was active. I'd be careful of running a file browser as root, though. You only have to mess up once....

---

### Post by tjwoosta on 2008-07-06
open a terminal and type 
```
gksudo nautilus
```

this opens a nautilus file browser with root privlages (just close the window and root privlages go away)

---

### Post by dasunst3r on 2008-07-06
Yes -- Press Alt+F2, type in *gksudo nautilus*, and hit enter.  Enter your password, and the Nautilus window that comes up will have root privileges.

---

### Post by T2manner on 2008-07-06
thanks!
this is exactly what i needed.

---

