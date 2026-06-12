---
title: "How to make a &quot;Basic&quot; .deb"
date: 2008-09-04
forum: Programming Talk
---

### Post by curvedinfinity on 2008-09-04
[COLOR="Red"][B]Note by slavik: discuss this how to here: 
[http://ubuntuforums.org/showthread.php?t=1005178](http://ubuntuforums.org/showthread.php?t=1005178)
[/B][/COLOR]
Hey,
I recently had to figure out how to make a stand-alone debian package (not intended for a repository or build system), and it took quite some patience to wade through all of the complex ways of making debs for more complex distribution channels than a simple web download.

**This tutorial shows the most basic way of packaging a simple already-compiled program.**

[LIST=1]
[*]Decide on the name of your package. Standard debian notation is all lowercase in the following format:
```
<project>_<major version>.<minor version>-<package revision>
```
For example, you could name your first package...
```
helloworld_1.0-1
```
[*]Create a directory to make your package in. The name should be the same as the package name.
```
mkdir helloworld_1.0-1
```
[*]Pretend that the packaging directory is actually the root of the file system. Put the files of your program where they would be installed to on a system.
```
mkdir helloworld_1.0-1/usr
mkdir helloworld_1.0-1/usr/local
mkdir helloworld_1.0-1/usr/local/bin
cp "~/Projects/Hello World/helloworld" helloworld_1.0-1/usr/local/bin
```
[*]Now create a special metadata file with which the package manager will install your program...
```
mkdir helloworld_1.0-1/DEBIAN
gedit helloworld_1.0-1/DEBIAN/control
```
Put something like this in that file...
```
Package: helloworld
Version: 1.0-1
Section: base
Priority: optional
Architecture: i386
Depends: libsomethingorrather (>= 1.2.13), anotherDependency (>= 1.2.6)
Maintainer: Your Name <you@email.com>
Description: Hello World
 When you need some sunshine, just run this
 small program!
 
 (the space before each line in the description is important)
```
[*]Now you just need to make the package:
```
dpkg-deb --build helloworld_1.0-1
```
[/LIST]

And you're done! :)

That wasn't so hard, was it?

Just so you know, there are a lot more fields in the metadata file, and even extra whole configuration files which you can have dpkg work with, which I left out -- this is the bare bones of what's required.

Thanks to bobbocanfly for the following: If you happen to be looking for how to let the Ubuntu repositories include your project, you need to follow this guide: [https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete). Then get in touch with the MOTU team  at #ubuntu-motu on irc.freenode.net and [email]ubuntu-motu@lists.ubuntu.com[/email].

---

