---
title: "How to build packages"
date: 2004-12-22
forum: Packaging and Compiling Programs
---

### Post by Smash on 2004-12-22
Hello, how could i build a .deb packages from a source tarball??
I think something like "Checkinstall"...

Thanks.

---

### Post by randy on 2004-12-22
The debian website has a very in depth guide on packaging.  It's a bit hard to learn (I'm working on it now). I found it very usefull when I learned how to build RPMs when I using Redhat/Fedora.

---

### Post by Smash on 2004-12-22
Checkinstall builds packages *.deb, *.tgz or *.rpm.
I can use this software to build *.deb for Ubuntu?

---

### Post by Quest-Master on 2004-12-22
Is it possible to make a .deb for a file that is compiled using SCons and not make ([http://scons.sf.net](http://scons.sf.net))?

---

### Post by Smash on 2004-12-23
Thanks.
Now i try it.  :D

---

### Post by Sniffer on 2004-12-23
Thks for the site will try also.

:)

---

### Post by oskude on 2005-11-26
[QUOTE=Quest-Master]Is it possible to make a .deb for a file that is compiled using SCons and not make ([http://scons.sf.net](http://scons.sf.net))?[/QUOTE]i was able to use```
sudo checkinstall scons install
```but im not happy with it, cause "sudo scons install" re-compiles (i made "scons" before) the source and now i have compiled files with root user/owner in my home dir... (i dont like to compile as root user)

checkinstall version 1.6.0 (i installed the deb from their site: [http://asic-linux.com.mx/~izto/checkinstall/download.php](http://asic-linux.com.mx/~izto/checkinstall/download.php)) has a nice feature, "--install=no" so it wont install the package automaticly...

---

### Post by dudus on 2005-12-01
Whats the diference between debian debs and ubuntu debs. How could I add my debs to the backports? Could I setup a private repo server?

---

### Post by oskude on 2005-12-02
[QUOTE=dudus]Whats the diference between debian debs and ubuntu debs.[/QUOTE]AFAIK, the content of the debs are "tuned" to the corresponding systems (like library versions, paths...)
[QUOTE=dudus]How could I add my debs to the backports?[/QUOTE]try the wiki for an answer to that. i assume you have to become a member, and then just add your debs (if not someone else has done it) to the appropiate reposity... but that way you "should" also be responsible of "your" package (respond to bug reports and so).
[QUOTE=dudus]Could I setup a private repo server?[/QUOTE]yes, try google or maybe even here in forum/wiki (this is a "common" task, but ive never done that)

---

### Post by cjssmo on 2007-05-21
you can use checkinstall to make .deb's but I remember reading somewhere that they do not conform to debian policies.  Hope this helps

---

