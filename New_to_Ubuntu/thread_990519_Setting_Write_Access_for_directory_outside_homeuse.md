---
title: "Setting Write Access for directory outside /home/username"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by ZZQQ on 2008-11-22
I have my harddrive partitioned into 3 drives, one for windows, linux root directory and linux /home.  The partition with /home is an ext3 drive shared between windows and linux.  As a result I have many folders outside my /home/username directory (ex: I store all my mp3s in /home/mp3s).  The problem with this is that when I am logged in I don't have write access to any of these folders without super user privileges.  How can I enable access to these folders permanently without having to sudo everytime?

---

### Post by Soriano on 2008-11-22
```
sudo chown root.users /directory_name
sudo chmod 770 /directory_name
```

That's if I'm understanding your question correctly...

---

### Post by jyaan on 2008-11-22
So, you're saying that you want to be able to access everything under /home? This is easily done with chown.
```
sudo chown -R username /home
```

This makes you the owner of all the folders under /home. -R means recursive.

---

