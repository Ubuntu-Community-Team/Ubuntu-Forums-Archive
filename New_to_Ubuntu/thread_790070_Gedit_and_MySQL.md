---
title: "Gedit and MySQL"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by Zeck on 2008-05-11
Hi all,
Is someone know mysql plugin in gedit ?

---

### Post by Nepherte on 2008-05-11
Gedit has built-in SQL syntax highlighting if that is what you are looking for. Somewhere under view > highlighting > sources > sql

---

### Post by Zeck on 2008-05-11
Okay, So how to work mysql query on gedit ? and how to connect mysql ?

---

### Post by indytim on 2008-05-11
You don't.  If you are trying to work on databases and tables, you will either need to access the database server through the database terminal mode or use one of the gui front ends to do the sql stuff.  The preferred route for most database users is phpMyAdmin (it's in the repositores).

Do not mess about and attempt to edit the database files directly through any type of text editor (unless you enjoy re-building your MySQL server from scratch).

IndyTim

---

### Post by indytim on 2008-05-11
Excuse me, I just re-read your posting (first cup of coffee today).  I mis-interpreted your intent.  To do any editing of the say the php that is driving your connection and subsequent query to the database, any text editor is fine.  There are a number of them out there that have syntax highlighting for the various apps (php, java etc.).  For my purposes, I just need an editor that includes line numbers (needed for the occassional programming error).

IndyTim

---

