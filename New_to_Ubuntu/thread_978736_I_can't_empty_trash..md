---
title: "I can't empty trash."
date: 2008-11-11
forum: New to Ubuntu
---

### Post by skysnow on 2008-11-11
I found a folder named "autorun.inf".When i wanted to delete it,it said the folder isn't empty. But i can't find any item in it.Anyone can help me.Thanks in advance.

---

### Post by bawilson2 on 2008-11-11
> **skysnow said:**
> I found a folder named "autorun.inf".When i wanted to delete it,it said the folder isn't empty. But i can't find any item in it.Anyone can help me.Thanks in advance.

The issue probably is that you don't have correct permissions on the file you want to delete.  Try going to:

```

cd /home/(username)/.local/share/Trash/files

```

From there you can run

```

sudo rm autorun.inf

```

That should delete the file.  

Check out this thread for more info.
[http://ubuntuforums.org/showpost.php?p=4581833&postcount=12](http://ubuntuforums.org/showpost.php?p=4581833&postcount=12)

---

