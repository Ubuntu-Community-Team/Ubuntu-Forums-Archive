---
title: "How do i check if I have a package installed using Shell?"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by markbusu on 2008-05-26
Thanks!

---

### Post by ubernuber on 2008-05-26
that's something I would like to know as well.

---

### Post by Inxsible on 2008-05-26
```
which *program-name*
```If it gives any output you have that program installed. If it simply comes back to the prompt without any output, you don't have that program installed.

---

### Post by sisco311 on 2008-05-26
```
aptitude show <package>
```
or
```
aptitude show <package> | grep State
```
or
```
aptitude search <package>
```
(i = installed)

---

### Post by markbusu on 2008-05-26
Thanks!

---

### Post by smartgilli on 2012-12-31
This might help you,
[http://ssatish.wordpress.com/2012/12/31/ubuntu-how-to-check-if-a-software-is-installed/](http://ssatish.wordpress.com/2012/12/31/ubuntu-how-to-check-if-a-software-is-installed/)

Cheerz :)

---

### Post by howefield on 2012-12-31
Old thread closed.

---

