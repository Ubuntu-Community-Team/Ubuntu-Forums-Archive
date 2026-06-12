---
title: "Easiest way to remove programs?"
date: 2013-01-21
forum: New to Ubuntu
---

### Post by MICsteven on 2013-01-21
Is there an application or software i can use that easily removes unwanted programs or old files that I don't use? For example, I was downloading Borderlands through Wine with Steam. I cancelled the installation and now i have the remaining files. Best way to get rid of them besides manually finding each one and moving to trash?

---

### Post by sidzen on 2013-01-21
[PHP]sudo apt-get remove (pkg-name)     [/PHP]
[PHP]sudo apt-get remove --purge (pkg-name)[/PHP]

First command removes the package only
Second removes both package and its configuration files

---

### Post by deadflowr on 2013-01-21
> **MICsteven said:**
> Is there an application or software i can use that easily removes unwanted programs or old files that I don't use? For example, I was downloading Borderlands through Wine with Steam. I cancelled the installation and now i have the remaining files. Best way to get rid of them besides manually finding each one and moving to trash?

If they're WINE programs, open up your home folder and mark 'show hidden folders'(ctrl + h), wine is a hidden folder in there somewhere. Open it and look for your aborted program, simply delete.

---

### Post by mysteriousdarren on 2013-01-22
Are you looking for orphaned packages and old kernels? I use bleachbit and computer janitor to take care of alot. Warning though it your unsure about the packages this could make your machine unstable.

---

### Post by Bucky Ball on 2013-01-22
```
sudo apt-get autoremove
```

... but not sure if that will work with Wine programs as never used Wine.

---

