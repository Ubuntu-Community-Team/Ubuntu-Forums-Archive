---
title: "Ubuntu version to read a UFS FS"
date: 2017-06-29
forum: New to Ubuntu
---

### Post by ddrecovery on 2017-06-29
What version of Ubuntu is good to mount a UFS file system. I currently have v16 something and I don't think it supports UFS.

---

### Post by TheFu on 2017-06-29
Welcome to the forums.

Any of them should work. 
Google found this answer:  [https://askubuntu.com/questions/85154/mount-ufs-filesystem](https://askubuntu.com/questions/85154/mount-ufs-filesystem) . I doubt the specific release matters.

I didn't have to install any packages to load the ufs kernel module. I don't have any UFS disks easily available to try and mount it - my only freeBSD system with it is in production can I'm unwilling to mess with it.

The general solution for almost any need is 
a) install the package (if necessary), 
b) load the kernel module (if necessary)
c) configure the server/module/application (if necessary)
d) Run the program/load the module / mount the disk.  
There are 45,000+ packages in the repos.  Just because something isn't pre-installed, that doesn't mean it won't work or isn't "included."

When it comes to kernel modules, the more that are loaded the more RAM is used.  Very few people need access to UFS, so it isn't loaded automatically - nor should it be.

I hope you only use LTS releases of Ubuntu. Those are the most stable and have the longest support periods.  Non-LTS releases only have 6-9 months of support from their release day. For me, it isn't worth my time to load anything important into an OS with less than 2-3 yrs of known, planned, support.  Of course, everyone is different, so that might not be important to you.  However, if you are running 16.10, support for it ends shortly - like less than a month.

---

### Post by ddrecovery on 2017-06-30
Many thanks for the reply.

---

