---
title: "Problem installing Python, permission error"
date: 2010-07-14
forum: Programming Talk
---

### Post by ilivlife on 2010-07-14
Hello
I am trying to install Python and I am running into some trouble. After reading most of last night on different languages, I choose Python and I also read how to install it.
Code Steps
./configure [worked]
make [worked]
make install [problem]
It says I need permission to install this.

[PHP]mike@mike-desktop:~$ make install
/usr/bin/install -c python /usr/local/bin/python2.7
/usr/bin/install: cannot create regular file `/usr/local/bin/python2.7': Permission denied
make: *** [altbininstall] Error 1
[/PHP]

Any help would be awesome.

---

### Post by diesch on 2010-07-14
You have to run make install as root:

```
sudo make install
```

If you don't need specifically Python 2.7 you can use the Python version that is installed by default on Ubuntu without installing anything.

---

