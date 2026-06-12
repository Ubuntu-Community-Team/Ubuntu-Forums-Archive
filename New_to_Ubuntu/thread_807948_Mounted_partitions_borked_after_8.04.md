---
title: "Mounted partitions borked after 8.04"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by rsd-17 on 2008-05-26
I upgraded from 7.10 to 8.04. Everything seems fine except my two
network storage devices can no longer be mounted.

[COLOR="Blue"]$ sudo mount -a
sudo unable to resolve host *hostname*
mount error 20 = Not a directory
Refer to the mount.cifs(8) manual page...[/COLOR]

The message about resolving hostname is new.
So is the mount error. I haven't knowingly made any other system changes.

Does anyone have any ideas?

...jr

---

### Post by sisco311 on 2008-05-26
Read this to resolve the sudo error:
[http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

---

### Post by rsd-17 on 2008-05-26
> **sisco311 said:**
> Read this to resolve the sudo error:
[http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

Thanks. That fixed the "unable to resolve hostname."

I still haven't found an answer to the cifs problem.

---

