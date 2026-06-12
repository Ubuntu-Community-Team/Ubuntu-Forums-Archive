---
title: "PHPMyAdmin need help ( Special Case )"
date: 2010-01-28
forum: Programming Talk
---

### Post by sukatoa on 2010-01-28
I have installed lampp
able to browse localhost etc2x

I have also installed mysql before the lampp, i would like to use that mysql server instead of the packaged mysql in lampp

I try to connect directly, without password on root, i got this one

The server is not responding (or the local MySQL server's socket is not correctly configured) 

I dont know where to start searching this configuration file?

Any advice/instructions? (noob here)

---

### Post by Hellkeepa on 2010-01-28
HELLo!

You need to figure out where the "mysql.sock" (or "mysqld.sock") file is stored, and where PHP and/or phpMyAdmin expects to find it. Create a symlink to fix this issue.

Also, I would highly recommend installing the LAMPP-stack via the package manager. This will ease off a LOT of headaches for you later on.

Happy codin'!

---

