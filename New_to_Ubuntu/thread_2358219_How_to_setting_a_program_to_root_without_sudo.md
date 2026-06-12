---
title: "How to setting a program to root without sudo?"
date: 2017-04-10
forum: New to Ubuntu
---

### Post by quiltshrimp on 2017-04-10
My user is superuser not root, 
I want to run a program as root but not use su or sudo, 
not use terminal to run too,
just run program, it will be root uthority.
I searched many datas, but can't find answer, 
please help me.

Thanks.

---

### Post by Impavidus on 2017-04-11
Are you really sure you want to run that program as root? Only do that with programs of which you're really sure they can do only one thing and do it very well.

You can edit the sudoers file: [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)
You can set it such that specific users can use a program as root with sudo, but without typing a password. You can even make a desktop file that prepends the sudo command automatically.

There's another way, but before posting dangerous commands on the forum, I'd like to know why you need automatic root permissions. Maybe there's a more secure alternative.

---

