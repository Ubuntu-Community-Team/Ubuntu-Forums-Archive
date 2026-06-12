---
title: "[SOLVED] Want to install new package version."
date: 2008-11-21
forum: New to Ubuntu
---

### Post by boof1988 on 2008-11-21
I want to install [Tomboy v0.12.0](http://projects.gnome.org/tomboy/index.html).  Current (installed) version is Tomboy v0.10.2.

Synaptics Package Manager indicates v0.10.2 as latest version {see attachment}, but [Gnome Project >> Tomboy](http://projects.gnome.org/tomboy/download.html) indicates v0.12.0 as latest version {see attachment}.  So I can't figure out how to use Synaptic Package Manager to download the desired version.

When I click the download link for [Tomboy 0.12.0](http://projects.gnome.org/tomboy/download.html), it downloads the tar.gz just fine and opens up Archive Manager.  Now the tar.gz has to be "extracted" to a directory.

The question:  To what directory should it be "extracted" so it is installed properly?

References:
[Advanced Package Management](https://help.ubuntu.com/8.04/add-applications/C/advanced.html)
[apt-get Manual](http://manpages.ubuntu.com/manpages/hardy/en/man8/apt-get.html)

---

### Post by sancho panza on 2008-11-21
The download link that you mentioned is for the source code. To install using that would involve compiling that code and the like. I'm guessing you may not wish to do that. 

What I would do is to google around for the deb file for the latest version which can be installed automatically by the ubuntu, or wait till the latest version of tomboy is uploaded to the ubuntu repositories.

---

### Post by ohzopants on 2008-11-21
The tar.gz file you've downloaded is actually the source code for tomboy.  You're going to have to compile it yourself.  Usually .tar.gz have a README file.  Typically you can extract it pretty much anywhere (I usually use /opt) and the run:
```

./autoconfig
make && sudo make install

```

CHECK THE README FIRST!

If you do go with this route of compiling it yourself you should uninstall tomboy 0.10.2 from synaptic to avoid conflicts.

---

### Post by phidia on 2008-11-21
What you want to do is, in using the latest version, do a manual install also called installing from source.

You can extract the package-which should create a directory in your user's home directory. You then should look at the README file there.

Installing from source generally is done by opening a terminal and cd-ing into the directory created from unpacking the tar.gz file. You then would type "./configure" when that completes you type "make" and if that works with no errors you type "sudo make install".

There are many guides for this type of installation. The issue can be that this latest version doesn't work right or needs other packages, and that's why people use the package manager. It might not have the latest versions of all programs but it's normally easier than hand installing stuff.

---

