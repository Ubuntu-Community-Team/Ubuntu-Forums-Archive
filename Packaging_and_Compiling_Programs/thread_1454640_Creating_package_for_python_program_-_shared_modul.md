---
title: "Creating package for python program - shared module"
date: 2010-04-14
forum: Packaging and Compiling Programs
---

### Post by jpietari on 2010-04-14
Hi,

I am trying to create a deb package of a simple python program using dpkg-buildpackage.  In my control file, I am trying to put my python modules in a shared location which is /usr/lib/python2.6/dist-packages/~package/.  Apparently, this is done by adding python-central to the control file.

When I build my package, I get a warning "dpkg-gencontrol: warning: unused substitution variable ${python:Depends}".  I believe this is messing my package build up.  The line it is referring to is "XB-Python-Version: ${python:Versions}" in the attached document.

Any help would be greatly appreciated.

---

### Post by SevenMachines on 2010-04-16
i dont think that the warning you're getting should cause a build failure. Can you post more info? If you can post the full packaging or even a ppa link that would be great

---

### Post by jpietari on 2010-04-17
You are completely right.  I was able to create the package eventhough I got a warning.

My problem was that my files were being put into the pyshared directory but I did not reference the proper directory in my import statements (i.e. /usr/share/pyshared/~package/ vs /usr/share/pyshared/).  It was a dumb error by me.  

I was able to create my first debian package!  Yay!

Thanks for your help.

I will be posting the package and source code on [https://launchpad.net/squash-tracker](https://launchpad.net/squash-tracker) tomorrow.  I had to make a number of changes to the project so that it would work in my development environment and when I create a package.  The joys of being new to this.

---

