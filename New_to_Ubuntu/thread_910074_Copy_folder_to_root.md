---
title: "Copy folder to root"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by Zeck on 2008-09-04
Hi all,
How to copy folder to root ? For example i wanna copy aa folder copy to /var/www.

---

### Post by rogeriopvl on 2008-09-04
you have to use the sudo command, or open nautilus with sudo and copy paste the folder.

```
sudo cp -R /path_to_folder_to_copy/ /var/www/
```

or

```
sudo nautilus
```

---

