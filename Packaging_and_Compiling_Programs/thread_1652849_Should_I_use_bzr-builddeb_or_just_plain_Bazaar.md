---
title: "Should I use bzr-builddeb or just plain Bazaar?"
date: 2010-12-25
forum: Packaging and Compiling Programs
---

### Post by Flimm on 2010-12-25
Merry Christmas and/or happy holidays!

I have a quick question about bzr-builddeb. If the upstream source code is in Bazaar revision control already, why not just create a branch of the trunk, add debian/ files, and merge with every upstream release? What is the advantage of using bzr-builddeb in that case?

To be clear, the bzr-builddeb method is [documented here](http://jameswestby.net/bzr/builddeb/user_manual/normal.html).

The "plain Bazaar" method is:
1. To create a new debian packaging branch:
```
bzr branch project-trunk debian-branch
cd debian-branch
# create debian/files
bzr add debian/
bzr commit -m message
```
2. With every upstream release, do the following:
```
bzr merge project-trunk
# modify debian/files
bzr commit -m message
```

---

### Post by MadCow108 on 2010-12-26
in general you should not use vcs snapshots for creating debian packets (when aimed for a official repository).
You may not be able to get the same support from upstream as with their regular releases and it is a lot harder for users to see which features/bugs their installed software really has.

So there is normally no gain in using the upstream vcs and adding a debian branch as you should only be using the release tags of the vcs anyway.
And you have the additional burden of repackaging the source tarball.

What you can do of course is add upstream vcs as a remote to your bzr-builddeb tree for easier cherry-picking of patches (which then go into debian/patches under source format 3.0).
But your debian package should stay based on the released tarball.

---

### Post by Flimm on 2010-12-27
> **MadCow108 said:**
> in general you should not use vcs snapshots for creating debian packets (when aimed for a official repository).
You may not be able to get the same support from upstream as with their regular releases and it is a lot harder for users to see which features/bugs their installed software really has.
In my case, the upstream developers would be support this move and would tag their branch appropriately for releases.

> And you have the additional burden of repackaging the source tarball.
You hit the nail on the head. My "plain Bazaar" method builds the package as if it were native, when it is not (see [native vs non-native](http://wiki.debian.org/DebianMentorsFaq#WhatisthedifferencebetweenanativeDebianpackageandanon-nativepackage.3F)). It also includes the .bzr directory in the source tarball. That is why it is not suitable.
Using bzr-builddeb forces one to grab upstream release tarballs. Having a .orig.tar.gz tarball and a packaging .diff.gz file keeps the distinction between cross-distro upstream code and distro-specific downstream packaging clear.

Thanks for your help. I needed someone to bounce ideas off.

---

