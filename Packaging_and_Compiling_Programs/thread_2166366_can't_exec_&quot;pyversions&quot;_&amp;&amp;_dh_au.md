---
title: "can't exec &quot;pyversions&quot; &amp;&amp; dh_auto_clean: failed to run pyversions"
date: 2013-08-08
forum: Packaging and Compiling Programs
---

### Post by epikvision on 2013-08-08
Hi all, 

My name is John Kim, and I have been doing packaging work for an app  called pylang [1]. I was successful in packaging the app, in which  lintian returned no errors with every bzr builddeb. 

The challenge, however, was pbuilder.  The app does not have a make  build system, as it's coded in Python 2.7, where installation is done  with setup.py.  I've tried to install this app with the newly packaged  .deb file in the saucy and wheezy pbuilder.  They both gave similar errors.

This one is from building pylang on clean pbuilder saucy.  I bolded the errors that stood out to me.

```

john@kotux:~/packaging/build-area$ pbuilder-dist saucy build pylang_0.0.3-0ubuntu1.dsc 
W: /etc/pbuilderrc does not exist
W: /home/john/.pbuilderrc does not exist
I: Logging to /home/john/pbuilder/saucy_result/last_operation.log
I: using fakeroot in build.
...
...
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Writing extended state information...
 -> Finished parsing the build-deps
Reading package lists...
Building dependency tree...
Reading state information...
The following NEW packages will be installed:
  fakeroot
debconf: delaying package configuration, since apt-utils is not installed
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/99.3 kB of archives.
After this operation, 355 kB of additional disk space will be used.
Selecting previously unselected package fakeroot.
(Reading database ... 14715 files and directories currently installed.)
Unpacking fakeroot (from .../fakeroot_1.19-2_amd64.deb) ...
Processing triggers for man-db ...
Setting up fakeroot (1.19-2) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode
I: Copying back the cached apt archive contents
I: Copying source file
I: copying [pylang_0.0.3-0ubuntu1.dsc]
I: copying [./pylang_0.0.3.orig.tar.gz]
I: copying [./pylang_0.0.3-0ubuntu1.diff.gz]
I: Extracting source
gpgv: Signature made Fri Aug  9 00:15:31 2013 UTC using RSA key ID 41320B4B
**gpgv: Can't check signature: public key not found**
**dpkg-source: warning: failed to verify signature on ./pylang_0.0.3-0ubuntu1.dsc**
dpkg-source: info: extracting pylang in pylang-0.0.3
dpkg-source: info: unpacking pylang_0.0.3.orig.tar.gz
dpkg-source: info: applying pylang_0.0.3-0ubuntu1.diff.gz
I: Building the package
I: Running cd tmp/buildd/*/ && env PATH="/usr/sbin:/usr/bin:/sbin:/bin" dpkg-buildpackage -us -uc  -rfakeroot
dpkg-buildpackage: source package pylang
dpkg-buildpackage: source version 0.0.3-0ubuntu1
dpkg-buildpackage: source changed by John Kim <johnkim.ubuntu@gmail.com>
 dpkg-source --before-build pylang-0.0.3
dpkg-buildpackage: host architecture amd64
 fakeroot debian/rules clean
dh clean 
   dh_testdir
   dh_auto_clean
**Can't exec "pyversions": No such file or directory at  /usr/share/perl5/Debian/Debhelper/Buildsystem/python_distutils.pm line  120.**
dh_auto_clean: failed to run pyversions
make: *** [clean] Error 2
**dpkg-buildpackage: error: fakeroot debian/rules clean gave error exit status 2**
E: Failed autobuilding of package
I: unmounting dev/pts filesystem
I: unmounting proc filesystem
I: cleaning the build env 
I: removing directory /var/cache/pbuilder/build//13908 and its subdirectories


```

So, a few things:
[LIST]
[*]gpg didn't run in the clean system because dpkg-source couldn't find it. 
[*]can't exec pyversions; according to the reports from other  people (there are not many), this occurs because dpkg-auto-* expects to find a make system. 
[/LIST]

