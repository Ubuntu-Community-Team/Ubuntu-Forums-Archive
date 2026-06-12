---
title: "[SOLVED] AcetoneIso2 installations problems"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by Zularan on 2008-10-18
Using Intrepid 8.10 and have used Acetone to mount cd images in the past.  I'm trying to install [AcetoneIso2]("http://www.acetoneiso.netsons.org/") and get this error:

```
Error: Dependency is not satisfiable: fuseiso
```

Doing ```
sudo apt-get install fuseiso
```
fails saying 'Couldn't find package fuseiso'

Any ideas? Alternatively are there any programs similar to daemontools/alcohol120 for Windows that make mounting iso/mdf easy ?

---

### Post by Zularan on 2008-10-18
Nevermind.. fixed, repositories were incorrect.

---

### Post by RandyRandola on 2008-10-25
Which repositories?

---

### Post by Zularan on 2008-10-26
My ISP has a mirror of the Intrepid repos which I had it set to which is free for me. When I changed it back to the main ubuntu one Synaptic search had Acetone/fuseiso in it.  I think my ISP wasn't as uptodate as the main ones at the time.

---

