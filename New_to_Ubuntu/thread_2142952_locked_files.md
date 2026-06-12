---
title: "locked files"
date: 2013-05-07
forum: New to Ubuntu
---

### Post by night116 on 2013-05-07
i have just reinstalled 12.04 ubuntu on my new main computer and i have my old home directory backed up on my usb hard drive , but when i go to copy them with gksudo nautilus to get access to root. when i copy over the home files all the files are locked. how do i fix it so they are not locked.

---

### Post by miegiel on 2013-05-07
The copied files are probably owned by the root user. To check go to the directory in the terminal and run
```
ls -al
```

To change it to be owned by you (the "normal" user) do
```
sudo chown -R ***user***:***user*** /home/***user***/***directory***
```
where ***user*** is your user name and ***directory*** is the directory with the files.

---

### Post by night116 on 2013-05-07
thanks heaps I will try it out

---

### Post by grahammechanical on 2013-05-07
You can also use gksudo nautilus and go to Privileges>Permissions. You can set the Group and Others permissions. You may even be able to change the permissions for enclosed files. Files inside folders. which is a lot faster than changing permissions for every folder and file one by one. I don't know if you can do this in 12.04 but you most certainly can do in 13.04. I did it recently when I installed a new hard disk and moved my data files on to it.

Regards.

---

