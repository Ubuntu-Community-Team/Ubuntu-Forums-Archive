---
title: "package manager not working"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by DGZDGZ on 2008-11-01
When i try to install a program i am often presented with an error message saying that the installation did not fully complete. This has happened most recently with amarok, which wont open. i've tried removing it and reinstalling it, but it's still the same.

the following error code shows at the end of the download:

E: openjdk-6-jre-headless: subprocess post-installation script returned error exit status 1
E: openjdk-6-jre: dependency problems - leaving unconfigured
E: icedtea-gcjwebplugin: dependency problems - leaving unconfigured


I feel like all i'm doing is constantly asking questions, for which i apologize- but can anyone help? 

Thanks

---

### Post by Martje_001 on 2008-11-01
Try in a terminal:
```
sudo apt-get install -f
```

---

### Post by DGZDGZ on 2008-11-01
hello, and thanks for the response.

That seems to have sorted out a lot of the broken packages, but strangely enough not amarok, but i'm just going to use rhythm box seeing as it's ok now.

thanks again

---

### Post by cosmoshell on 2008-11-01
sudo dpkg-reconfigure amarok

---

### Post by Martje_001 on 2008-11-01
Try Synaptic. It has solved a lot of problems for me in the past.

---

### Post by DGZDGZ on 2008-11-01
> **cosmoshell said:**
> sudo dpkg-reconfigure amarok

i tried this but it's still the same - the load box flashes up then disappears.


Martje_001- When you say try Synaptic, do you mean re-installing with Synaptic manager?

thanks for helping folks

---

### Post by Martje_001 on 2008-11-02
Yes, I do.

---

