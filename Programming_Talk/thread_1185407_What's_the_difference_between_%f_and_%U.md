---
title: "What's the difference between %f and %U"
date: 2009-06-12
forum: Programming Talk
---

### Post by cl333r on 2009-06-12
Hi folks,
I noticed the Exec value of desktop entries (files ending with .desktop) sometimes contains either %f or %U as a param to execute the app the desktop file refers to, but I googled and couldn't find out what's the difference between %f and %U. Any ideas?

---

### Post by benj1 on 2009-06-12
%U is urls
%F is files

there are more but i can't think of them off the top of my head

---

### Post by Reiger on 2009-06-12
A guess: %f = filename; %U = url. In particular %U is used in conjunction with kio slaves (so the same app can work with files over smb, sftp, ftp, svn, etc. )

---

### Post by froggyswamp on 2009-06-12
Thanks!! I was wondering too

---

### Post by cl333r on 2009-06-12
I see, thanks!

---

