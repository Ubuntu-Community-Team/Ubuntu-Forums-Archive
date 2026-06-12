---
title: "[SOLVED] Don't have permission to save file in this folder"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by Vithant on 2008-05-13
How do I get permission to save a php file in var/www?

---

### Post by drs305 on 2008-05-13
```
sudo cp filename /var/www/filename
```

---

### Post by sam_delta on 2008-05-13
click on ALT+f2 and type 
```
gksudo nautilus
```

a file browser WITH root (administrator) permissions will open, use that to copy the files.

sam

---

### Post by sunstriker on 2008-05-13
You could chown this folder to yourself if u use it a lot. I don't think it's a security issue:

To change the owner (so you can write to it)
```
sudo chown -R yourusername /var/www/
```
Set permissions so that you can read/write/execute and other can read and execute (others = apache)
```
sudo chmod -R 755 /var/www/
```

---

### Post by Joeb454 on 2008-05-13
I'd prefer doing a soft link using a folder in my /home directory. Say I created a folder called "web" in my home folder, I would run the following from a terminal ```
sudo ln -s /var/www/ ~/web/
```

---

### Post by Vithant on 2008-05-13
I will be happy to mark it solved, how do I do that?
 Thanks Jim

---

### Post by Joeb454 on 2008-05-13
In thread tools at the top of this page, click that, and then choose mark as solved :)

---

