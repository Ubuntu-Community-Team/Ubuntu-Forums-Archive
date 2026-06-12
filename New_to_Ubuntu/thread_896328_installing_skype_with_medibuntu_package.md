---
title: "installing skype with medibuntu package"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by acerunner on 2008-08-21
hi, new to ubuntu.

i'm trying to install skype by following the steps provided in this wiki page:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

this command works:
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

however this command fails:
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

error:
E: Type '--00:03:56--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

what does that mean?

and then if i try to open the synaptic package manager, i get this:
E: Type '--00:03:56--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by plucky on 2008-08-21
See this [thread](http://ubuntuforums.org/showthread.php?t=847444&highlight=medibuntu) to fix your problem with the Medibuntu repository.


Good Luck

---

### Post by satir.satir on 2008-08-21
just tape in terminal:
```
sudo apt-get install skype
```

---

### Post by acerunner on 2008-08-21
thanks! it worked

---

