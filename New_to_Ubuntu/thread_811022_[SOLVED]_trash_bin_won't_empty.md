---
title: "[SOLVED] trash bin won't empty"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by JimmyJim on 2008-05-28
I have some seemingly empty folders in my trash bin that won't go away. When I click "empty" nothing happens. When I try to delete an individual folder, I get a message saying "Error removing file: Directory not empty".

I'm not sure whats wrong; any help is greatly appreciated.

---

### Post by Arthur Archnix on 2008-05-28
Lots of threads on this on the forums already, a little searching might have saved you the bother of waiting to hear a response.

First thing to try is to manually remove the folders from the trash can by going to the trash can in the terminal. On hardy its ~/.local/share/Trash  go there by typing ```
cd ~/.local/share/Trash/files
``` and then type```
ls
```  that second command will print out a list of everything in the trash. Let's say it shows you>  . .. folder1 folder2  then you would do this to get rid of them
```
sudo rm -R folder1 folder2
```There are other ways to do it, but that's a bit safer. If you're on Gutsy the trash is in a different place. Maybe ~./Trash?

This took me a while to type. Chances are its been answered already. Oh well.

---

### Post by SlappyPappy on 2008-05-28
> **Arthur Archnix said:**
>  If you're on Gutsy the trash is in a different place. Maybe ~./Trash?



Perhaps if you're unsure, you should have looked it up? I'm sure there are threads about this already.  ):P

---

### Post by JimmyJim on 2008-05-28
OK I did this, as posted in another thread, and it worked:

```
sudo rm -rf ~/.local/share/Trash
```

---

