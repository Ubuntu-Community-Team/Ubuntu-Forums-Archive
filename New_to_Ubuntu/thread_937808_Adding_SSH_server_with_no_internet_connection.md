---
title: "Adding SSH server with no internet connection"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by Konstabel on 2008-10-04
Where can I download a SSH server to install with a flash disk?

---

### Post by Dougie187 on 2008-10-04
Why do you want ssh if you don't have an internet connection?

---

### Post by gimlithedwarf on 2008-10-04
[http://packages.ubuntu.com/](http://packages.ubuntu.com/) -> pick your distro and arch and you're away

---

### Post by gimlithedwarf on 2008-10-04
> **Dougie187 said:**
> Why do you want ssh if you don't have an internet connection?

He could be using it within a network that doesn't have internet access

---

### Post by Konstabel on 2008-10-04
Thanks glim

---

### Post by Konstabel on 2008-10-04
I got the ssh package, from a XP machine (FAT32 flash disk). How can I mount this disk in Ubuntu to be able to install the package?
I get a "Invalid mount option when attempting to mount the volume" message.

---

### Post by Gannon8 on 2008-10-04
Try:
```
sudo mount -t msdos /dev/whatever /mnt/somewhere
```

---

