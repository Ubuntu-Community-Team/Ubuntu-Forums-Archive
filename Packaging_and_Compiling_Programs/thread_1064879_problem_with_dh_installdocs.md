---
title: "problem with dh_installdocs"
date: 2009-02-09
forum: Packaging and Compiling Programs
---

### Post by beaky@beaky.name on 2009-02-09
Hi Folks

I'm having my very first attempt at creating a .deb package for Ubuntu and I've come somewhat unstuck with the instructions given in the PackagingGuide part of the Ubuntu wiki.  I'm the lead developer on the WACS project ([https://launchpad.net/wacs](https://launchpad.net/wacs)) and I'm trying to build a deb package for the first time.  This will be an in-tree debian packaging.

In my rules files, I have a bunch of entries copied from the examples - the
first was:

    dh_testroot -a

which kept failing and I've now commented out.

The next one is with dh_installdocs where I'm really not understanding the message - the output goes:

Hostauth work completed.
dh_testdir -a
#dh_testroot
dh_installdocs --all RELEASENOTES README TODO DONE
install: cannot change owner and permissions of `debian/wacs/usr/share/docs/wacs': Operation not permitted
dh_installdocs: command returned error code 256
make: *** [binary-arch] Error 1
dpkg-buildpackage: failure: debian/rules build gave error exit status 2
pbuilder: Failed autobuilding of package
 -> Aborting with an error
 -> unmounting the dev/pts filesystem
 -> unmounting the proc filesystem
 -> cleaning the build env
    -> removing directory /var/cache/pbuilder/build/30201 and its subdirectories

OK, so what I'm doing is:

% sudo -s
[sudo] password for beaky: 
root@livia:~/wacs# debuild -S
[...]
root@livia:~/wacs# pbuilder build ../*.dsc
[...]
and then the error above...

The pbuilder preamble includes mention of fakeroot but I should be running as root anyway.

Please help!

Cheers, Beaky.

---

### Post by beaky@beaky.name on 2009-02-09
OK, I'm now getting a whole stream of error messages out of dh_fixperms as well - exactly the same error:

chown: changing ownership of `debian/wacs': Operation not permitted

and so on for a whole bunch of files.  There is obviously something pretty basic I'm missing here....

Cheers.
Beaky.

---

