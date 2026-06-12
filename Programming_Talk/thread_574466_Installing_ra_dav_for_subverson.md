---
title: "Installing ra_dav for subverson"
date: 2007-10-12
forum: Programming Talk
---

### Post by np_ on 2007-10-12
Ubuntu 7.04

I've installed the subversion package via apt-get. I want to be able to access an svn repository over http. I've read I need ra_dav to do this. How do I get it?

I've read [https://wiki.ubuntu.com/Subversion](https://wiki.ubuntu.com/Subversion) but that seems to be about setting up a svn repository rather than simply accessing an existing one.

My svn version info is:

svn, version 1.4.3 (r23084)
   compiled Oct 12 2007, 13:28:55

Copyright (C) 2000-2006 CollabNet.
Subversion is open source software, see [http://subversion.tigris.org/](http://subversion.tigris.org/)
This product includes software developed by CollabNet ([http://www.Collab.Net/](http://www.Collab.Net/)).

The following repository access (RA) modules are available:

* ra_svn : Module for accessing a repository using the svn network protocol.
  - handles 'svn' scheme
* ra_local : Module for accessing a repository on local disk.
  - handles 'file' scheme

---

### Post by ascandroli on 2007-10-13
I had the same problem just now.
It looks like svn was compiled without webdav support.
To solve it I've installed the previous version: 1.4.3dfsg1-1ubuntu1

Your version is 1.4.3dfsg1-1ubuntu1.1
svn, version 1.4.3 (r23084)
compiled Oct 12 2007, 13:28:55

You need to force synaptic to install 1.4.3dfsg1-1ubuntu1
svn, versión 1.4.3 (r23084)
compilado Mar 28 2007, 22:49:14

You need to force this version for both subversion and libsvn1 packages.

---

### Post by np_ on 2007-10-13
Thanks for the info. Following the instructions [here]("https://help.ubuntu.com/community/SynapticHowto#head-ec06ac55f7b20957887c4b9cfdea6efd07727415"), I had problems making Synaptic work. I got it to work with the following commands:

sudo apt-get install libsvn1=1.4.3dfsg1-1ubuntu1
sudo apt-get install subversion=1.4.3dfsg1-1ubuntu1

Is there a way to have Synaptic not propose updates to those two packages?

---

### Post by ascandroli on 2007-10-14
In Synaptic, if you click on the package you want to hold back from updates, then go to the Package menu you can choose Lock Version.
A little padlock should end up next to the package.

From the command line:
echo "libsvn1 hold" | sudo dpkg --set-selections
echo "subversion hold" | sudo dpkg --set-selections

That will tell apt to place these packages on hold. It won't upgrade these packages, even if it means holding back loads of upgrades that depend on the upgraded versions.

---

### Post by np_ on 2007-10-14
Thanks again!

---

### Post by ryun on 2007-10-15
Thanks two friends. :KS

---

### Post by johann_p on 2007-10-16
The update manager today (2007-10-16) provided an update that makes ra_dav work again.
So locking to a previous version should not be necessary any longer.

---

