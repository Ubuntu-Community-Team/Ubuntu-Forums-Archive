---
title: "File date stamping"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by rogerdb on 2008-05-14
:confused:I recently upgraded from Ubuntu V7.1 to V8.04.  After the upgrade Ubuntu stamps a copied file with the date & time the copy was made.  Is there a way to change the time & date stamp on the copy to the original file date & time stamp like V7.1 did?

---

### Post by rogerdb on 2008-05-14
Can anyone help?

---

### Post by Oldsoldier2003 on 2008-05-14
```
cp -p
```

from man cp
```
 -p     same as --preserve=mode,ownership,timestamps
```

---

### Post by drs305 on 2008-05-14
The 'cp -p' will preserve timestamps on future copies. You can also changed existing timestamps - read the man page for 'touch'.

Here is a way to make the file have a particular date:
```
touch -t CCYYMMDDhhmm.ss filename
```
(the ss is optional)

---

### Post by urshans on 2008-05-20
But what if I want to use nautilus in gnome and not the terminal?

Why does it change so suddenly from one version to another?

I don't understand this, it seems to be a huge topic in many ubuntu forums and wikis, so quick repair is needed.

Thanks in advance! Urs

---

