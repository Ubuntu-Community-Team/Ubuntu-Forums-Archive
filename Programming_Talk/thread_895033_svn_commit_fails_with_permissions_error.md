---
title: "svn commit fails with permissions error"
date: 2008-08-19
forum: Programming Talk
---

### Post by AncientPC on 2008-08-19
I followed the instructions listed here:
[https://help.ubuntu.com/community/Subversion](https://help.ubuntu.com/community/Subversion)

The permissions is as follows:
/home/
```
total 500
drwxr-xr-x  3 root   root        8 2008-08-19 17:29 svn/

```

/home/svn/
```
total 0
drwxrwsr-x 7 www-data subversion 64 2008-08-19 17:30 myproject/
```

Both myself and www-data is in the subversion group, yet commit fails with permissions errors.

---

