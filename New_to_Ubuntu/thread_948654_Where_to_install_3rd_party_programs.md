---
title: "Where to install 3rd party programs"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by hwttdz on 2008-10-15
Where does tradition dictate that one installs third party programs.  I've now been using ubuntu and various other flavors of linux for years without ever really having to install much that wasn't in a repository.  Anyways should I install in 
/usr/local/sbin
/usr/local/bin
/usr/sbin
/usr/bin
/sbin
/bin
these are what's in my path by default so I assume it should go in one of these.  But then again the program probably wants its own folder in which to put all its data files and whatnot and I don't want that cluttering up any of these folders.  So should I make a progname/ dir in one of these install there and make a link from .. to progname/progname?  Thanks.

---

### Post by schnauzer93 on 2008-10-15
I usually create a new folder in /opt and install there.

---

### Post by Nepherte on 2008-10-15
Typically, programs that come with the linux distribution (things you can install with the package manager) are stored in /usr (libraries in /usr/lib, symbolic links to run the program in /usr/bin, etc...), other programs you install yourself can be put into /opt, though /usr isn't forbidden.

---

