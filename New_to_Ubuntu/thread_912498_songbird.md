---
title: "songbird"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by antgul338 on 2008-09-06
how do i install from a tar.gz file?

---

### Post by wolfen69 on 2008-09-06
just go to [www.getdeb.net](www.getdeb.net) and search for songbird. it is a 1 click install.

---

### Post by whizbaby on 2008-09-06
try
tar xfvz targzfile.tar.gz
if that gives you a directory named targzfile go there (cd targzfile) and look if there isnt a .deb file (ls)
If there is one, do
sudo dpkg -i name-of-the-file.deb
Greetz

---

### Post by 7raTEYdCql on 2008-09-06
Just brief you on it
In the beginning install build-essential.
First extract the tar.gz
Then cd to the file in terminal
Then ./configure (after the depenencies are satisfied)
Then make
Then make install.

That will do it for you.

---

### Post by 7raTEYdCql on 2008-09-06
Install build essential either from cd or
```
sudo apt-get install build-essential
```

This is required to compile  code.

---

