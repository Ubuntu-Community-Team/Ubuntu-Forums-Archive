---
title: "Trying to create new repository."
date: 2006-06-05
forum: Repositories &amp; Backports
---

### Post by sanderella on 2006-06-05
I just downloaded and installed Dapper yesterday, no problems.

Today I'm trying to install Realplayer in a new repository. I get this message - 

E: Type ‘[http://packages.freecontrib.org/ubuntu/plf’](http://packages.freecontrib.org/ubuntu/plf’) is not known on line 33 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

I'm just a newbie. Can anyone help me?

---

### Post by aysiu on 2006-06-05
Can you post the output of this command? ```
cat /etc/apt/sources.list
```

The lines should read: ```
deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
```

---

### Post by sanderella on 2006-06-05
This is what I get when I paste the command -cat /etc/apt/sources.list

"Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences."

---

### Post by aysiu on 2006-06-05
```
cat /etc/apt/sources.list
``` just lists what repositories you have.

The output you gave seems to have come from the command ```
sudo apt-get update
```

---

### Post by sanderella on 2006-06-05
My upgrade didn't install properly, I'm doing it again. Files missing.:(

---

