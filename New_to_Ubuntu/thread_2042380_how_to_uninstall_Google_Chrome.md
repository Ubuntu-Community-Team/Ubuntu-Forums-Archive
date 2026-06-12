---
title: "how to uninstall Google Chrome?"
date: 2012-08-14
forum: New to Ubuntu
---

### Post by Old-un on 2012-08-14
Have tried to un-install Google Chrome via the terminal using the command:

```

sud apt-get purge google chrome

```

and i get this output:  

E: Unable to locate package google
E: Unable to locate package chrome

---

### Post by FatFrog on 2012-08-14
you need to specify the package correctly, try the following:

sudo apt-get purge google-chrome-stable

---