I think to fix this issue, I will need to edit my debian/rules file - or  maybe not.  The problem is I don't know how to accomplish this.  I  would appreciate any help. Thanks.

[1] [https://launchpad.net/pylang](https://launchpad.net/pylang)

---

### Post by amoog on 2013-08-09
You are missing packages needed to build the software. In your debian/control, check the line "Build-Depends", most likely you will to have "python-dev" there.

---

### Post by epikvision on 2013-08-09
Hi amoog,

Should I add simply 'python-dev', or something like "python-all-dev (>= 2.3.5-11)" as provided by the Debian Wiki [1]?

[1] [https://wiki.debian.org/Python/Policy](https://wiki.debian.org/Python/Policy)

---

### Post by epikvision on 2013-08-09
Hi, I opted for python-dev, and now this popped up at the building stage.

```

I: Building the package
I: Running cd tmp/buildd/*/ && env PATH="/usr/sbin:/usr/bin:/sbin:/bin" dpkg-buildpackage -us -uc  -rfakeroot
dpkg-buildpackage: source package pylang
dpkg-buildpackage: source version 0.0.3-0ubuntu1
dpkg-buildpackage: source changed by John Kim <johnkim.ubuntu@gmail.com>
 dpkg-source --before-build pylang-0.0.3
dpkg-buildpackage: host architecture amd64
 fakeroot debian/rules clean
dh clean 
   dh_testdir
   dh_auto_clean
Traceback (most recent call last):
  File "setup.py", line 20, in <module>
    from DistUtilsExtra.auto import setup
ImportError: No module named DistUtilsExtra.auto
dh_auto_clean: python setup.py clean -a returned exit code 1
make: *** [clean] Error 1
dpkg-buildpackage: error: fakeroot debian/rules clean gave error exit status 2
E: Failed autobuilding of package
I: unmounting dev/pts filesystem
I: unmounting proc filesystem
I: cleaning the build env 
I: removing directory /var/cache/pbuilder/build//27261 and its subdirectories


```

Do I need to specify the module DistUtilsAuto as a build-depends as well? 

If so, I will need to consult with the developer.  He says since it is quite big, the app shoud work without this dependency.  I don't know if that's possible for pbuilder.

---

### Post by epikvision on 2013-08-09
Is there a way I can integrate this py script [1], maybe some other solution to avoid adding DistAutoUtils as a dependency? I don't want the application to balloon in size just because it needs DistAutoUtils. 

[1] [https://code.launchpad.net/~mterry/python-distutils-extra/skip-setup.py](https://code.launchpad.net/~mterry/python-distutils-extra/skip-setup.py)

---

### Post by amoog on 2013-08-09
Yes. you need to include everything that is needed to build. If the setup.py script uses distutils, you need to add that to the Build depends.

---

### Post by epikvision on 2013-08-09
Hey amoog,Good news!  When I specified python-distutils-extra as a build-depends, the build was successful on both saucy and wheezy  :-)! 

My  concern is whether this would make python-distutils-extra a dependency  on the .deb file as well. The building from source process definitely required this dependency, but would the resulting .deb file need it too.  How can I make sure it doesn't?

To put it in a better way: many other programs, like this one, needs it, but the distutils stuff isn't already preinstalled.  Distutils install has to be a one time thing.

---

### Post by amoog on 2013-08-09
If you have a Python:Depends in the binary package Depends stanza in debian/control and use debhelper, the needed depends will be automatically resolved. Usually, you only need distutils to *build*, not to run the package.

---

### Post by epikvision on 2013-08-09
> **amoog said:**
> If you have a Python:Depends in the binary package Depends stanza in debian/control and use debhelper, the needed depends will be automatically resolved. Usually, you only need distutils to *build*, not to run the package.

Awesome, thanks for the info.  

Another way to put it, from what I now understand, the Build-Depends and Depends fields of the debian/control file serve different functions, the former for during buildtime, the latter when the binary is executed.  

Marking as solved.

---

