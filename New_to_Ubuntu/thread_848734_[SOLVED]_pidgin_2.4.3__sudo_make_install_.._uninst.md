---
title: "[SOLVED] pidgin 2.4.3  sudo make install .. uninstall ???"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by whitethorn on 2008-07-03
Hi yesterday I compiled pidgin because I wanted to get icq to work.  Thanx to a bunch of threads I figured out what needed to be changed in the source code, and successfully compiled pidgin.  For it to compile properly sudo checkinstall didn't work.  I had to use sudo make install.  My problem is I deleted the folder where I the compiled source code was in.  How do I go about getting rid of pidgin when I want to get the version from the repositories?

---

### Post by unutbu on 2008-07-03
Download the source again.
Run any configure script that comes with the source. This is done to rebuild the Makefile.
You do not need to run `make`.
To uninstall, most Makefiles define an uninstall command which you would run like this:
```

sudo make uninstall
```

I'm surprised checkinstall did not work. 
Do you know what the problem was?

---

### Post by ZabiGG on 2008-07-04
checkinstall needs to be installed first to work (it's optional)

sudo apt-get install checkinstall
or
search for checkinstall in the Synaptic Package Manager (System > Administration)


;)

---

### Post by bumanie on 2008-07-04
To get rid of what you installed > sudo aptitude remove <package name>

---

### Post by drs305 on 2008-07-04
A bit of elaboration about *checkinstall*. 

If you are compiling, using the command "*checkinstall*" instead of "make install" will make a .deb package (default) and, more importantly in this case, will track the installation to allow you to remove the package with the standard package managers (synaptic, aptitude, apt-get, etc).

As was mentioned, you have to install "checkinstall" and you run it with the "sudo" command.

---

### Post by khc on 2008-07-05
I should point out that, Richard Laager, one of the pidgin developers, uploaded some debs to his ppa archive:

[https://launchpad.net/~pidgin-developers/+archive](https://launchpad.net/~pidgin-developers/+archive)

---

