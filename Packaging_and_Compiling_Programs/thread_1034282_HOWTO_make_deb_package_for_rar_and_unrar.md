---
title: "HOWTO make deb package for rar and unrar"
date: 2009-01-08
forum: Packaging and Compiling Programs
---

### Post by SuperBo on 2009-01-08
I want to make deb package for rar and unrar.
But there is no make file, so I can't use checkinstall.
How can i build deb packages with these program.

---

### Post by KIAaze on 2009-01-09
There are already packages for rar and unrar:
[http://packages.ubuntu.com/intrepid/rar](http://packages.ubuntu.com/intrepid/rar)
[http://packages.ubuntu.com/intrepid/unrar](http://packages.ubuntu.com/intrepid/unrar)

Why do you want to make another one?

Also, rar and unrar do have a Makefile!!!
Just run:
```
apt-get source rar
apt-get source unrar

```

Unrar has source code, but rar doesn't.
The Makefile for rar is very simple. It only contains an install target, which seems to be enough to package it by using the instructions from:
[https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)

Anyway, here's a quick and dirty way if there's no Makefile:

Let's say we want to package foo-1.0 which installs "bar" to "/usr/bin/bar".

```
mkdir -p foo-1.0/DEBIAN
mkdir -p foo-1.0/usr/bin
touch foo-1.0/usr/bin/bar

```

Create a file named "DEBIAN/control" in foo-1.0:

DEBIAN/control:
```
Source: foo
Section: unknown
Priority: extra
Maintainer: John Doe <you@yourmail.com>
Version: 1.0
Homepage: <insert the upstream URL, if relevant>
Package: foo
Architecture: i386
Description: <insert up to 60 chars description>
 <insert long description, indented with spaces>

```

Then to create the package:
```
dpkg-deb -b ./foo-1.0/ ./foo-1.0.deb
```

That's all. :)
The package works and will install "bar" in /usr/bin.

However, it's not the correct way to create a debian package! [-X

Here's how to create a correct debian package:
[https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)

---

