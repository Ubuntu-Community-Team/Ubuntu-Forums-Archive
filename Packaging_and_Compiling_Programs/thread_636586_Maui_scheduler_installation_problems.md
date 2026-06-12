---
title: "Maui scheduler/ installation problems"
date: 2007-12-10
forum: Packaging and Compiling Programs
---

### Post by osaka_dude on 2007-12-10
hello,i m not sure if im in the right blog.
has anyone used the Maui scheduler with ubuntu gutsy?
 [http://clusterresources.com/maui](http://clusterresources.com/maui)
i tried "./ configure" with the Wiki and Bamboo resource managers,
configure was successful,but when i `make install` i get the error 
`chmod: cannot access `/usr/local/maui/spool': No such file or directory
make[1]: *** [install] Error 1`
any luck?
harry

---

### Post by dholbach on 2007-12-10
```
sudo make install
```

maybe?

---

### Post by osaka_dude on 2007-12-11
thnx,i was missing a resource manager
now i succeeded in installing.

---

### Post by brendanh21 on 2008-01-25
i had to edit the makefile in src/server and expand the mkdir command into separate ones for each listing

that worked

---

