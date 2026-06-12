---
title: "Cannot install updates or become #superuser"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by broivan on 2008-09-06
I cannot install updates error message dpkg was interrupted

---

### Post by dje on 2008-09-06
do what the message says ;), open a terminal and run:
```
sudo dpkg --configure -a
```

dje

---

### Post by broivan on 2008-09-06
I cannot become the superuser

---

### Post by egalvan on 2008-09-06
The **[COLOR="Red"]sudo[/COLOR]** part of the command gives you temporary superuser powers.

No need to "become" superuser.

---

### Post by malathion on 2008-09-06
Can you give us the exact terminal output you receive when you try to run the suggested command?

---

