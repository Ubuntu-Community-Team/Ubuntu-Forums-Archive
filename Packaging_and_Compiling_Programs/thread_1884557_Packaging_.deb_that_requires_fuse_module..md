---
title: "Packaging *.deb that requires fuse module."
date: 2011-11-21
forum: Packaging and Compiling Programs
---

### Post by anatolik on 2011-11-21
Hi,

I am trying to debinize 'tup' build tool [http://gittup.org/tup/]("http://gittup.org/tup/"). The project does not use make, instead it uses custom 'bootstrap' script to build itself and this script needs fuse kernel module.

Here is my code [https://github.com/anatol/tup/tree/debian](https://github.com/anatol/tup/tree/debian) that debianizes this project.

When I run 'sudo pbuilder build ../tup_0.5-0ubuntu1.dsc' it fails with


> [ tup ] Parsing Tupfiles...
fuse: device not found, try 'modprobe fuse' first
fuse_mount: No such file or directory
tup error: Unable to mount FUSE on .tup/mnt
make: *** [build-stamp] Error 255
dpkg-buildpackage: error: debian/rules build gave error exit status 2


Does anyone knows from top of the head if there any restriction to use fuse module from pbuilder? I guess the problem is in 'chroot' that does not let current process to see /dev/fuse file.

Is there any way to use fuse from pbuilder? Did anyone do something similar?

---

### Post by Bachstelze on 2011-11-21
Just load the module before running pbuilder. Remember pbuilder is basically just a chroot, it uses the same kernel as the "host" system, with the same modules loaded.

You're not going to be able to get this easily (if at all) in the official repos, though, if that is your goal.

---

### Post by anatolik on 2011-11-21
> **Bachstelze said:**
> Just load the module before running pbuilder. Remember pbuilder is basically just a chroot, it uses the same kernel as the "host" system, with the same modules loaded.

You're not going to be able to get this easily (if at all) in the official repos, though, if that is your goal.

The build script works fine outside of pbuilder. I can run it a regular user and root. But this script fails when I run it from pbuilder.

Here is the build log with debug enabled [https://gist.github.com/1383660](https://gist.github.com/1383660)

I see that it creates a temporary user (pbuiler) and does "chroot /var/cache/pbuilder/build//2625 env LOGNAME=pbuilder su -p pbuilder".

1) Can it be that there is no /dev/fuse after chroot?
2) Can it be a permission issue. If I remember correctly to connect /dev/fuse a user should be in 'fuse' group. How to add this temporary user to 'fuse' group?


And yes I need to run this script in the official repo. My plan is to upload the debianized package to PPA.

---

### Post by Bachstelze on 2011-11-21
> **anatolik said:**
> My plan is to upload the debianized package to PPA.

Not going to happen. I would be very surprised if the build servers had the fuse module loaded, and of course you don't have root on them. Even if you manage to do it on a pbuilder at home, you have zero control over the build servers.

---

