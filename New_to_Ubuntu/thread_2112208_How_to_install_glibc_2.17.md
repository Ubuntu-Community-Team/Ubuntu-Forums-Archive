---
title: "How to install glibc 2.17"
date: 2013-02-04
forum: New to Ubuntu
---

### Post by bonedriven on 2013-02-04
I find it and download the glibc-2.17.tar

Now when I extrat it there are many folders and files, but there is no file that's executable.

Thanks

---

### Post by schragge on 2013-02-04
There already is [glibc 2.17 package](https://launchpad.net/ubuntu/+source/eglibc) for raring (coming Ubuntu release) . What Ubuntu version are you trying to install it on? Is backporting the existing package an option?

---

### Post by bonedriven on 2013-02-04
Mine is Ubuntu 12.04 LTS.
I'm trying to install a computational software "Materials Studio 6" for Ubuntu. Here's what's required. 

[[IMG]http://img69.imageshack.us/img69/2610/capturebei.jpg[/IMG]](http://imageshack.us/photo/my-images/69/capturebei.jpg/)

Uploaded with [ImageShack.us](http://imageshack.us)

So you mean it's already included in the OS?

---

### Post by omeomi on 2013-02-04
Ubuntu 12.04 comes with glibc-2.15 so that should be fine. Does it give you any errors about dependencies when you try to install this software?

---

### Post by schragge on 2013-02-04
Yes. The package is called 'libc6' on Debian-based systems.

---

### Post by bonedriven on 2013-02-04
Thank you very much. I haven't tried to install it yet as I read it also needs to install HP-MPI, which I am also not sure how to do it yet. Thanks again.

---

