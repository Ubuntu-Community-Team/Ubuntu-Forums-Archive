---
title: "Problem overwriting existing file, Installing a packaged program."
date: 2011-12-13
forum: Packaging and Compiling Programs
---

### Post by marrabld on 2011-12-13
I have packaged up a program I wrote in Python and have uploaded into my ppa.  Just recently I needed to add python-matplotlib-basemap dependency.  It doesn't exist for Oneric for some reason.  No problem, I figured I would just package that as well.

I can package it no problems, but when I install it, I get the following error 

```

dpkg: error processing python-matplotlib-basemap_1.0.1-0ubuntu1_amd64.deb (--install):
 trying to overwrite '/usr/share/pyshared/mpl_toolkits/__init__.py', which is also in package python-matplotlib 1.0.1-3

```

I can get around this problem using 

```

--force-overwrite

```

And everything installs fine and I have no problems (for now).  But this isn't really an acceptable solution for sharing my code using my ppa.

Can someone tell me how to avoid this problem and package it correctly.

I am fairly new to packaging, I can do the basics but I still have a fair bit to learn.

Thanks

I should add my control file

```


Source: python-matplotlib-basemap
Section: python
Priority: extra
Maintainer: Daniel Marrable <email@email.com>
Build-Depends: debhelper (>= 8.0.0), python-support, python(>=2.6), python-numpy, libgeos-3.2.2, libgeos-dev, python-dev
Standards-Version: 3.9.2
Homepage: http://matplotlib.github.com/basemap


Package: python-matplotlib-basemap
Architecture: any
Depends:${shlibs:Depends}, ${misc:Depends}, ${python:Depends}, python-dev, libgeos-3.2.2, libgeos-dev, libproj0, python2.6, python2.6-dev, python-matplotlib, python-imaging, python-numpy
Description:The matplotlib basemap toolkit is a library for plotting 2D data on maps in Python. 
 It is similar in functionality to the matlab mapping toolbox, the IDL mapping facilities, GrADS, or the Generic Mapping Tools. PyNGL and CDAT are other libraries that provide similar capabilities in Python.

```

and rules file 

```

#!/usr/bin/make -f
# -*- makefile -*-
# Sample debian/rules that uses debhelper.
# This file was originally written by Joey Hess and Craig Small.
# As a special exception, when this file is copied by dh-make into a
# dh-make output file, you may use that output file without restriction.
# This special exception was added by Craig Small in version 0.37 of dh-make.

# Uncomment this to turn on verbose mode.
#export DH_VERBOSE=1

%:
	dh $@

#override_dh_install:
#	dh_installpython setup.py install 
	

```

---

### Post by MadCow108 on 2011-12-15
why not use the basemap package from debian testing or precise, it does not overwrite matplotlibs file

if you really want to do it yourself here's how the official package solves it in debian/rules:
```

override_dh_pysupport:
        dh_pysupport
        # remove namespace file, already shipped with python-matplotlib
        rm $(CURDIR)/debian/python-mpltoolkits.basemap/usr/share/pyshared/mpl_toolkits/__init__.py
```

---

### Post by marrabld on 2012-01-04
Thanks for you help again MadCow108

The solution I was happiest with was to add this line

```
rm $(CURDIR)/debian/tmp/usr/share/pyshared/mpl_toolkits/__init__.py
```

problem solved.

And oh yes, I should have gone to the Debian repos to see how they did it.  Lesson learnt.

---

