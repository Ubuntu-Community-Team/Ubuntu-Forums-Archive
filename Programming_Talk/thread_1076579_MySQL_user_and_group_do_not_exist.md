---
title: "MySQL user and group do not exist"
date: 2009-02-21
forum: Programming Talk
---

### Post by Diabolis on 2009-02-21
If I execute groups and users, the "mysql" user and group do not appear. I need them because I changed the datadir and I have to chwon it. I tried this:

```
sudo apt-get --reinstall install mysql-server-5.0
```

and then:

```
sudo dpkg-reconfigure mysql-server-5.0
```

But the user and group are not being created.

How do I force mysql to make its user and group? I would like to avoid making them myself.

---

### Post by Diabolis on 2009-02-21
I made a mistake, the mysql user and group do exist, but I can't chown a folder.
I did this:
```
mkdir folder
chown -R mysql:mysql folder/
```

and when I do **ls -l** it is listed as beng in the root group and belongs to root :-S

---

### Post by Diabolis on 2009-02-21
After thinking about some time, I figured it out!

The problem is that my new folder is in a FAT32 partition and it doesn't support file permissions, so apparently by default all the files are owned by root and that can not be changed.

---

