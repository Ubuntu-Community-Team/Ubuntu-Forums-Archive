---
title: "How do I obtain build dependencies that are not in repositories?"
date: 2010-07-27
forum: Repositories &amp; Backports
---

### Post by s3a on 2010-07-27
I would like to know if there is a way to figure out what the dependencies of a particular package are (so that I can obtain them and proceed to building the package --- the documentation on the internet is rather complex for me to understand since I don't learn things easily but once I do they pretty much never escape me):
[INDENT]-without requiring that the source is in a repository of any kind.[/INDENT]
[INDENT]-without requiring me to compile/install the program without a package manager (I want to compile to a binary .deb file and then install via that)[/INDENT]

There must be a way of doing this since the Ubuntu/Debian developers have to get their source from some upstream source before "debianizing" it.

If someone knows the answer to my problem, please respond, I would be VERY grateful!
Thanks in advance!

---

### Post by RainCT on 2010-08-22
That depends on the application. Some upstream tarballs include a file with a dependency list, or have one on a website or wiki. For others you'll have to try and figure them out yourself, trying to build the application, or checking the source code or build scripts.

In particular, if you have this problem with a project using autotools, you can run "./configure" and it'll print an error if you are missing any dependency, saying which dependency it is.

If you are building a Debian package, you can check if you got the dependencies right by trying to build it inside a chroot. See [http://bloc.eurion.net/archives/2009/test-build-debian-packages/](http://bloc.eurion.net/archives/2009/test-build-debian-packages/) for an introduction to my preferred method of doing this (it's one of the easiest and supports working with packages for multiple distribution releases).

---

