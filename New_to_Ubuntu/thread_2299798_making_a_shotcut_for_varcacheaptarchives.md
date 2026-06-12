---
title: "making a shotcut for /var/cache/apt/archives"
date: 2015-10-21
forum: New to Ubuntu
---

### Post by thexnightmare on 2015-10-21
Dear,
How can I make a shotcut "/var/cache/apt/archives" in the Desktop?
Thanks

---

### Post by tgalati4 on 2015-10-21
Not sure why this would be useful.

/var/cache/apt/achives is a system directory of Debian packages installed on your system. It is protected with root access.

```
cd
cd Desktop
sudo ln -s /var/cache/apt/archives
ls -la

```

---

### Post by thexnightmare on 2015-10-21
Thanks

---

