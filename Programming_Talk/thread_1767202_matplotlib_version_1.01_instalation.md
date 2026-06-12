---
title: "matplotlib version 1.01 instalation"
date: 2011-05-25
forum: Programming Talk
---

### Post by abottrill on 2011-05-25
Hi all,
I have been trying to install the new matplotlib on ubuntu 10.04LTS 64bit.

have down loaded the packages from source forge and followed the instruction[ here]("http://matplotlib.sourceforge.net/users/installing.html"). but when i check which version I have installed it is still 0.99.3.

I have made sure I have all dependencies using  
sudo apt-get build-dep python-matplotlib

[FONT=Arial]Anyone got any ideas or an idiots guide on how to do this?[/FONT]

---

### Post by MadCow108 on 2011-05-25
it probably installs itself into /usr/lib/pythonX.Y/site-packages or /usr/local
this directory is not searched by default for modules
try:
```
PYTHONPATH=/usr/lib/pythonX.Y/site-packages/ python -c "import matplotlib; print matplotlib.__version__"
```
or
```
PYTHONPATH=/usr/local/lib/pythonX.Y/site-packages/ python -c "import matplotlib; print matplotlib.__version__"
```

---

### Post by ladasky on 2011-06-01
On a related subject: does anyone know why Ubuntu has gone through fully three revisions without adding a more recent version of python-matplotlib to its standard repository?  We've been stuck on matplotlib 0.99.3 since Ubuntu 9.10 at least.  I'm currently using Ubuntu 10.10, but _[the package list for 11.04]("http://packages.ubuntu.com/natty/python/")_ indicates that 0.99.3 is STILL the supported version of matplotlib.

I'm having some build troubles with matplotlib 1.0.1, I'm chasing down dependencies manually.  I just know that if Ubuntu decided to bump up to a new revision, all that would be handled automatically.

---

### Post by MadCow108 on 2011-06-01
the matplotlib package comes from debian, and is packaged by volunteers. If you want software faster help the maintainers in doing so.

matplotlib 1.0.1 is now in debian and ubuntu 11.10 oneiric.
you can probably backport the 1.0.1 package to 10.10.

---

### Post by ladasky on 2011-06-01
> **MadCow108 said:**
> the matplotlib package comes from debian, and is packaged by volunteers. If you want software faster help the maintainers in doing so.

I doubt I have the computer skills for that.  I've haven't touched the operating-system level since Apple DOS, circa 1983.

> **MadCow108 said:**
> matplotlib 1.0.1 is now in debian and ubuntu 11.10 oneiric.  you can probably backport the 1.0.1 package to 10.10.

So, backporting an application of interest is something that users can choose to do themselves?  I didn't know that.  I've just been installing packages manually, then installing any packages which the error messages tell me I need when a build fails.  

I think [_this thread_]("http://ubuntuforums.org/showthread.php?t=268687") might tell me how to do it a better way?  It runs all the way back to 2006, and I've only just started reading it.

---

### Post by MadCow108 on 2011-06-02
you can request backports:
[https://help.ubuntu.com/community/UbuntuBackports#How to request new packages](https://help.ubuntu.com/community/UbuntuBackports#How to request new packages)
but you need to find someone who actually does the work.

if you want to backport yourself I would recommend the backportpackage script from the ubuntu-dev-tools. It requires a working pbuilder/cowbuilder/sbuild chroot or a ppa:

build with pbuilder
```
backportpackage -s oneiric -d maverick matplotlib -w /working/dir/ -b
```
resulting deb by default lands in /var/cache/pbuilder/result

build in ppa
```
backportpackage -s oneiric -d maverick matplotlib -u ppa:yourusername/targetppa
```
resulting deb can be installed by adding your ppa to your sources.list

or build it completely local (requires devscripts package):
```

#get package
dget -ux https://launchpad.net/ubuntu/+archive/primary/+files/matplotlib_1.0.1-2ubuntu1.dsc
cd matplotlib-1.01
# install build dependencies
mk-build-dep -i -r
#set version number so it will be superseeded when you upgrade your dist
dch --bpo
#build the package (without signing it)
debuild -us -uc
ls -ltr ../*deb
```

---

### Post by moteyalpha on 2011-11-22
Isn't that 
*mk-build-deps* -i -r
instead of
*mk-build-dep* -i -r

---

