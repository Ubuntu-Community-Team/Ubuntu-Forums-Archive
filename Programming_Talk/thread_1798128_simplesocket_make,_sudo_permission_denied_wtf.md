---
title: "simplesocket make, sudo permission denied wtf?"
date: 2011-07-05
forum: Programming Talk
---

### Post by Pierrick584 on 2011-07-05
Hello, i'm trying to install simplesockets, and as they suggested on their website, i runned their make command in sudo, here's the command and the output...


```
sudo **make** **BUILD=Release** **&&** **make** **install**
```

```
cp: cannot create regular file `/usr/local/include/ActiveSocket.h': Permission denied
cp: cannot create regular file `/usr/local/include/Host.h': Permission denied
cp: cannot create regular file `/usr/local/include/PassiveSocket.h': Permission denied
cp: cannot create regular file `/usr/local/include/SimpleSocket.h': Permission denied
cp: cannot create regular file `/usr/local/include/StatTimer.h': Permission denied
make: *** [install] Error 1

```


Gotta say i'm not familiar to seeing "permission denied" as root, wtf is wrong with that?

---

### Post by TwoEars on 2011-07-05
Well, firstly, this is the wrong sub forum, and secondly, your second command is not run as root.

```
sudo make BUILD=Release && sudo make install
```
would probably fix that.

---

