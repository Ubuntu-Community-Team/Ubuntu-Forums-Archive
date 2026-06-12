---
title: "Cannot Access Software Updater"
date: 2017-02-02
forum: New to Ubuntu
---

### Post by kathokennedy on 2017-02-02
Error reads as follows

E: Encountered a section with no Package: header 
E: Problem with MergeList /var/lib/apt/lists/za.archive.ubuntu.com_ubuntu_dists_trusty_universe_i18n_Translation-en%5fZA 
E: The package lists or status file could not be parsed or opened. 
E: _cache->open() failed, please report.

---

### Post by wildmanne39 on 2017-02-02
Please do:
```
sudo rm /var/lib/apt/lists/* -vf
```

The first command will remove the damaged list and when you run the second command it will replace it with a new list.

```
sudo apt-get update
```

---

### Post by kathokennedy on 2017-02-02
Thanks so much. Seems to have solved the problem. Regards Katherine

---

### Post by wildmanne39 on 2017-02-02
Your welcome, please use thread tools at the top of the page to mark the thread solved!

---

