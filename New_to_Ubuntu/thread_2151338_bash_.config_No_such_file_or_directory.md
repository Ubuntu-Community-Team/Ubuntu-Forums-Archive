---
title: "bash: ./config: No such file or directory"
date: 2013-06-04
forum: New to Ubuntu
---

### Post by kautKas on 2013-06-04
Hi everyone,

Just installed Ubuntu 13.04 yesterday, so I'm a total noob.
I tried to install Java from a tar.gz file by following this tutorial:[http://www.makeuseof.com/tag/compile-install-tar-gz-tar-bz2-files-ubuntu-linux/](http://www.makeuseof.com/tag/compile-install-tar-gz-tar-bz2-files-ubuntu-linux/)
Everything went fine till the step where I had to type ./config
bash: ./config: No such file or directory
I followed all the tutorial steps.
How can I fix that?

---

### Post by slickymaster on 2013-06-04
> **kautKas said:**
> Hi everyone,

Just installed Ubuntu 13.04 yesterday, so I'm a total noob.
I tried to install Java from a tar.gz file ...

Since you are not experienced in Ubuntu/Linux and since you want to install Java on your system, my advise to you is to do it the easy way, which is adding a PPA repository to install and keep your computer up to date with the latest Java.
Just open a terminal window and copy/paste the following commands:```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

---

### Post by kautKas on 2013-06-04
Thanks, it worked! :)

---

### Post by slickymaster on 2013-06-04
Glad you got it working.
Please mark your thread as SOLVED so other people searching the forums know that it provides a working solution for their problem. Follow the link in my signature on how to do it.

---

