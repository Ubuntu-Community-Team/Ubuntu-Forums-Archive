---
title: "Create an Upstream Tarball"
date: 2012-11-22
forum: Packaging and Compiling Programs
---

### Post by bronkeydain on 2012-11-22
I am trying to work out how to create a proper upstream tarball? It is so hard to find info on this. All guides assume you download the tarball somewhere. Other info seems to suggest everybody creates these using GIT. 

There must be a way to create an upstream tarball without GIT. Are there other tools than GIT that can do this? Can they be created manually? 

I can create a tarball, stick my source files in it, name it whatever_1.0.orig.tar.gz and build my package no problem. I want to do it the proper way however... Normally there are loads of make files and stuff in the tarball. 

Does anybody have any info/guides/ideas on this at all?

---

### Post by Bachstelze on 2012-11-23
Instead of ranting, tell us what you are trying to do. Apparently, you are trying to package some code. Where does it come from? Is it code you have written yourself or you got from somewhere else?

---

### Post by bronkeydain on 2012-11-23
Ranting?

I am trying to build a package (source and binary) for:
1) files (shell scripts, configuration files)
2) C source code
3) QT code

So that is three different kinds of packages, not one package with all of those. These packages are for internal use only, no upstream stuff.

While I have been able to do all the above, I have just put my source code in the tarballs. The upstream tarballs I have seen contain loads of files and I wonder what the guidelines/concepts are for creating those tarballs. I don't even know why they have to be there. 

Even though the packages aren't going to be upstream, I would like to know the proper way of making an upstream tarball.

As I said I cannot find any info on creating those. Almost all info assumes someone has made me an upstream tarball, ready to go.

Cheers

---

### Post by bronkeydain on 2012-11-26
Although I still have not found any definate answer I think what needs to be in the tarball is:
1) Your source files
2) Makefile (logically this is not needed when packaging files or shell scripts)

-----------------------------------------------------

If you have homewritten software that you would like to package and your packages are for internal/personal use only, this is the workflow I worked out (Example is helloworld c code):

NOTE: I am a noob and I have little time at the moment; The workflow below is a bit cryptic and might contain errors... just trying to help

-----------------------------------------------------
(you need packages: build-essential, debhelper, devscripts)

1) make a directory ~/packaging/helloworld-1.0
2) Put your helloworld.c sourcecode in there
3) Put your Makefile in the same directory
4) cd ~/packaging
5) tar czf helloworld_1.0.orig.tar.gz helloworld-1.0
6) cd helloworld-1.0
7) dh_make (this will create a lot of debhelper files, most are not needed. The minimum you need are: debian/changelog which you can also create using "dch -v 1.0", debian/rules, debian/compat, debian/control)
8) debuild -us -uc (this will create source and binary package that are not GPG signed)
9) If you want to automatically resolve runtime dependencies you will have to set up a local repository. 

I wish I had more time to document this properly but at present I don't. I WILL do this in the near future because for this particular case I found documentation is confusing or scarse.

---

