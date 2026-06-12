---
title: "How to package a RealBasic application?"
date: 2011-08-25
forum: Packaging and Compiling Programs
---

### Post by RandomProgrammer on 2011-08-25
So I've spent quite a bit of time developing and testing an application in Real Studio (formally, Real Basic) and I really want to distribute my application in a PPA for Ubuntu users. I don't have time to rewrite the entire thing in C++ or any other programming language and I'm wondering if there's a way I can still provide my software to users through a PPA.

From what I've read, when you upload a source package, Launchpad will compile it for you. Obviously, this is easy for Java or C++ apps but there's no way Launchpad is going to compile a RS app. So how can I distribute my app via PPA?

Thanks!
Anthony

---

### Post by ubudog on 2011-09-02
You can probably do a PPA, a good start would be making a .deb.  My browser, UbuMonkey, was originally written in Real Basic, and I followed this guide to create a .deb.  Another developer created the PPA, so I'm not sure how to do that, sorry.  

Guide to create .deb:
[http://ubuntuforums.org/showthread.php?t=910717](http://ubuntuforums.org/showthread.php?t=910717)

(note, make sure the libs are with the executeable)

---

