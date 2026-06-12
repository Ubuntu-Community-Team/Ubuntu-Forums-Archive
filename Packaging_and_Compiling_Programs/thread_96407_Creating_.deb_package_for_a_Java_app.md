---
title: "Creating .deb package for a Java app"
date: 2005-11-28
forum: Packaging and Compiling Programs
---

### Post by paulby on 2005-11-28
Hi,

I'm trying to create .deb packages for Project Looking Glass ( [http://lg3d.dev.java.net](http://lg3d.dev.java.net) ) and it's dependencies. This is mostly a java project so uses ant rather than make for build and deployment. I've updated the ant script to create the DEBIAN/control file and to run dpkg -b which all works fine, but I need to do more and I'm hoping someone here can offer guidance becuase thus far I've failed to find any documentation.

Firstly my shell scripts which are executable in the directory structure from which dpkg created the packages are being unpacked without being marked as executable. Is this expected, should I use postinst to fix this ?

How do I interact with the user during install time ?

I'm sure I'll think of other stuff later, but help with these issues would be a great start ;-)

Thanks

Paul

---

### Post by prince2689 on 2009-12-22
check out this page

  [https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)

Hope it will help you.....

---

### Post by mimadfli on 2009-12-24
I have compiled stuff from source before with the

---

