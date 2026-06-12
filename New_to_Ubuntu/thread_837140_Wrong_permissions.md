---
title: "Wrong permissions?"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by livefastdiefun87 on 2008-06-22
After login I get an error message stating that "user $home /.dmrc file is being ignored this prevents the default season and launguage from being saved file should be owned by user and have 644 permissions user home directory must be own by user and not writeable by others" clicking ok on this message still brings me to the desktop as if nothing has happened and I cant seem to find anything that is affected by this. Please can someone advise me on what has happened here

---

### Post by sisco311 on 2008-06-22
Restore the permissions form a terminal:
```

sudo chown -R $USERNAME. $HOME[FONT=monospace]
[/FONT]chmod 0750 $HOME[FONT=monospace]
[/FONT]chmod 0644 $HOME/.dmrc
```

---

