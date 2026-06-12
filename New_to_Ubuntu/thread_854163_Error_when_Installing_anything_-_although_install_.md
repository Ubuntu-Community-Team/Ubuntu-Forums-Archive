---
title: "Error when Installing anything - although install works"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by sekelly on 2008-07-09
I am getting the following error after the installation or uninstallation of any application or system update. Does anyone know what to do about it?

E: msttcorefonts: subprocess post-installation script returned error exit status 1

Any help is appreciated.

I am running Ubuntu 8.04 on a Lenovo T61, if that matters at all.

---

### Post by ibutho on 2008-07-09
Were you trying to install msttcorefonts? It looks like the post installation script for that package is not running successfully.

---

### Post by sekelly on 2008-07-09
Well, the installation processes may be trying to install the msttcorefonts package and failing, but I am not specifically trying to install that package.

Whenever I install anything using the Add/Remove Applications tool I get this error. I also get the error when I am doing system updates in the update manager.

I suppose it is trying to install the msttcorefonts package and failing, but I'm not sure what to do about this.

---

### Post by ibutho on 2008-07-09
Run a terminal and do
```
sudo dpkg --configure -a
```
After that try to install something. Does that help?

---

### Post by sekelly on 2008-07-09
> **ibutho said:**
> Run a terminal and do
```
sudo dpkg --configure -a
```
After that try to install something. Does that help?

I tried that, and I got returned

dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts

I'm stuck here... Thanks for the help though, I appreciate it.

---

### Post by ibutho on 2008-07-09
One thing you could try is uninstalling the package (purge it) and reinstall. Don't know if that will help.

---

### Post by sekelly on 2008-07-09
That didn't seem to work either. It seems like I am unable to connect to the sourceforge server for that particular download. I can't uninstall it, as I get the same error.

I can install applications fine, but this error just drives me bonkers, lol.

---

### Post by zvacet on 2008-07-09
>  It seems like I am unable to connect to the sourceforge server for that particular download.

Maybe server is down now.Try later.

---

### Post by sekelly on 2008-07-09
It doesn't seem to be down. I haven't been able to get this package for the last two days.

Also, I did the install at work side by side with a co-worker on a T60 (we are testing for enterprise level involvement) and he does not receive this error.

---

