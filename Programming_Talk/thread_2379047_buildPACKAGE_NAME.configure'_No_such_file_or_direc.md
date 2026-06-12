---
title: "/build/PACKAGE_NAME/./configure': No such file or directory when doing pdebuild"
date: 2017-11-30
forum: Programming Talk
---

### Post by ishannbhatt on 2017-11-30
I am using Ubuntu 16.04 xenial to build deb files using pbuilder.


I have the following folder structure in place,


debian  modules  products  result  tests
I am trying to build a deb file using pdebuilder. I followed this to get rid off


Package cowdancer is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source


Then I ran cowbuilder --create This command seemed successful. with no error and following output.


I: new cache content 'perl-modules-5.22_5.22.1-9_all.deb' added
I: new cache content 'libmount1_2.27.1-6ubuntu3.3_amd64.deb' added
I: unmounting dev/pts filesystem
I: unmounting run/shm filesystem
I: unmounting proc filesystem
With no E. The I ran my pdebuild command


pdebuild --architecture i386 --buildresult /home/ishanbhatt/PACKAGE_NAME/result --pbuilder cowbuilder --auto-debsign --pbuildersatisfydepends /usr/lib/pbuilder/pbuilder-satisfydepends --debbuildopts '-si -ebuild\@abc.def'
It was running smoothly till I hit with the road block.


touch debian/stamp-autotools-files
chmod a+x /build/PACKAGE_NAME/./configure
chmod: cannot access '/build/PACKAGE_NAME/./configure': No such file or directory
/usr/share/cdbs/1/class/autotools.mk:42: recipe for target 'debian/stamp-autotools' failed
make: *** [debian/stamp-autotools] Error 1
dpkg-buildpackage: error: debian/rules build gave error exit status 2
How do I get around this one??

---

### Post by Yellow Pasque on 2017-11-30
> PACKAGE_NAME

You are supposed to substitute the actual name of the package here instead of literally using it in the command.

---

### Post by ishannbhatt on 2017-12-01
Hi, the package name is already been substituted, I have not written it here as per company policy..

---

### Post by deadflowr on 2017-12-01
Is /build the right directory?
And the path implies that you have a directory called . as in dot as in /build/THING/./configure

Would the path make more sense if was something like
```
build/PACKAGE_NAME/configure
```
depending on where the build directory is, whether in somewhere like /home or /tmp or somewhere else.

---

### Post by ishannbhatt on 2017-12-01
As far as I know, It is correct, the last run of the successful build had chmod a+x /tmp/buildd/vdl2xml-1.14.0/./configure line successful. Followed by mkdir -p .

---

### Post by cariboo on 2017-12-01
Moved here for a better fit.

---

