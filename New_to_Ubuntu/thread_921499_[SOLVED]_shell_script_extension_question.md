---
title: "[SOLVED] shell script extension question"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by lovinglinux on 2008-09-16
I'm wondering if there is any difference between creating a shell script file with or without the "*.sh" extension?

I have seen tutorials that use the "*.sh" extension and others that do not use it.

---

### Post by Mornedhel on 2008-09-16
There isn't any. Adding .sh just gives a visual hint of what kind of text file it is. This is true for all types of text files, although some applications rely on the extension.

---

### Post by iaculallad on 2008-09-16
Only difference for aside from the way they are named, either filename and filename.sh are their permission attribute:

For a normal file named filename.sh

> -rw-r--r--

and for a file named filename.sh having with executable bit turned on (chmod +x filename.sh):

> -rwxr-xr-x

---

### Post by lovinglinux on 2008-09-16
> **iaculallad said:**
> Only difference for aside from the way they are named, either filename and filename.sh are their permission attribute:

For a normal file named filename.sh



and for a file named filename.sh having with executable bit turned on (chmod +x filename.sh):

These would be achieved by changing the permissions in the file properties if I don't want to use the CLI right? Either way, when I create the file, the permission will be the same using sh or not right?

---

### Post by szymon_g on 2008-09-16
> **lovinglinux said:**
> These would be achieved by changing the permissions in the file properties if I don't want to use the CLI right? Either way, when I create the file, the permission will be the same using sh or not right?

que?
you can change file permission from GUI as well (at least from KDE), you dont have to use CLI.
when you create files (with and without .sh extension), they will have the same permissions (if they are created in the same directory, by the same user and by the same method)

---

### Post by lovinglinux on 2008-09-16
> **szymon_g said:**
> que?
you can change file permission from GUI as well (at least from KDE), you dont have to use CLI.
when you create files (with and without .sh extension), they will have the same permissions (if they are created in the same directory, by the same user and by the same method)

Thank you.

---

### Post by szymon_g on 2008-09-16
your welcome :>

---

