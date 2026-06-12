---
title: "how backup my packages"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by lio_013 on 2008-05-30
now i have the ubuntu on a cd and i download a lot of packages 
I'm afraid if i lost the system i will have to re download every thing so how can i backup my packages for every format and installation
:confused::confused::confused:

---

### Post by iaculallad on 2008-05-30
> **lio_013 said:**
> now i have the ubuntu on a cd and i download a lot of packages 
I'm afraid if i lost the system i will have to re download every thing so how can i backup my packages for every format and installation
:confused::confused::confused:


If the packages you mean are packages downloaded through apt-get, then you can backup those using the APTonCD utility.

Packages are copied to your /var/cache/apt/archives

Code:

```
sudo apt-get install aptoncd
```

---

### Post by Ptero-4 on 2008-05-30
You can install and use aptoncd. This app allows you to make a repository out of a bunch of debian packages (provided that all the needed packages have been downloaded) and format it to be burned to a CD (which after reinstalation can be added with the apt-cdrom --add command).

---

