---
title: "Python package working for hardy but not for lucid"
date: 2011-10-26
forum: Packaging and Compiling Programs
---

### Post by Fusel Wusel on 2011-10-26
Hello there!

I have stumbled onto a problem whilst packing a python package for Ubuntu. The basic problem is that when I create the *.deb for Ubuntu Hardy, all goes well and the content of the package gets installed to /usr/share/pyshared. But when I create the very same package for Lucid, nothing gets installed to /usr/share/pyshared.

My package is very simple because it is only a basic package for an ongoing series of further additions to a program. It should only create the base folders in /usr/share/pyshared with an __init__.py (Some functions in it, not empty) in it.

This is, what the package looks like (names substituted):
```
tree -F foo-common-0.9
foo-common-0.9
&#9500;&#9472;&#9472; debian/
&#9474;** &#9500;&#9472;&#9472; changelog
&#9474;** &#9500;&#9472;&#9472; compat
&#9474;** &#9500;&#9472;&#9472; control
&#9474;** &#9500;&#9472;&#9472; control.in
&#9474;** &#9500;&#9472;&#9472; copyright
&#9474;** &#9500;&#9472;&#9472; pycompat
&#9474;** &#9500;&#9472;&#9472; rules*
&#9474;** &#9492;&#9472;&#9472; source/
&#9474;**     &#9492;&#9472;&#9472; format
&#9500;&#9472;&#9472; foo/
&#9474;** &#9500;&#9472;&#9472; __init__.py
&#9474;** &#9492;&#9472;&#9472; plugins/
&#9474;**     &#9492;&#9472;&#9472; __init__.py
&#9492;&#9472;&#9472; setup.py

4 directories, 11 files
```

As I am using CDBS, the debian/rules looks like this:
```
#!/usr/bin/make -f

DEB_PYTHON_SYSTEM := pycentral

include /usr/share/cdbs/1/rules/debhelper.mk
include /usr/share/cdbs/1/class/python-distutils.mk
include /usr/share/cdbs/1/rules/simple-patchsys.mk

# Don't compress .py files
DEB_COMPRESS_EXCLUDE := .py
```

The setup.py is as follows:
```
#!/usr/bin/env python

from distutils.core import setup

setup(name='foo-common',
      version='0.9',
      description='The foo common support files for development',
      author='Fusel Wusel',
      author_email='a@b.c',
      url='https://foo.net',
      packages=['foo','foo.plugins']
     )
```

The debian/control file should be alright:

```
Source: foo-common
Section: science
Priority: extra
Maintainer: my_name <my_email>
Build-Depends: cdbs (>= 0.4.49), debhelper (>= 7), python-all, python-central (>= 0.6.5)
Standards-Version: 3.8.4
XS-Python-Version: >=2.4
Homepage: https:/foo.net/

Package: foo-common
Architecture: any
Depends: ${shlibs:Depends}, ${misc:Depends}, ${python:Depends}
XB-Python-Version: ${python:Versions}
Description: The foo common support files for development
 This package installs the basic folder structure for foo
 development. It is needed by all following foo packages.
```

Lintian gives no errors or warnings besides a missing debian/watch file, which is no problem at the moment.

I create the *.deb package with pbuilder I use Jamin W. Collins script:
```
#!/bin/sh
# script from Jamin W. Collins  BTS: #255165
# name this script 'pbuilder-woody', 'pbuilder-sid', 'pbuilder-sarge', 'pbuilder-experimental' etc.

OPERATION=$1
DISTRIBUTION=`basename $0 | cut -f2 -d '-'`
PROCEED=false
BASE_DIR="$HOME/pbuilder/$DISTRIBUTION"
case $OPERATION in
   create|update|build|clean|login|execute )
      PROCEED=true
      ;;
esac
if ( $PROCEED == true ) then
   shift 
   sudo pbuilder $OPERATION \
      --basetgz $BASE_DIR/$DISTRIBUTION-base.tgz \
      --distribution $DISTRIBUTION \
      --othermirror "deb http://archive.ubuntu.com/ubuntu $DISTRIBUTION main universe multiverse restricted" \
      --buildresult $BASE_DIR/result "$@"
else
   echo "Invalid command..."
   echo "Valid commands are:"
   echo "   create"
   echo "   update"
   echo "   build"
   echo "   clean"
   echo "   login"
   echo "   execute"
   exit 1
fi
```

With either pbuilder-hardy or pbuilder-lucid with only changing the distribution-name within debian/changelog. (Of course I have got two working directories for this. Not changing it every time)

I hope you could follow my problem and could give me a hint on this. If any information is missing, I'll add it asap.

[EDIT] Solved this with kicking out CDBS and using the new debhelper 7 features for my lucid build with a new minimalistic debian/rules file.

---

