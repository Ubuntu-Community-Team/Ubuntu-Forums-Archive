---
title: "[SOLVED] How do I fix a broken Synaptic?  Same error everytime I install a package."
date: 2008-08-10
forum: New to Ubuntu
---

### Post by crjackson on 2008-08-10
Okay, so I thought an error I was getting was related to a specific package, but as it turns out I'm now getting the same error on all package installs.

How can I fix this without a fresh install?  Please have a look at this thread in order to see the uploaded images. [http://ubuntuforums.org/showthread.php?t=885267](http://ubuntuforums.org/showthread.php?t=885267)

---

### Post by Lerxst51 on 2008-08-10
I'm assuming it's Aptitude itself, but if you could check see if you get the same error in terminal:

```
sudo apt-get install zoneminder
```

---

### Post by crjackson on 2008-08-10
Sorry for this thread.  I can't find a way to delete it.  It seems the problem is fixed by removing the problematic package (ZoneMinder) as referenced by a previous thread.  I didn't know this problem was caused by the other one.

---

### Post by crjackson on 2008-08-10
> **Lerxst51 said:**
> I'm assuming it's Aptitude itself, but if you could check see if you get the same error in terminal:

```
sudo apt-get install zoneminder
```

No it's not synaptic (I think).  The problem was fixed by REMOVING the zoneminder package.

And yes, I did get the same error when attempting to install by terminal.

---

