---
title: "permission denied?!"
date: 2007-05-26
forum: Programming Talk
---

### Post by md5hash on 2007-05-26
im geting this error i dont know why. i already set the permission to 777

Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required '/home/yoshi/www/portal/index.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

---

### Post by Metacarpal on 2007-05-26
What did you set to permissions 777?

It may be a question of directory access - if a file in a directory under your home directory is marked 777, that doesn't necessarily mean that another user can access it.  If they don't have read access to the folders leading to the file, they can't access the file.

NOTE: don't change the permissions on your home directory!  This can keep you from being able to log in.

The best thing you can do is either move that .php file elsewhere, or create a symlink (aka a soft link) to the folder containing your php files from somewhere outside of the /home directory.

---

### Post by md5hash on 2007-05-28
i tried moving it to another location.. /var/www/portal/, but im stll getting the same error..

---

