---
title: "creating a hard link to a network file"
date: 2012-11-10
forum: New to Ubuntu
---

### Post by hookitup on 2012-11-10
so here is my situation,

i have a index.html file on my ubuntu server that i would like to link to a network share on my windows computer so i can use CS5 to edit this file , i have mounted the windows cifs share in the /mnt/ directory, when i run command ```
ln index.html /mnt/webdap/prod/index.html

```
i get the following error
```
ln index.html /mnt/webdap/prod/index.html
ln: failed to create hard link `/mnt/webdap/prod/index.html' => `index.html': Invalid cross-device link
```

im assuming it doesn't like the fact that its a network share and may get corrupt if connection to network share is lost and file is updated or whatever.

is there a way around this or what?

---

### Post by HiImTye on 2012-11-10
you can try a soft link, it should behave more or less the same as a hard link, except for file deletion. I don't know if it will solve the problem or not, to be honest

---

### Post by hookitup on 2012-11-10
i figured it out, its a symblic link, with command ```
ln -s
```
idk if this will actually work for production but i tested it and it worked just now so hopefully all is good.

---

### Post by jerome1232 on 2012-11-10
fyi, hard links only work on the same file system as each other.

---

