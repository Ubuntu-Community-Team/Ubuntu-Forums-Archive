---
title: "Trying to upload files from an old hard drive via USB. Getting permission error"
date: 2012-05-28
forum: New to Ubuntu
---

### Post by lupulin on 2012-05-28
So as the title says. I bought a new computer a while ago and I'm finally trying to get all my old pictures etc from the old computer-drive. I bought a converter so I can plug the old drive into the new computer via USB. My last computer was also an Ubuntu computer. I can see the drive is mounted, and I can see it in /media in the terminal, but when I try to access files to copy them it says "You do not have the permissions necessary to view the contents". 

Is there a way for me to change the use/permissions of the old drive so I can copy from it? Currently using Ubuntu 10.10 on the current computer.

---

### Post by ajgreeny on 2012-05-28
You can move or copy the files with command ```
gksudo nautilus
``` which will open nautilus with root permissions.

---

### Post by lupulin on 2012-05-28
> **ajgreeny said:**
> You can move or copy the files with command ```
gksudo nautilus
``` which will open nautilus with root permissions.

 Nautilus did open and I can see the folders without the 'X' over them but when trying to copy it says "error opening files: permission denied"

---

### Post by lupulin on 2012-05-28
Update: I googled some more and used
```
 sudo chown -R user:user /media/actual location of media
```and that took care of it.

---

