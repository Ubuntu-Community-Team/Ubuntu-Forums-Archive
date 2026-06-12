---
title: "How to create deb of a Python script?"
date: 2009-12-11
forum: Packaging and Compiling Programs
---

### Post by bilalakhtar on 2009-12-11
I have a small PyGTK script that I would like to package in a DEB. How do I do it? I have read ways of packaging C++ source code in DEBs but I know that python scripts are not compiled like C++ but interpreted. So, how do I di it? :popcorn:

---

### Post by asipi on 2009-12-12
Hi,

I am in the same "shoe" :)
The best is to start the developing with quickly (sudo apt-get install quickly, and after quickly --help, or [quickly guide here]("http://blog.didrocks.fr/index.php/post/Build-your-application-quickly-with-Quickly%3A-part1")

If you have the application developed already your only chance is to get familiar with gnu autotools ([guide here]("http://www.galassi.org/mark/mydocs/autoconf_tutorial_1.html") and [here]("http://autotoolset.sourceforge.net/tutorial.html")) and adapt what you have learned. It is not so easy but with this way you can distribute your app as a tarball also, and you can upload it to your launchpad ppa. (I am in this phase, currently learning how to use the autotools)

You can also make a deb with dpkg --build <your_source_dir> but some preparation need for this. google for "debian packaging guide". However this type is not recommended, you cannot insert the result package in a repository only if you build up your own (knowledge need to do that).

---

### Post by Flimm on 2009-12-12
You can [create a setup.py distutils script and package it](http://ubuntuforums.org/showthread.php?t=1002909), or just use quickly.

---

### Post by Sandsound on 2009-12-12
I use this method :
[http://showmedo.com/videotutorials/video?name=linuxJensMakingDeb]("http://showmedo.com/videotutorials/video?name=linuxJensMakingDeb")

---

### Post by Brandon Williams on 2009-12-13
I got started with python packaging using [this guide](https://wiki.ubuntu.com/PackagingGuide/Python).

---

### Post by Jacks0n on 2009-12-14
Hi,

I hate to sound spammy (I'm the creator :-/), but checkout [Python Packager]("http://python-packager.com/") ([http://python-packager.com]("http://python-packager.com")). It'll create a deb and rpm file automatically. At least it *should* :), it's still in development. Just upload the source, put in the other information like description and name, and it'll email you when it's done.

Otherwise when I used to do it manually, I made a debian control file, a desktop file (to appear in the applications menu), and used dpkg to build it.

Hope that helps!

Jackson

---

