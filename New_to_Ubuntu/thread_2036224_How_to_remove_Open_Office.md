---
title: "How to remove Open Office"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by henry cow on 2012-08-01
I am sure that this has been addressed before, but I could not figure out how to find it.

I recently upgraded from 10.04 to 12.04

It seems to be working properly, and my laptop is low on space. I need to clean house.

There are not many old Linux images laying around, but I suspect that Open Office is taking up a fair-sized chunk of disk space.

Besides going into Synaptic Package Manager and checking everything with "open-office" in the name for removal, what else should I do, or not do?

Are there any "cleanup" or "maintenance" utilities that I could run, like I do in Windows?

Thanks!

---

### Post by Linux_junkie on 2012-08-01
```
sudo apt-get purge openoffice
```

This should remove open office completely. You may have to delete the .openoffice directory (folder) on your home partition.

As you have limited resources on your computer you might be better off installing Xubuntu or Lubuntu.

Hope this helps

---

### Post by lukeiamyourfather on 2012-08-01
This command will remove packages that are no longer a dependency for other packages or that are out of date.

```
sudo aptitude autoclean
```

Also check temporary directories and caches for things like internet browsers. Also Baobab (in the repositories) can help you find large files and folders.

---

