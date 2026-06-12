---
title: "[SOLVED] garbage bin"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by davarse on 2008-08-01
hi all, i have very annoying problem...
i deleted some movies in my computer and when i want to empty the garbage bin it does want to empty it, it says that error occurred in deleting some files.. it's bin annoying and i really want to delete it, it just take too much space... is there any way to delete it, maybe force to delete it? i also tried to move the files out of garbage bin but it doesnt do either..
much appreciate for the help...

---

### Post by iaculallad on 2008-08-01
Drop on your terminal and issue the command below:

```
sudo rm -rf /home/your_user_name/.local/share/Trash/*
```

---

### Post by superbenny on 2008-08-01
Yes this will work. I know everyone says dont run commans with sudo rm -rf in it, but in this case, you want to force the delete of everything in the trash, which is what this command does. So go for it.

---

