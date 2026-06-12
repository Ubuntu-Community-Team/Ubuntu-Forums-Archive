---
title: "Author of an app, confused about packaging"
date: 2010-05-20
forum: Packaging and Compiling Programs
---

### Post by lunarcloud on 2010-05-20
Hey, I wrote a little Grub2 config app in Qt Creator. [http://code.google.com/p/qgrub2editor/](http://code.google.com/p/qgrub2editor/)

As you can see I do have a deb package, that was easy, just drop things into a fakeroot folder and make a control file.

Now, however, I want to get it into my PPA, but I cannot figure out how to do this whole debian/rules .diff .orig.gz THING! It's very confusing. I've looked at the ubuntu wiki pages and they're of little help. It's constantly assuming I'm packaging something that someone else has written that already has a bunch of useful things there for you.

I wish I could just drop my package into the ppa...

Honestly, I want to clean my app up enough to submit for proposal for kubuntu 10.10 or more realistically now 11.04 since their TODOs are already done.

I'm rather discouraged by this other way of packaging.

Edit: I've actually done the dh_make thing, and I think I'm just having an issue with the debian/rules, and why the build package programs complain about not knowing where to get original sources from.

---

### Post by SevenMachines on 2010-05-20
Don't be discouraged! It seems like the previous deb file was essentially an archive with a control file in it, this may be installable but its not a 'debianized' package. The 'other way' is actually the only proper way i'm afraid.
Luckily, this is actually quite simple. For the source-ball you mention for example...

$ tar -zvxf qgrub2editor_1.2.tar.gz

// But packaging expects the directory form <package>-<version>, so, for example
$ mv qgrub2editor qgrub2editor-0.1

// now let dh_make create a bunch of example files and a tarball for us
$ cd qgrub2editor-0.1
$ dh_make -createorig

technically you could probably run debuild now and have it build a package! but of course, you'll actually want to edit the files in the debian directory and remove any examples you dont need. Especially important is the control file as you mention, the copyright file, and usually the rules file but in this case dh_make should create a good enough rules file to not need to change it. And the changelog.

Depending on how your source is set up you might need a debian/install file too, for instance with something like
QGrub2Editor   /usr/bin
in it. in general
path/to/thing/to/install     /place/to/install/it/on/system

the install file, or <binary-package-name>.install file is used by dh_install to decide what goes where on installation (which is is automatically run if the debhelper cdbs rules are included in the rules file, as they are automatically in this case)

The [Packaging Guide]("https://wiki.ubuntu.com/PackagingGuide/Complete") is really the place to go for more detailed information though.

App looks good by the way, good luck!

---

