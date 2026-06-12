---
title: "Building patched/updated versions of applications to replace versions from the repos"
date: 2009-01-02
forum: Packaging and Compiling Programs
---

### Post by retrovertigo on 2009-01-02
There are a few applications (Pidgin and VLC, to name a couple) that Ubuntu doesn't really keep up-to-date in their repositories.  What I would like to do is grab the source and compile, then package them as .deb files.  I am familiar with how to compile from source and how to create a .deb, but I've noticed that some programs (like VLC, for instance) have a TON of configuration options, and I inevitably find that I've left one out when I compile it, and certain features don't work or are missing.

I've been searching for some documentation on how Ubuntu builds their applications, specifically what options are appended to the **configure** command, so that I can build applications that integrate with Ubuntu as well as possible.  However, I have not yet found anything.  Does anyone know how I would go about finding this information?

---

### Post by geraldm on 2009-01-03
Perhaps you might get hints from the files PACKAGE_VERSION-?.diff.gz and *.dsc  for the version-build used by  the ubuntu/debian package in the repository?  
You also need the build dependency packages named.

Gerald

---

