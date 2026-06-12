---
title: "How do I obtain build dependencies that are not in repositories?"
date: 2010-02-27
forum: Packaging and Compiling Programs
---

### Post by s3a on 2010-02-27
Lets say that I want to compile a program that is in the unstable repository and I have testing (or also if I am using stable and want to compile something from testing), I know that I have to put the deb-src repository line of the repository from which I want to obtain the build dependencies by ussing apt-get build-dep packagename but my question is: what if it's not in the repositories at all? How does one go about obtaining these dependencies?

I don't know much about this topic but I know how to use dh-make with dh_make --createorig and I also know how to do dpkg-buildpackage but not more than that.

Any input would be greatly appreciated!
Thanks in advance!

---

### Post by pastalavista on 2010-02-27
I believe Google could find the files you need and you could use apt-cache to save them. Also aptitude is a powerful tool. Try```
sudo aptitude --full-resolver

or

man aptitude
```

---

