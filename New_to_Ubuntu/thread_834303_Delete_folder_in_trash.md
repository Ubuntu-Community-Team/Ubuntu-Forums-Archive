---
title: "Delete folder in trash"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by drrwhistle3 on 2008-06-19
I have made a copy of a CD and to do so I copied to a folder then copied back to a new cd.  I was successful however when I dragged the new folder to trash and the tried to empty the trash it won't delete.  The permissions are read and execute on all the files but I can not change to read write execute.  Nor will they delete.  Is there a way to do it?

---

### Post by Tomatz on 2008-06-19
> **drrwhistle3 said:**
> I have made a copy of a CD and to do so I copied to a folder then copied back to a new cd.  I was successful however when I dragged the new folder to trash and the tried to empty the trash it won't delete.  The permissions are read and execute on all the files but I can not change to read write execute.  Nor will they delete.  Is there a way to do it?

Open a terminal and type:


```
gksu nautilus
```


Then you will be able to delete the file in the nautilus window that pops up as it will have root privelages ;)

---

