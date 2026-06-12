---
title: "APT installs but can't authenticate my package"
date: 2009-03-12
forum: Packaging and Compiling Programs
---

### Post by DaveBeal on 2009-03-12
I'm a new Linux developer.  I've managed to create a .deb package that apt-get will install from a private local repository on my Ubuntu machine, but APT complains that the package can't be authenticated.

I think I've jumped through all the proper hoops.  I built the package with *dpkg-buildpackage -rfakeroot*, which asked me to sign the .dsc and .changes files.  I then created the Packages file with *apt-ftparchive packages* and created the Release file with *apt-ftparchive release*.  I then signed the Release file with *gpg -abo Release.gpg Release* and gzipped the Packages and Release files.

I copy all the files into a repository directory on my target machine and edit /etc/apt/source.list to look there.  *sudo apt-get update* seems to find my index files, saying "Get:1 file: Release.gpg", although I get "Ign file:" messages for my Release and Packages files.  (What does that mean?)  *sudo apt-get install* will then install my package, but complains that "The following packages cannot be authenticated!"

I have done *apt-key add* to add my GPG key on the target machine, and *apt-key list* shows it.  The key shows the same key ID and owner on both the development and target machines.

I notice that my /var/lib/apt/lists directory contains xxx_Release and xxx_Release.gpg files for all repositories except my local one.  Is this why APT can't authenticate my packages?  How do I fix this?

---

### Post by DaveBeal on 2009-03-12
I fixed the problem by doing two things.  I no longer gzip my Packages and Release files, and on the target machine I deleted everything in /var/lib/apt/lists (except lock and partial) and did the *apt-get update* again to repopulate it.  Now my package authenticates and installs.

---

