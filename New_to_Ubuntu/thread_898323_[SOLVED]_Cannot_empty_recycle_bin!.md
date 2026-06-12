---
title: "[SOLVED] Cannot empty recycle bin!"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by ooobuntooo on 2008-08-23
Cannot empty recycle bin, permission denied!

Over 30GB of stuff is in there, I want it deleted!

---

### Post by iaculallad on 2008-08-23
> **ooobuntooo said:**
> Cannot empty recycle bin, permission denied!

Over 30GB of stuff is in there, I want it deleted!

On your terminal:

```
sudo rm -rf /home/username/.local/share/Trash/*
```

or

```
sudo rm ~/.local/share/Trash/files/*
```

---

### Post by sisco311 on 2008-08-23
Open a terminal and run the following command:
```
sudo chown -R $USER:$USER ~/.local/share/Trash/
```then try to empty the recycle bin.

---

### Post by thebigbluecan on 2008-08-23
Can you open it and see the files? If so highlight them all and right click and "Delete from trash".

---

### Post by bubba_169 on 2008-08-23
Try pressing alt+F2 and run 'gksu nautilus'. This will run nautilus with full permissions so be careful what you do in here...

When nautilus is open press ctrl+h to show hidden files and folders, then go to filesystem/home/yourname/.local/share/trash and you should see 2 folders named files and info. If you empty these folders you should be rid of those files in your trash.

If you have other partitions mounted you may also want to clear their trash too so go to the root of the partition, eg sda2 might be mounted at /media/sda2, and look for a folder called trash-#### where ### is a number. Do the same with this folder as you did with the others to fully clear your trash!

---

### Post by ooobuntooo on 2008-08-23
I tried all that, but none of it worked. :(
It says "Permission Denied" but the file permissions say I have I own the files, rather that the root admin.

---

### Post by ooobuntooo on 2008-08-23
Problem solved i did.

Alt F2 and typed "gksudo nautilus" and navigated to the directory that you told me about and deleted the files!

I worked thanks!!

---

### Post by sisco311 on 2008-08-23
Cool!
If your thread is solved, please mark it solved by selecting 
**Mark this thread as solved** from the **Thead Tools**.

---

