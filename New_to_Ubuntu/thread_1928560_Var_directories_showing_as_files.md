---
title: "Var directories showing as files"
date: 2012-02-20
forum: New to Ubuntu
---

### Post by bacobits9982 on 2012-02-20
Ubuntu 11.10 - All of my var directories are showing up as files, not directories. 

When I tried to copy a directory into my var/www/ I was getting an error saying I didn't have permission.  So I went to a command window, and ran teh command sudo chmod 666 /var/www and now when I go to move the directory under /var/www the directoreis now shw up as files. Did I screw something up?

Thx
John

---

### Post by SlugSlug on 2012-02-20
Directory's need to be executable 

```
sudo chmod +x /var/www -R
```


after that you can use 

```
gksudo nautilus &
```

to open a file browser with root perms (so u can copy your stuff to /var/www)

---

### Post by bacobits9982 on 2012-02-20
Thx.

John

---

