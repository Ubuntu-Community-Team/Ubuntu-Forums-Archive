---
title: "Help Creating Source .dsc Package"
date: 2008-01-17
forum: Packaging and Compiling Programs
---

### Post by derrick81787 on 2008-01-17
Hello, everyone.  I've been working on a program for Ubuntu that can be used to rip DVDs, and I finally have a stable version.  I've even manually made some binary .deb packages that can be used to install/uninstall the program.

I'm wanting to eventually get my program into the universe/multiverse repository for Ubuntu (whichever repository it belongs in), but I'm having some major difficulties creating a .dsc package for it.  The problem is the makefile and configure script that the backend (HandBrakeCLI) uses.  It isn't possible to pass an installation prefix to the configure script, and therefore building the .dsc package fails every time.  I used Glade to create the GUI, and so there is no problem with the frontend, just the backend.

I know practically nothing about Makefiles or Jamfiles (HandBrakeCLI uses Jam, which is part of the problem), and so I really don't know how to fix this issue, especially since automake compliant makefiles seem to be so large and complicated.

Basically, I was wondering if there is anyone on the forums here who would be willing to help out with this issue.  I think that this is the only major obstacle in the way of this program being included in the repositories, and I think it is a great alternative to things like and acidrip and dvdrip (although I may be a little subjective, I suppose).

If you would like to download my source code, a direct link is available here:
[COLOR="SandyBrown"][http://m-sack.net/files/derrick/ghandbrake_0.1_source.tar.gz]("http://m-sack.net/files/derrick/ghandbrake_0.1_source.tar.gz")[/COLOR]

Also, if you want to read about it, see screenshots, or just visit the webpage, the webpage is here:
[COLOR="SandyBrown"][http://ghandbrake.ubuntuisms.com]("http://ghandbrake.ubuntuisms.com")[/COLOR]

Any help at all would be greatly appreciated, and I'd be more than happy to add you to the list of authors of the program, if you would like.

Thanks,
Derrick

---

