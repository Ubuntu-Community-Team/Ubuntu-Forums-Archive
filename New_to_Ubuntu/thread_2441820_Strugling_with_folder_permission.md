---
title: "Strugling with folder permission"
date: 2020-04-27
forum: New to Ubuntu
---

### Post by budan1976 on 2020-04-27
Hi 

I have ubuntu 18.04 installed in ec2 instance.

I have created a new user called subadmin and added the user in the www-data group.

```
sudo usermod -a -G www-data subadmin 
```

and then

```
sudo chmod -R g+w /var/www/staging
```

The folder permission is 

```
drwxrwxr-x+ 13 ubuntu www-data 4096 Apr 27 07:54 staging
```


And the file is 

```
-rw-rw-r-- 1 ubuntu www-data 623 Apr 27 08:12 /var/www/staging/readme.md
```

This user can create/edit/delete a new file but can't modify any existing folder or file.

Any help is highly appreciated. Thanks in advance.

---

### Post by TheFu on 2020-04-27
[https://ubuntuforums.org/showthread.php?t=2382965&highlight=working+chgrp](https://ubuntuforums.org/showthread.php?t=2382965&highlight=working+chgrp) explains.  The parent directory permissions control create/delete permissions on all child objects.

---

