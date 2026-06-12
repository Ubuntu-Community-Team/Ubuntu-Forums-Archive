---
title: "[SOLVED] where in /home do AWN personal settings live?"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by earthpigg on 2008-11-03
howdy,

1. where in /home do AWN settings live? i backed up all the contents of /home and am trying to restore a select few programs on an 8.10 clean install.

2. how do i find this info out on my own, for future reference?

thanks!

---

### Post by billgoldberg on 2008-11-03
> **earthpigg said:**
> howdy,

1. where in /home do AWN settings live? i backed up all the contents of /home and am trying to restore a select few programs on an 8.10 clean install.

2. how do i find this info out on my own, for future reference?

thanks!

I presumed it would .awn, but it doesn't seem to exist.

rw@legend:~$ whereis awn
awn: /usr/lib/awn /usr/share/awn

---

### Post by dje on 2008-11-03
/home/**your_username**/.config/awn

in future look around the hidden folders in your home folder, that is where user specific program settings are stored usually under .*program_name* or .gnome2/*program_name* or .config/*program_name*

hope that helps
dje

---

### Post by dfreer on 2008-11-03
IIRC, somewhere in ~/.share/ but I can't remember off the top of my head. You can also do a locate for it:
```
sudo updatedb
locate awn
locate avant
```

---

### Post by Coreigh on 2008-11-03
/home/<username>/.config/awn

---

### Post by dfreer on 2008-11-03
EDIT: Clearly not only did I take so long posting that I didn't see the other posts, but somehow it made me double post. Sorry about that :D

---

### Post by earthpigg on 2008-11-03
thanks folks!

---

