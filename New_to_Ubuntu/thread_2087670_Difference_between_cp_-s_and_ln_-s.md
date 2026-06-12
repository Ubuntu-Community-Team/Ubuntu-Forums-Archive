---
title: "Difference between cp -s and ln -s"
date: 2012-11-24
forum: New to Ubuntu
---

### Post by KuRA96 on 2012-11-24
As the title says.

I know both used to make symbolic links, but is there any difference between cp -s and ln -s  ?

thanks in advance :)

---

### Post by mlentink on 2012-11-24
cp is the copy command, not used to make links.
You can quickly find what a commanc does by typing info in a terminal windows followed by the command, like:
```
info cp
```

---

### Post by ajgreeny on 2012-11-24
**cp -s** can be used to make a link to a file or files;** ln -s** would more commonly be used to make a soft link to a source folder from a destination folder.

I am sure there will be other differences that I'm not aware of, but that seems to be the main thing I can see.

---

