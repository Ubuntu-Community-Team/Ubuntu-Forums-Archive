---
title: "Operation not supported error using ntfs-3g"
date: 2017-04-30
forum: New to Ubuntu
---

### Post by gege3043 on 2017-04-30
I forgot the password to windows 10 on my computer so I decided to load a live usb of Ubuntu to gain acess again. My plan was to rename cmd.exe and Utilman.exe to gain cmd access on the login screen so I could change the password. However, after mounting the drive in Ubuntu when i try to rename any files in System32, I get the error "Sorry could not rename 'Utilman.exe' to 'cmd1.exe': Error renaming file: Operation not supported".

---

### Post by Xian on 2017-04-30
> **gege3043 said:**
> However, after mounting the drive in Ubuntu when i try to rename any files in System32, I get the error "Sorry could not rename 'Utilman.exe' to 'cmd1.exe': Error renaming file: Operation not supported".

What mount options did you use for the drive? It sounds as if the user has no write permissions.

---

### Post by gege3043 on 2017-04-30
Unfortunatly it looks as if the drives are not even showing up at all right now :(
I'll see what i can do.

---

### Post by gege3043 on 2017-04-30
Ok I got it and I was able to delete files that would have been on the C:/ in windows

---

