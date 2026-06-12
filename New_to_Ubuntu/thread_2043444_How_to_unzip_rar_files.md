---
title: "How to unzip rar files?"
date: 2012-08-16
forum: New to Ubuntu
---

### Post by asmith2306 on 2012-08-16
Hi,

I tried downloading Rar from [http://www.rarlab.com/download.htm](http://www.rarlab.com/download.htm) but how do you use it?  I did a make, make install and nothing happened.  I installed Ark as well from the package manager but that seems to hang when I try to extract a .rar file.

Thanks

---

### Post by ubudog on 2012-08-16
Have you tried unrar?

```
sudo apt-get install unrar
```

Then:
```
unrar x filename.rar
```

Hope that helps,
ubudog

---

### Post by asmith2306 on 2012-08-20
> **ubudog said:**
> Have you tried unrar?

```
sudo apt-get install unrar
```Then:
```
unrar x filename.rar
```Hope that helps,
ubudog

Hi, I got unrar to work but I had to use the full path to execute ie. usr/bin/unrar the install from apt-get didn't seem to add it to the path.  I think I may have tried to untar it from source so there is something still lying around that is interfering with a fresh install.

---

### Post by Paqman on 2012-08-20
Once you've install unrar you can also just right click > extract here.

---

