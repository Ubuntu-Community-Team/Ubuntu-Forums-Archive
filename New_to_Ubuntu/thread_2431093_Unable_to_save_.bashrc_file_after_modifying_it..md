---
title: "Unable to save .bashrc file after modifying it."
date: 2019-11-11
forum: New to Ubuntu
---

### Post by eigensystems on 2019-11-11
I edited .bashrc file to add some aliases but it's not allowing me to save it even after changing the file access permissions to 666. Any hints?

---

### Post by TheFu on 2019-11-11
Please show the full permissions for the file and the parent directory.[B]
ls -al[/B] is the normal way to do that.

---

### Post by Impavidus on 2019-11-12
Normally permissions of .bashrc should be 644 or 640 or 600 and the owner should be you.

Furthermore, make sure the filesystem is mounted in read-write mode. If mounted read-only, you cannot save anything (or change any permissions, or delete anything). The filesystem may get mounted read-only after an input/output error. It may be OK after a reboot, but may also be a sign of more trouble.
```
findmnt /
# Or, if you have a /home partition
findmnt /home
```

---

