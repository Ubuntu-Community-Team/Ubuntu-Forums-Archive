---
title: "Stand Alone Package Install"
date: 2006-06-12
forum: Repositories &amp; Backports
---

### Post by SoftGround on 2006-06-12
I need to add packages to a standalone installation (no network or dialup)

How can I put packages on CD or USB thumb and install from there.

All the help seems to assume you have a network connection.

Is there any easy way to find out the dependency list before I transfer the file so I don't end up doing it hundereds of times to get the extra dependencies?

 I do NOT have access to another Ubuntu machine, but I do have fast network access elsewhere.

---

### Post by zugu on 2006-06-12
[http://packages.ubuntu.com/breezy/allpackages](http://packages.ubuntu.com/breezy/allpackages) - All Breezy packages.
[http://packages.ubuntu.com/dapper/allpackages](http://packages.ubuntu.com/dapper/allpackages) - All Dapper packages.

On your networked machine, search for the package you need and download it. Every package has its dependencies listed. On the Ubuntu machine, install the package with:```
sudo dpkg -i /path/to/package.deb
```

If you get dependency errors, don't worry. Go again to one of the links listed (the one for your Ubuntu version), search and download the dependencies you need.

Usually, the dependency depth is not higher than 3, and each time you'll need less and less packages.

Currently, this is the only way to install things on my home PC. The only disadvantage I have is that it can take, let's say, 3 days to install VLC: first day I download the VLC package from my work computer, go home, try to install and see what deps I need. The second day I download the deps, go home and try to install them. Some of them might have deps themselves, so I might repeat the process the next day. It's time consuming, but I have become used to it.

Be aware that you might find a package that says "one of the packages I need is installed, but not configured". In this case you have to install both packages with one command, like this:```
sudo dpkg -i /path/to/package1.deb /path/to/package2.deb
```You can use your USB thumb; the only condition is that its filesystem has to be in a format that both machines can read and write, like FAT32 (chances are that it already is).

---

