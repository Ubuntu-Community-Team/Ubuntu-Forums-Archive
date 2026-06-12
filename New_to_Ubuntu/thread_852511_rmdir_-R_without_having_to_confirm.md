---
title: "rmdir -R without having to confirm"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by ben22 on 2008-07-07
high what do I have to add to

```
rmdir -R folder
```  to delete a folder so that I do not have to confirm the deletion process manually for each file?

---

### Post by AnarkistNZ on 2008-07-07
Use this command

```

rm -rf /folder/

```

---

### Post by txcrackers on 2008-07-08
[COLOR="Red"]**WARNING!**[/COLOR] When you do this, the file system will *permanently* delete the named folder. If you make a mistake, it is a long and painful process to try to recover - if you even can. I would strongly recommend sticking to your UI file-browser and moving files into the Trash.

Use this **only** if you're **absolutely** sure you want the folder removed.

---

