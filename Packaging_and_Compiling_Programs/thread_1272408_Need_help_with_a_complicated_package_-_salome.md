---
title: "Need help with a complicated package - salome"
date: 2009-09-22
forum: Packaging and Compiling Programs
---

### Post by aquavitae on 2009-09-22
Hi

I am attempting to package salome (from salome-platform.org) properly into a deb.  The source archive contains folders for what should probably be different packages, e.g.:
[LIST]
[*]src5.1.2.tar.gz
[List]
 [*] GUI_SRC_5.1.2
 [*] KERNEL_SRC_5.1.2
 [*] etc...
[/list]
[/LIST]

Each of these folders contains source code in a fairly standard format, using the configure - make - install procedure, except that before configure there is a build_configure script which needs to be run. To make matters worse, it seems to be impossible to build the gui (for example) before installing the kernel, since it looks for a KERNEL_ROOT_DIR environment variable in the gui build_configure script.

This is the first time I'm trying to package something in ubuntu so I'm not too familiar with the system. Does anyone have any suggestions as to how I go about it?  I've read the various ubuntu and debian packaging docs and I understand the procedure for something straight forward.

---

### Post by aquavitae on 2009-09-22
I'm made a bit of progress - the environment variable it requires can be set manually after compiling the kernel, so as long as I can control the order of compilation, it shouldn't be a problem.  I'm still not sure how to build several packages from one source though...

---

### Post by Bachstelze on 2009-09-22
[http://wiki.debian.org/PkgSplit](http://wiki.debian.org/PkgSplit)

Good luck, this ain't no walk in the park. ;)

---

### Post by aquavitae on 2009-09-25
Thanks for the reply.  I've kinda given up though - it seems I'm not the first to try this, but its devs set it up so badly that its just about impossible to package properly.  They supply an executable installer on the website which I'm fighting with at the moment (in a vm ;-)) but its not much better.  They seem to think its clever to packages all the dependancies with it, so the installed dumped python 2.4 into the installation path (I set it to /opt, but it defaults to the home), and changed the python environment variables accordingly!  Since its in a vm, I'm not to worried about it messing up my system so I left it as it was.  Now I'm trying to install code_saturne, which I think is by the same devs, and comes with a similar installer written in python 2.6, which bombs out cos its trying to use python 2.4...

Ok, maybe packaging it properly will be easier!

---

