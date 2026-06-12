---
title: "unable to mount .iso/.img"
date: 2013-02-01
forum: New to Ubuntu
---

### Post by Rfdp on 2013-02-01
I'm having problems mounting .iso or .img files.

I've tried Furius ISO Mount, Gmount-iso, Acetone ISO and manual mount in the terminal.



Furius just shows it as mounted, but it doesn't appear anywhere else;

Gmount only mounts iso files and doesn't unmount afterwards;

Acetone sends an error message as soon as I try to mount any file.

and the terminal solution works neither ("directory doesn't exist"), I'm probably too stupid to execute the commands



If anyone had any suggestion on how I could at least mount .img files or why Furius and Acetone don't work at all I would appreciate it very much.

---

### Post by Mark Phelps on 2013-02-01
In the past, I've found the following to work:

```
# mkdir -p /mnt/disk
# mount -o loop disk.img /mnt/disk
# cd /mnt/disk
# ls -l
```

---

