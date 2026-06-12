---
title: "Completely removing Avast Workstation For Linux?"
date: 2013-05-21
forum: New to Ubuntu
---

### Post by Treeant34 on 2013-05-21
Howdy:

There is a closed thread that partially describes how to completely remove Avast Workstation for Linux, but after performing the removal I still have a folder named .avast in my home folder.
 
It contains three folders (chest, log, moved) a text file (avastrc) and a 400.vps file that probably contains the definitions that were downloaded (I'm guessing from the file size). 

This makes me wonder what else was left behind...

How can I ascertain if there are any dependencies, config data etc left behind after purging the program?

Is it safe to manually delete the .avast folder?

Thx

T

---

### Post by Mariane on 2013-05-21
I think it is safe. You can try to look for anything called avast or Avast:
```

cd /
sudo find ./ -name *vast*

```
This will look for any name containing "vast", so it does not matter if the initial A is upper case or lower case.

---

### Post by Treeant34 on 2013-05-22
> **Mariane said:**
> I think it is safe. You can try to look for anything called avast or Avast:
```

cd /
sudo find ./ -name *vast*

```
This will look for any name containing "vast", so it does not matter if the initial A is upper case or lower case.

Thanks Mariane, appreciate your help, I just turfed the folder (nothing exploded)...

The search syntax was helpful...

Cheers

---

