---
title: "[SOLVED] How do I remove an entire directory?"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by nothingspecial on 2008-07-11
Made a cock up and want to start something again. Bit scared of sudo rm and want to get it right.
Thanks

---

### Post by RavUn on 2008-07-11
sudo rm -rf /path
It won't prompt you to enter yes or no to delete, so you want to make sure you have the path right.

You may want to read this to know about the rm command:
[http://ubuntuforums.org/announcement.php?f=326](http://ubuntuforums.org/announcement.php?f=326)

If it's a folder in your home directory you can do 
```

sudo rm -rf ~/directory

```

I think you have to use -rf to delete directories.. but I could be wrong.  Or, you can open nautilus and right-click the folder and delete.

---

### Post by Canis familiaris on 2008-07-11
A safer approach:

In terminal:
```
gksudo nautilus
```

Browse in Nautilus and delete the folder.

---

### Post by nothingspecial on 2008-07-11
Just to check, does this look right -
```

sudo rm -rf /media/New\ Volume/mp3
```
Thanks

---

### Post by tjwoosta on 2008-07-11
-r means recursively (every directorory or file within will be deleted)
-f means forcefully  (self explaning)

-rf is the combination

---

### Post by nothingspecial on 2008-07-11
> **Anurag_panda said:**
> A safer approach:

In terminal:
```
gksudo nautilus
```

Browse in Nautilus and delete the folder.

Of course. I knew that:roll:

---

### Post by Dougie187 on 2008-07-11
Keep in mind too, you dont need the sudo unless the directory is owned by root.
Only do this if it is owned by root, It won't really hurt anything if its not owned by root, but then if you type something wrong like your path is "/ temp" or something like that, you won't totally f up your whole system.

---

