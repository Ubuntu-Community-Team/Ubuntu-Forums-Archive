---
title: "some problem with my .deb package"
date: 2012-05-01
forum: Packaging and Compiling Programs
---

### Post by avisoft on 2012-05-01
hi
i created .deb package by this guide, 
[https://wiki.ubuntu.com/PackagingGuide/QtApplication](https://wiki.ubuntu.com/PackagingGuide/QtApplication)
for my QT application, i was build it locally by this command
```
debuild -uc -us
```
and everything goes perfect except some minor 'w' on 'lintian' output.

when i open the package on the 'ubuntu software center' i can install it, but after the installation , i cant remove it on the 'software center' just reinstall it. 
(with this command 'sudo apt-get --purge remove' the program is removed)

why is that?

i'm using ubuntu 12.04 amd64.

thanks a lot!

---

