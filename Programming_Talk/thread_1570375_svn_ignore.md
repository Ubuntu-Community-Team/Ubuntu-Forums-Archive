---
title: "svn ignore"
date: 2010-09-08
forum: Programming Talk
---

### Post by rax_m on 2010-09-08
Hi all, 

I am setting up an svn repository for our development team. I need to set the svn ignore property on the repository, so that all files of a certain type are ignored (e.g. *.log and *.done). 

The install is done on redhat. 

Can I do this in a config file without using the svn:ignore command?

Thanks
Rax

---

### Post by surfer on 2010-09-08
you can edit your ~/.subversion/config :

```

[auto-props]
*.log = svn:ignore

```

but this will only work for newly imported files; the ones that are under svn already will not be changed.

---

### Post by rax_m on 2010-09-09
Hi surfer, 

Thanks for the reply. Won't that only affect me as one user?
I would like the ignore to apply to anyone who uses that repo. 

R

---

### Post by surfer on 2010-09-10
yes, that will only affect you. i'm not sure it can be done globally; shouldn't every user be able to check in whatever he/she likes?

---

