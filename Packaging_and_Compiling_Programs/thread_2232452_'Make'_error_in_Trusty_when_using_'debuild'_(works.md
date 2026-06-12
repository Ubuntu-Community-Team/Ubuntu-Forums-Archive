---
title: "'Make' error in Trusty when using 'debuild' (works in previous Ubuntu versions)"
date: 2014-07-02
forum: Packaging and Compiling Programs
---

### Post by inameiname on 2014-07-02
Ever since I did a fresh install of Ubuntu Trusty, I have been unable to build a package for use in my Launchpad PPA. The issue is not in uploading a package, but before that, when running 'debuild -b' to get it made. 

Based on the error output, the issue lies with my 'package_name.install' file that I use. The thing that I do not get is why I can do exactly what I do to make packages in previous Ubuntu versions, but not Trusty. 

Has something changed with how packages are built from Saucy to Trusty, such as changes with whatever particular packages are used in the building I do?

Anyway, the following is the error I'm getting:

```

debuild -b
 dpkg-buildpackage -rfakeroot -D -us -uc -b
dpkg-buildpackage: source package package_name
dpkg-buildpackage: source version 1.0-1ppa1~tester1
dpkg-buildpackage: source distribution trusty
dpkg-buildpackage: source changed by Me <me@me.com>
 dpkg-source --before-build package_name-1.0-1ppa1~tester1
dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
dh clean 
   dh_testdir
   dh_auto_clean
   dh_clean
 debian/rules build
dh build 
   dh_testdir
   dh_auto_configure
   dh_auto_build
   dh_auto_test
 fakeroot debian/rules binary
dh binary 
   dh_testroot
   dh_prep
   dh_auto_install
   dh_install
/home/me/Temp/test/package_name-1.0-1ppa1~tester1/debian/package_name.install:3: *** missing separator.  Stop.
dh_install: problem reading debian/package_name.install: 
make: *** [binary] Error 2
dpkg-buildpackage: error: fakeroot debian/rules binary gave error exit status 2
debuild: fatal error at line 1364:
dpkg-buildpackage -rfakeroot -D -us -uc -b failed

```

To note, the following is my extremely basic 'package_name.install' script that always worked before:

```

#!/usr/bin/make -f
# add more lines like below when necessary
usr/ /

```

Finally, despite never having to do this in past Ubuntu versions, I tried building my package with the 'package_name.install' file containing a <tab> before my one line, (a suggestion I found via Google), but that just gives me another error:

```

#!/usr/bin/make -f
# add more lines like below when necessary
    usr/ /

```

```

debuild -b
 dpkg-buildpackage -rfakeroot -D -us -uc -b
dpkg-buildpackage: source package package_name
dpkg-buildpackage: source version 1.0-1ppa1~tester1
dpkg-buildpackage: source distribution trusty
dpkg-buildpackage: source changed by Me <me@me.com>
 dpkg-source --before-build package_name-1.0-1ppa1~tester1
dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
dh clean 
   dh_testdir
   dh_auto_clean
   dh_clean
 debian/rules build
dh build 
   dh_testdir
   dh_auto_configure
   dh_auto_build
   dh_auto_test
 fakeroot debian/rules binary
dh binary 
   dh_testroot
   dh_prep
   dh_auto_install
   dh_install

/home/me/Temp/test/package_name-1.0-1ppa1~tester1/debian/package_name.install:3: *** commands commence before first target.  Stop.
dh_install: problem reading debian/package_name.install: 
make: *** [binary] Error 2
dpkg-buildpackage: error: fakeroot debian/rules binary gave error exit status 2
debuild: fatal error at line 1364:
dpkg-buildpackage -rfakeroot -D -us -uc -b failed

```

Anyway, if anyone knows a solution for this I would be most grateful. I am thinking of figuring out how to downgrade the version of the packages I used in Saucy so as to make this work.

---

### Post by inameiname on 2014-07-03
I think I have found the culprit to this problem. It relates to dh-make. I believe version 0.63 (and 1.20140617 for Utopic) has something in it that changed which causes the error. I have uninstalled this package and installed version 0.62 of it, and it works. Will test further.

---

