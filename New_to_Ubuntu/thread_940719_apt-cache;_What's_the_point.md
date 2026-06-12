---
title: "apt-cache; What's the point?"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by adamogardner on 2008-10-07
hey I'm trying to figure out what it means that apt has a cach and you can manipulate files in this cache.  Can this be explained better?  Is cache the repository from whence apt got?  In what ways are these files(I assume to be packages) manipulated?  I'm just trying to get a better understanding of this.

---

### Post by bodhi.zazen on 2008-10-07
[http://www.linux.com/feature/55828](http://www.linux.com/feature/55828)

> 
Before installing packages, experienced Debian users may want to learn as much as possible about the packages they are installing. One way to check this information is through the Debian [Packages page]("http://www.debian.org/distrib/packages"), but that page is so heavily used that it is often slow, and sometimes crashes for hours or even days at a time.
  Instead, experienced users rely on apt-cache and its series of commands. Typing apt-cache showpkg *packagename*  from any account will give information about a package's current version and the latest version available from the repositories in sources.list, as well as the package's dependencies and its reverse dependencies -- that is, the packages dependent on it. You can also get dependency information using apt-cache depends *packagename*  or with apt-rdepends. Similarly, apt-cache dump gives a list of all installed packages, and apt-cache stats reports detailed statistics about installed packages as a whole. And if you want to check whether a package is available, then apt-cache --full search *packagename*  can give you the answer, complete with the available version, MD5 sum, and encryption keys. If you have trouble remembering the exact package name, you can enter regular expressions to expand your search.


For the abridged version : [http://wiki.vpslink.com/Linux_Command_Reference:_apt-cache_(Debian,_Ubuntu](http://wiki.vpslink.com/Linux_Command_Reference:_apt-cache_(Debian,_Ubuntu))

---

