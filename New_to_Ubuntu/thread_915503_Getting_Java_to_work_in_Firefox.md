---
title: "Getting Java to work in Firefox?"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by meepster on 2008-09-09
I am running kubuntu 8.04 and Firefox and trying to get Java to work.  I installed the Sun Java 6 browser plugin through the package manager (Adept Installer), but Firefox still does not recognize it; when I try to open a web page with java on it, it does not load and tells me to "download plugins", which I presumably already have.

Thanks in advance for the help and advice.

---

### Post by WindowsNudge on 2008-09-09
I had the same problem with ubuntu until I did an uninstall on the default java plug ins that came with the os
If you can done that with yours try it it should work after restart.

---

### Post by meepster on 2008-09-09
> **WindowsNudge said:**
> I had the same problem with ubuntu until I did an uninstall on the default java plug ins that came with the os
If you can done that with yours try it it should work after restart.

Alas, no.  Still the same trouble.  Thanks for the reply, though; I appreciate it.

---

### Post by jamesstansell on 2008-09-11
Does this help?
```
$ sudo update-java-alternatives -s java-6-sun
```

Also, is it Firefox 2 or Firefox 3?

---

