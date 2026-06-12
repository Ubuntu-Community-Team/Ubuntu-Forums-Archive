---
title: "Pbuilder not picking up libming-dev build dependency"
date: 2008-04-21
forum: Packaging and Compiling Programs
---

### Post by JustinClift on 2008-04-21
Hi all,

Trying to package Salasaga (an eLearning IDE), and I can't seem to tell pbuilder to include the "libming-dev" build dependency. :(

This is from the debian/control file I'm using:

Build-Depends: autoconf, pkg-config, libgtk2.0-dev (>=2.2.0), libglib2.0-dev (>=2.2.0), libgconf2-dev, libgnome2-dev, libming-dev, libxml2-dev

(Not that it DOES have libming-dev in there)

This is from the dsc that's created from it:

Build-Depends: autoconf, pkg-config, libgtk2.0-dev (>= 2.2.0), libglib2.0-dev (>= 2.2.0), libgconf2-dev, libgnome2-dev, libming-dev, libxml2-dev

(Yep, it's there too)

But pbuilder keeps on failing:

<initial lines snipped>
Installing the build-deps
 -> Attempting to parse the build-deps : pbuilder-satisfydepends,v 1.29 2006/11/06 20:20:56 lool Exp $
 -> Considering build-dep autoconf
   -> Trying autoconf
 -> Considering build-dep pkg-config
   -> Trying pkg-config
 -> Considering build-dep libgtk2.0-dev (>= 2.2.0)
   -> Trying libgtk2.0-dev
 -> Considering build-dep libglib2.0-dev (>= 2.2.0)
   -> Trying libglib2.0-dev
 -> Considering build-dep libgconf2-dev
   -> Trying libgconf2-dev
 -> Considering build-dep libgnome2-dev
   -> Trying libgnome2-dev
 -> Considering build-dep libming-dev
   -> Trying libming-dev
       -> Cannot install libming-dev; apt errors follow:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libming-dev
W: Unable to locate package libming-dev
E: Could not satisfy build-dependency.
E: pbuilder-satisfydepends failed.
Copying back the cached apt archive contents
 -> unmounting dev/pts filesystem
 -> unmounting proc filesystem
 -> cleaning the build env 
    -> removing directory /var/cache/pbuilder/build//18631 and its subdirectories
$

Have already tried using the "create" and "update" commands for pbuilder, and although they complete, they don't appear to have added in libming-dev to anything.  pbuilder "build" still fails with this exact same error message afterwards. :-/

Also, libming-dev is 100% installed on this system, as the Salasaga package happily builds from source on it.

So, anyone have any ideas what I'm doing wrong?

This is really frustrating. :(

---

### Post by deuce868 on 2008-04-22
Just an idea here, but perhaps when you built pbuilder it isn't using all of the repositories? I'm not sure which is uses by default, but I know I generally create my pbuilder env. with 
sudo pbuilder create --distribution gutsy \
--othermirror "deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe multiverse

and I wonder if the libming-dev is outside the normal scope. 

You can actually get a shell into your pbuilder environment and probably check the apt sources.list file. Otherwise I'm not sure how to change that after the fact.

---

### Post by JustinClift on 2008-04-22
Hi,

Yeah, no real idea.

The workaround was to just use "debuild" instead of pbuilder.  The packages create and work fine from that. :)

---

