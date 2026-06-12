---
title: "[SOLVED] A couple quick quesitons on building .debs"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by isaacj87 on 2008-06-08
Hey all,

I found this [handy little website]("http://www.quietearth.us/articles/2006/08/16/Building-deb-package-from-source") that taught me how to build debs (I hope correctly lol). But I have a couple questions as the site doesn't explain the process in full detail. 

1) First and foremost, is what the site teaching correct? I don't want to pass out any debs that could potentially hose somebody's box!

2) What if I need to add some configuration flags?

For example I want to build some Banshee 1.x debs and normally I would compile like this:

```

$ cd banshee/
$ ./configure **--prefix=/usr --disable-docs**
$ make
$ sudo make install

```

Yeah? So, I'm assuming that after I run "dh_make --createorig," I should edit the "debian/rules" file...Like this?

> 
#!/usr/bin/make -f
# -*- makefile -*-
# Sample debian/rules that uses debhelper.
# This file was originally written by Joey Hess and Craig Small.
# As a special exception, when this file is copied by dh-make into a
# dh-make output file, you may use that output file without restriction.
# This special exception was added by Craig Small in version 0.37 of dh-make.

# Uncomment this to turn on verbose mode.
#export DH_VERBOSE=1


# These are used for cross-compiling and for saving the configure script
# from having to guess our platform (since we know it already)
DEB_HOST_GNU_TYPE   ?= $(shell dpkg-architecture -qDEB_HOST_GNU_TYPE)
DEB_BUILD_GNU_TYPE  ?= $(shell dpkg-architecture -qDEB_BUILD_GNU_TYPE)


config.status: configure
	dh_testdir
	# Add here commands to configure the package.
ifneq "$(wildcard /usr/share/misc/config.sub)" ""
	cp -f /usr/share/misc/config.sub config.sub
endif
ifneq "$(wildcard /usr/share/misc/config.guess)" ""
	cp -f /usr/share/misc/config.guess config.guess
endif
	./configure --host=$(DEB_HOST_GNU_TYPE) --build=$(DEB_BUILD_GNU_TYPE) **--prefix=/usr --disable-docs** --mandir=\$${prefix}/share/man --infodir=\$${prefix}/share/info CFLAGS="$(CFLAGS)" LDFLAGS="-Wl,-z,defs"

...or is that wrong?

3) What is the proper way to edit the "debian/control" file?

> 
Source: banshee-1
Section: unknown
Priority: extra
Maintainer: Isaac J <isaac@unknown>
Build-Depends: debhelper (>= 5), autotools-dev
Standards-Version: 3.7.2

Package: banshee-1
Architecture: any
Depends: ${shlibs:Depends}, ${misc:Depends}
Description: <insert up to 60 chars description>
 <insert long description, indented with spaces>

See how this particular control file has 2 separate chunks I could edit? What should I be changing here...Obviously, the dependencies have been taken care of. I should change the maintainer and description fields correct?

Thanks in advance for the help guys :D

---

### Post by Xiong Chiamiov on 2008-06-09
Hmm, that is an interesting guide.  Personally, I start a compile like normal (with ./configure and make), but then, instead of "make install", I use "checkinstall", which you may have to install from the repos.  This is used to make a .deb in the source folder so that you can then uninstall your compiled program from apt, but I would assume that .deb is perfectly usable for others.  It also asks you for things like maintainer and such, and does it for you.

That said, I would follow [this guide]("http://ubuntuforums.org/showthread.php?t=51003").

---

### Post by InfinityCircuit on 2008-06-09
The given guide is the correct way to build a debian package.  Checkinstall is not.  For more documentation, see the link in my signature ([http://www.debian.org/doc/maint-guide](http://www.debian.org/doc/maint-guide))

That is the correct place to change compile-time options.

You can edit any part of the control file, just make sure you stay within line character limits.  You will need to change the Build-Depends line however in debian/control manually.

---

### Post by PinkFloyd102489 on 2008-06-09
Checkinstall it easiest to use.

```

cd /path/to/dir
./configure
make
sudo checkinstall

```

and done.

---

### Post by isaacj87 on 2008-06-09
> **InfinityCircuit said:**
> The given guide is the correct way to build a debian package.  Checkinstall is not.  For more documentation, see the link in my signature ([http://www.debian.org/doc/maint-guide](http://www.debian.org/doc/maint-guide))

That is the correct place to change compile-time options.

You can edit any part of the control file, just make sure you stay within line character limits.  You will need to change the Build-Depends line however in debian/control manually.

Thanks for the info. I'll have a look at the link :)

Thanks for all the responses, but I'm trying to stay away from checkinstall. Checkinstall doesn't adhere to certain debian policies or whatever. Marking thread as solved. :D

---

