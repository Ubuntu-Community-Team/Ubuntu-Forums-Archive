---
title: "error Installing deb files  11.04"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by mokman on 2011-10-17
"sudo dpkg -i gdebi_0.7.0_all.deb "
"sudo dpkg -i ark_4.6.2-0ubuntu1_i386.deb"

Tried above command on 11.04, but the error was_
"cannot access archive: No such file or directory
Errors were encountered while processing:
 ark_4.6.2-0ubuntu1_i386.deb"

The files were in Downloads folder and using 11.04 from pendrive.

Help please

---

### Post by mcduck on 2011-10-17
Have you actually changed your directory to the Downloads directory before running the commands?

```
cd ~/Downloads
sudo dpkg -i gdebi_0.7.0_all.deb
```

or:
```

sudo dpkg -i ~/Downloads/gdebi_0.7.0_all.deb
```

---

