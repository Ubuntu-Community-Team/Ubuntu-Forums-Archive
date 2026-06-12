---
title: "files in a directory are still showing after deletion"
date: 2012-04-06
forum: New to Ubuntu
---

### Post by goingforcoffee on 2012-04-06
Hey guys,

After deleting some files from a directory using the GUI (and then from the recycle bin) they are still showing up when I view the dir from the terminal:

```

cd directory
ls
xxxx.py~

```

Not sure exactly what that means? or why they are still showing up after being removed

Thanks

---

### Post by sudodus on 2012-04-06
> **goingforcoffee said:**
> Hey guys,

After deleting some files from a directory using the GUI (and then from the recycle bin) they are still showing up when I view the dir from the terminal:

```

cd directory
ls
xxxx.py~

```

Not sure exactly what that means? or why they are still showing up after being removed

Thanks
The files ending with ~ are backed up in an old way by some programs. For example: when you edit a file, the old version is saved with a new name = the old name + ~.

And these files remain if you delete the original files (in your example xxxx.py). You can simply look for and delete the ~ files once in a while, or switch the ~ backup mode off in the program that creates those files.

---

