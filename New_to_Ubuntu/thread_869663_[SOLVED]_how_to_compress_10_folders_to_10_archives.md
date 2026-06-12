---
title: "[SOLVED] how to compress 10 folders to 10 archives by one command"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by afeasfaerw23231233 on 2008-07-25
i need to compress each holder to an archive. it has nearly a hundred folders. how can i do this in a quickest way? i don't want to right click each --> "create archive.." that tooooo slow! thanks!

---

### Post by hyper_ch on 2008-07-25
write a shell script that loops through each directory name and compresses it.

---

### Post by afeasfaerw23231233 on 2008-07-25
sorry i don't know how to write a script! noob.....

---

### Post by sdennie on 2008-07-25
Try:

```

find . -maxdepth 1 -type d ! -name "." -exec echo "'{}'" \; -exec tar cf '{}.tar' '{}' \;

```

That will make a tar file for every directory in the directory it's run.

---

### Post by afeasfaerw23231233 on 2008-07-25
if i want it to be .zip or .rar then should it be 
find . -maxdepth 1 -type d ! -name "." -exec echo "'{}'" \; -exec zip cf '{}.zip' '{}' \;

---

### Post by sdennie on 2008-07-25
I'm not familiar with the syntax of zip but, it looks like you understand the find command I posted so, you may want to check the man page for zip and figure out the exact syntax zip uses to create an archive:

```

man zip

```

---

### Post by afeasfaerw23231233 on 2008-07-25
thanks. problem solved

---

