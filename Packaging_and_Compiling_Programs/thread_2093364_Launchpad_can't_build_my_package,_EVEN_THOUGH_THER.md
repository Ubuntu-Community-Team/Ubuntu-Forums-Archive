---
title: "Launchpad can't build my package, EVEN THOUGH THERE'S NOTHING TO BUILD."
date: 2012-12-10
forum: Packaging and Compiling Programs
---

### Post by JamesTheAwesomeDude on 2012-12-10
I was just trying to Debianize the game, [Mari0]("http://stabyourself.net/mari0/") (it's a mash-up of SMB and Portal,) and I got it working, and I uploaded it to Launchpad. It then tried to "build" it (it runs from source, so all it has to do is say that it was built,) and succeeded making the i386 build, but, for some reason, it won't work with the AMD64 build. (NOTE: I could successfully use debuild to build both architectures, both as source, and as binaries.)

I'm not quite sure why Launchpad's n00b computers can't mark files as "built" just because the computer is 64-bit, but I was wondering if there's any way to get this fixed.

The game is fully architecture-independent, but, once debianized, it "requires" the version of [Love]("http://love2d.org/") (the framework it's built on) to be of matching architecture. This means that when you download the i386 build of Mari0, it says that it won't work because you need the i386 build of Love (which you don't.) I have successfully made an AMD64 .deb file, and installed it, too. Why the computers at Launchpad can't do it, I have no idea.

---

### Post by JamesTheAwesomeDude on 2012-12-10
Hey, here's the build log: [https://launchpad.net/~jamestheawesomedude/+archive/ppa/+build/4052478](https://launchpad.net/~jamestheawesomedude/+archive/ppa/+build/4052478)
Error is at line 496:
```
[...]
dpkg-genchanges: error: cannot read files list file: No such file or directory
dpkg-buildpackage: error: dpkg-genchanges gave error exit status 2
******************************************************************************
Build finished at 20121210-1836
FAILED [dpkg-buildpackage died]
******************************************************************************
Finished at 20121210-1836
Build needed 00:00:02, 7344k disk space
RUN: /usr/share/launchpad-buildd/slavebin/scan-for-processes ['/usr/share/launchpad-buildd/slavebin/scan-for-processes', 'b7b4b3071f938d13748796d981f6d6f2d0a06c16']
Scanning for processes to kill in build /home/buildd/build-b7b4b3071f938d13748796d981f6d6f2d0a06c16/chroot-autobuild...
RUN: /usr/share/launchpad-buildd/slavebin/umount-chroot ['umount-chroot', 'b7b4b3071f938d13748796d981f6d6f2d0a06c16']
Unmounting chroot for build b7b4b3071f938d13748796d981f6d6f2d0a06c16...
RUN: /usr/share/launchpad-buildd/slavebin/remove-build ['remove-build', 'b7b4b3071f938d13748796d981f6d6f2d0a06c16']
Removing build b7b4b3071f938d13748796d981f6d6f2d0a06c16

```

---

### Post by milosmilos on 2012-12-11
I think this might help:
[http://ubuntuforums.org/showthread.php?t=1312655#2]("http://ubuntuforums.org/showthread.php?t=1312655#2")

In short: You do need the file "files list file"

---

### Post by JamesTheAwesomeDude on 2012-12-29
> **milosmilos said:**
> I think this might help:
[http://ubuntuforums.org/showthread.php?t=1312655#2]("http://ubuntuforums.org/showthread.php?t=1312655#2")

In short: You do need the file "files list file"

Nope... that didn't fix it...
```
[...]
 fakeroot debian/rules clean
debian/rules:2: /usr/share/cdbs/1/rules/debhelper.mk: No such file or directory
debian/rules:3: /usr/share/cdbs/1/class/cmake.mk: No such file or directory
make: *** No rule to make target `/usr/share/cdbs/1/class/cmake.mk'.  Stop.
dpkg-buildpackage: error: fakeroot debian/rules clean gave error exit status 2
debuild: fatal error at line 1350:
dpkg-buildpackage -rfakeroot -D -us -uc failed
james@james-OptiPlex-GX620:~/sandbox/Mari0/mari0-1.6$
```

I'm guessing that I made a mistake somewhere in the vein of "Error: directory not found: '/home/USERNAME/' is not a file or directory!" ;)
What did I do?

---

