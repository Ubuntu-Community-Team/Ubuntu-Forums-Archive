---
title: "I got the drive to mount but I can't"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by captgadget on 2008-05-17
create a folder. It tells me I don't have permission. How do I fix this?

Thanks

---

### Post by macaholic on 2008-05-17
Can you make a folder with:```
sudo mkdir
```
Also, can you change the folder permissions by right-clicking it and selecting properties?

---

### Post by captgadget on 2008-05-17
I got this:  sudo mkdir
mkdir: missing operand
Try `mkdir --help' for more information.

---

### Post by macaholic on 2008-05-17
Sorry, you have to add the name of the directory you want to make after mkdir.

---

### Post by captgadget on 2008-05-17
SOLVED!!!! Used gksudo nautilus

---

