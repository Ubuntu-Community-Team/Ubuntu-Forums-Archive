---
title: "building deb package - Questions about dpkg -b"
date: 2011-02-03
forum: Packaging and Compiling Programs
---

### Post by pedrotuga on 2011-02-03
So I have my small python application source with all the files under a folder. I created a DEBIAN folder inside that folder, and a control file inside it.
I ran dpkg -b and a package was created.

This was easy but I got quite confused with all the documentation out there.

So where are my questions:

1. Aren't the files supposed to go under a directory structure that mimics my file system? After I created my deb package, all the .py files were in the root folder, where will they end up if the package is installed?

2. Do I really need an uninstall script? Don't all the installed files get removed when te package is removed?

3. I red that there should be some text file with all the files and their checksums, my package doesn't contain any such thing, is it optional?

---

### Post by MadCow108 on 2011-02-03
dpkg is the lowest level tool to create packages. --build just takes a directory and packs it into a deb as is. You have to place the files in the intended file system structure for it to install properly

This is ok for small packages for personal use but not so much for more complex packages intended for distribution.

a high level tools to create packages is debuild which does almost everything:
building the binaries, installing them (+ changlog documentation etc) in a temporary folder which mimics the real filesystem, builds the packages from that folder, sign the package and create the dsc and changes file (+ a bunch of other stuff I don't recall now).

to create a template package suitable for debuild have a look at dh_make from the devscripts package and:
[http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)
[https://wiki.ubuntu.com/PackagingGuide](https://wiki.ubuntu.com/PackagingGuide)
[http://www.debian.org/doc/debian-policy/#contents](http://www.debian.org/doc/debian-policy/#contents)
[http://www.debian.org/doc/packaging-manuals/python-policy/ch-python.html](http://www.debian.org/doc/packaging-manuals/python-policy/ch-python.html)
[http://www.debian.org/doc/developers-reference/index.html](http://www.debian.org/doc/developers-reference/index.html)
for details

2) if it is a simple package which does not install or change any other stuff besides the files in the .deb you don't need an uninstall script (= post-rm file)

3) the low level tools dpkg-genchanges and dpkg-source create these. Using debuild this is done automatically.

---

