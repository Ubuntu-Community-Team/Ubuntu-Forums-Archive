---
title: "Download packages required to build specific package"
date: 2009-04-17
forum: Packaging and Compiling Programs
---

### Post by koma77 on 2009-04-17
Hi!

I would like to know if there is a way to download source-packages with dependencies.

For example:
Say that I would like to build Transmission from source.

How can I download the source-package for Transmission and all its dependencies?

Is there a way to do this with apt-get?

Thanks.

---

### Post by johnl on 2009-04-17
Try:

```

sudo apt-get build-dep <package-name>

```

This will retrieve the build dependencies for the package you specify.

You can then perform

```

apt-get source <package-name>

```

To get the source code of the specified package. (Note that I didn't use sudo -- if you use sudo, root will own the source files you download).

Hope this helps.

---

