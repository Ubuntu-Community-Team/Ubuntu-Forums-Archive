---
title: "Failed to fetch... Size mismatch"
date: 2008-12-11
forum: Packaging and Compiling Programs
---

### Post by n_i_c_k on 2008-12-11
For a year or so I have used an internal package repository at my place of work.  I build packages with debuild, upload with dput and (re)create the Packages file and friends with mini-dinstall.

Since upgrading to intrepid, this process has been broken.  (I am not certain that the intrepid upgrade is the cause.)

Everything in the process proceeds as usual without apparent trouble, except that I cannot install an uploaded package with apt-get.  I can use 'dpkg --install' on the .deb file.  apt-get install produces

[FONT="Fixedsys"]Failed to fetch http://debs.ccmlan/stable/bbmd_0.01_all.deb[/url]  Size mismatch
[/FONT]
I'm none too sure even where to start investigating.  Any ideas welcome.  Is anyone else using debuild/dput/mini-dinstall in intrepid?

---

### Post by n_i_c_k on 2008-12-12
[https://bugs.launchpad.net/ubuntu/+source/mini-dinstall/+bug/307494]("https://bugs.launchpad.net/ubuntu/+source/mini-dinstall/+bug/307494")

---

