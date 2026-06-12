---
title: "[SOLVED] Problems With Synaptic Package Manager"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by getitright on 2008-10-29
I have somehow messed up my access to SPM. When trying to access SPM I get the following error message: 

<E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.>

And typing 'dpkg --configure -a' into the terminal gives:

<dpkg: requested operation requires superuser privilege
>

Can anyone advise me on this problem please?

---

### Post by Duck2006 on 2008-10-29
Try

sudo dpkg --configure -a

---

### Post by getitright on 2008-10-29
That appears to have rsolved my problem.

---

### Post by jras20 on 2008-11-03
That fixed my problem also.  I had the same problem.
Thanks

---

