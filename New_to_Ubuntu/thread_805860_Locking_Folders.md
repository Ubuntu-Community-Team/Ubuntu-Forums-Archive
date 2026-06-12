---
title: "Locking Folders"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by appoloin on 2008-05-24
is there anyway i can lock specific folders "passwording"

---

### Post by cdtech on 2008-05-24
You can do it with "sudo chmod -R 700 /folder", this will allow only the owner of the folder to view, execute, or even read the folder.

Or use permissions to set folder permissions per user.

Hope this helps......

---

### Post by barnex on 2008-05-24
You can also create an encrypted copy of a directory/file. If you've installed gnupg and seahorse, you can right-click on a file and simply choose 'encrypt'. You will first need to create an encryption key with seahorse, which is easy.
Not sure if this is exactly what you are looking for but I hope it helps.

---

### Post by ~E3016~ on 2008-05-24
> **cdtech said:**
> You can do it with "sudo chmod -R 700 /folder", this will allow only the owner of the folder to view, execute, or even read the folder.

Or use permissions to set folder permissions per user.

Hope this helps......

agreed..., but it can be done without 'sudo' too..

---

