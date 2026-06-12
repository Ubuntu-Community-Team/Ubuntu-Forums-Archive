---
title: "user name structure..."
date: 2007-12-30
forum: Other OS Talk
---

### Post by cprofitt on 2007-12-30
Why does Fedora Core 8 and openSUSE 10.3 allow you to have a user name such as first.last but Ubuntu does not? Is this something that can be changed?

---

### Post by kidders on 2008-01-01
Hi there,

There doesn't seem to be any such restriction. Just to be sure, I gave it a try...```
# useradd first_name.surname
# passwd first_name.surname
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
...
[SIZE=1][ Try to login, etc. ]
[/SIZE]...
# userdel first_name.surname
```

The set of characters acceptable in usernames is pretty constant across all Linux & Linux-like OSs. Any restrictions present in Ubuntu should also apply to all other distros. Having said that, to avoid problems with naively-written software, I've always thought it best to stick to US English alphanumeric characters.

---

