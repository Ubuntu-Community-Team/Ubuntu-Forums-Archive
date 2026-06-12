---
title: "xubuntu 12.04 installing nodjs ?"
date: 2013-04-30
forum: New to Ubuntu
---

### Post by klein5366 on 2013-04-30
hi 
i'm trying to install node js and from [this page]("https://github.com/joyent/node/wiki/Installing-Node.js-via-package-manager") it is telling me to creat a symlink /usr/bin/node to /usr/bin/nodejs but node is already  symlinked.

```
klein@lg1:~$ sudo ln -s /usr/bin/node /usr/bin/nodejs
ln: failed to create symbolic link `/usr/bin/nodejs': File exists

```
```
ls -l
lrwxrwxrwx 1 root   root          22 Apr 30 07:47 node -> /etc/alternatives/node
-rwxr-xr-x 1 root   root     8281904 Apr 24 01:11 nodejs

```
i'm not sure what to do?

---

