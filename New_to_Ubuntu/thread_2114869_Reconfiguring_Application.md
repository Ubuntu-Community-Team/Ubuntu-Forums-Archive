---
title: "Reconfiguring Application"
date: 2013-02-11
forum: New to Ubuntu
---

### Post by Paradigm Arsenist on 2013-02-11
Sometimes, I mess up my configuration files for an application or other set of software in my home directory and want to start again. I have sometimes deleted directories like ~/.xfce4 , but this of course only deletes some Xfce4 files and leaves others, making a mess.

Is there a clean way to reconfigure an application? Thanks.

---

### Post by SlugSlug on 2013-02-11
A couple

```
sudo dpkg-reconfigure APP
```or purge it and reinstall

```
sudo apt-get remove --purge APP
```

---

