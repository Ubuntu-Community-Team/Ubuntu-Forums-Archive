---
title: "[SOLVED] Can't put files in the trash"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by lavadisco on 2008-11-21
I have Intrepid and Win XP on my laptop. After I first installed Intrepid, I couldn't put any files in the trash, I could only permanently delete them. After searching through numerous threads, I finally tweaked things so that stuff on the windows partition, when deleted in Intrepid, would go to the trash. However, I still cannot put items in the trash from my Intrepid partition. I have searched the forums and tried tons of stuff, but nothing seems to work. I would appreciate some guidance here if anybody's got any ideas.

---

### Post by jrib on 2008-11-21
paste the results including the command you ran from:
```
find ~/.config ~/.local ! -user $USER
```

---

### Post by rbprogrammer on 2008-11-21
Ok, first it seems like (from my understanding of what you wrote) that you did a fresh install of intrepid and you were never able to send stuff to the trash bin.

If that is correct, it should rule out the possibility of a permissions error on your trashbin folder.  But just in case, what is the output of this command:
```

ls -l ~/.local/share/Trash

```

That should give light as to what the permissions are on the trash bin.

---

### Post by lavadisco on 2008-11-23
Here's what I get when I run those commands in a terminal window:

```
lavadisco@lavadisco:~$ find ~/.config ~/.local ! -user $USER
/home/lavadisco/.local/share/Trash/files

```

and

```
lavadisco@lavadisco:~$ ls -l ~/.local/share/Trash
total 8
drwxr-xr-x 2       777 root      4096 Nov 18 21:39 files
drwx------ 2 lavadisco lavadisco 4096 Nov 20 22:36 info
```

Anything in there I should change?

---

### Post by jrib on 2008-11-23
> **lavadisco said:**
> 
Anything in there I should change?

```
sudo chown -R $USER: ~/.local/share/Trash
```

---

### Post by lavadisco on 2008-11-23
That did it, thanks!

---

