---
title: "Error while moving:  Permission Denied"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by klemperal on 2008-08-08
hi guys,

I moved some files from an external hd to my Ubuntu desktop and it seems that there is some sort of permission problems.  I can't move the files off my desktop where I want them without getting a permission error.  The folders in question have a lock emblem on them if that is any help.  Let me know if you can help.

thanks

---

### Post by ad_267 on 2008-08-08
Can you go to Applications - Accessories - Terminal and post the output of "ls -l ~/Desktop"

That will show the files on the desktop and the permissions set.

If you moved the files as root they are probably owned by root so you don't have permission to move them.

---

### Post by InfinityCircuit on 2008-08-08
Open up a terminal (Applications -> Accessories -> Terminal) and type the following commands:

```
cd ~/Desktop
sudo chmod -R 755 *
sudo chown -R $USER:$USER *

```

This will make the files executable and changeable by your user.  If you want them to just be rw but not executable, then use "644" instead of "755"

---

### Post by klemperal on 2008-08-08
thanks a lot guys.  worked like a charm

---

