---
title: "DocuCanvas"
date: 2013-04-17
forum: Packaging and Compiling Programs
---

### Post by Bresser on 2013-04-17
Hello,
So I found a program written in Python. I cloned the Repository. So now how to I compile it into a package?

Thanks

p.s. the package is DocuCanvas from github.com

---

### Post by schragge on 2013-04-20
Is it your first attempt at packaging a piece of software for Ubuntu? Then I'd suggest looking at something else. If that needs to be a python application then at least choose something that uses [Distutils]("http://docs.python.org/2/distutils/introduction.html") (it usually will have file *setup.py* in the root directory).

Anyway, for how to package DocuCanvas see [http://wiki.debian.org/DjangoPackagingDraft](http://wiki.debian.org/DjangoPackagingDraft), [Packaging Django Projects for Debian Using Autotools](http://www.radix50.net/~ibr/notes/20080323-0-django-autotools-debian.html), and [Create a Debian package for your Django application](http://www.laurentluce.com/posts/hello-world/)

---

