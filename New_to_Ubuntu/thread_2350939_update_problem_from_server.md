---
title: "update problem from server"
date: 2017-01-29
forum: New to Ubuntu
---

### Post by deeplokhande6 on 2017-01-29
I wanted to upgrade from 16.04 to 16.10 ubuntu. but whenever i try to upgrade this error is displayed, I tried changing servers still it didn,t work.
Even when i want to update an app or anything i get the same error.
Please help i am a noob, and actually require an updated ubuntu working fine to work on my CUDA project.

```
W:The repository 'cdrom://Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719) xenial Release' does not have a Release file., W:Data from such a repository can't be authenticated and is therefore potentially dangerous to use., W:See apt-secure(8) manpage for repository creation and user configuration details., W:Invalid 'Date' entry in Release file /var/lib/apt/lists/developer.download.nvidia.com_compute_cuda_repos_ubuntu1604_x86%%5f64_Release, E:Failed to fetch cdrom://Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)/dists/xenial/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs, E:Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by wildmanne39 on 2017-01-29
You have to open the "Software Sources", which you will find using the Unity dash if you are using unity.

To remove the CD sources you have to uncheck all sources in "Installable from CD-ROM/DVD".

after this is done just update the sources again and try to install the application again.

I do not use unity myself so when you get into software it may look a little different then my directions say so you will have to look for cdrom and uncheck it and that may resolve your issue,

---

