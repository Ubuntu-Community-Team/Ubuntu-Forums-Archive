---
title: "Building a modified version of a package"
date: 2010-05-22
forum: Packaging and Compiling Programs
---

### Post by chaosinfurnus on 2010-05-22
In short, I am trying to modify and rebuild a package. That package is kde-window-manager (kwin), but I don't really know where to start.

I did some digging and apparently the source package for kde-window-manager is actually kdebase-workspace, which is also the source package to a whole bunch of other packages, which complicates things. I want the new kde-window-manager to be binary compatible with the rest of the current kde packages (the changes I have made are not something that would interfere with this).

I am not new to programming (C/C++/Java), the command line, and using package management tools (apt-*, aptitude, dpkg), but I am fairly new to building packages.

FYI, I am trying to write an effect for kwin and want to test it without messing with two separate kde installations conflicting each other, chroots, VMs, etc. until a later point in time. The effect I am trying to write is a screen capture effect that provides a way for any application to grab the screen via communication over dbus and shared memory. However, I do not (yet) require assistance with coding, only with building a package compatible that will work with the other kde packages currently in Ubuntu.

---

### Post by SevenMachines on 2010-05-27
hi there, i'm not entirely sure what your aiming to do so i'll apologise beforehand for how general what follows is. I would warn though, as you mention, kwin (kde-workspace) isnt the exactly the simplest package in the world!

Say you want to make come changes to a package already in the repository. You could use bzr, but i'll describe the other way, the way i vaguely know better :)

// get a copy of the source package
$apt-get source kwin

// get the build dependencies
$sudo apt-get build-dep kwin

// go into the source directory and check the patching system used
$ cd kdebase-workspace-4.4.2/
$ what-patch 
quilt

// ah, quilt, i'm sketchy on that! See bottom of post to actually make the changes

//after the changes are made you'll want to add a changelog entry
$dch -i

// and build
$debuild -b -us -uc

Hopefully now you'll have binaries to install that are the same as the repository versions but contain the changes you've made, added as an easily removable/postable patch.

To use quilt you might need to look at a tutorial, its a little more involved than previous patch systems. [Heres a quick explanation]("http://mybravenewworld.wordpress.com/2007/11/13/quilt-patch-management/"), and [this longer one seems quite good]("http://www.suse.de/%7Eagruen/quilt.pdf")

In general you want to do something like
// push all ( -a ) the current patches onto the stack
$ quilt push -a

// create a new patch
$ quilt new my-new-patch

// let quilt know the file (and each file) you want to change
$ quilt add thisfilehere

// edit the file, then refresh the patch when finished
$ quilt refresh

// pop all the patches off the stack, just my habit maybe
$ quilt -a pop

You should now have a new patch in debian/patches with all your changes in it

If this all seems quilt involved, quilt also has an 'quilt import some-other-patch' ability for external patches you may have created.

Hopefully some of that rambling explanation helps :)

---

