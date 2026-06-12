---
title: "Launchpad fails to build a package for my PPA"
date: 2012-06-15
forum: Packaging and Compiling Programs
---

### Post by AZorin on 2012-06-15
Hello everyone.
I'm trying to build a package on Launchpad's Debian build system for PPAs but I'm having some issues with a certain package.
The package I'm trying to build (zorin-xwinwrap) contains a source C file which I'm trying to get to compile and build on Launchpad's server so that it would install and work on 32 bit (i386) and 64 bit (amd64) systems. Unfortunately I keep on getting an Error code 2 with the debian/rules file and I have no clue how to fix this issue.
The following link is the source package of the software I'm trying to add to my PPA: [http://goo.gl/GjZvd](http://goo.gl/GjZvd)
The following link is the buildlog for the failed package on Launchpad: [http://goo.gl/6A2rQ](http://goo.gl/6A2rQ)
Just in case anyone will need it to fix this issue, here is the link to the packages in my PPA: [http://goo.gl/uODZ7](http://goo.gl/uODZ7)

I would greatly appreciate any suggestions if anyone may have any.
Thank you for your time.

---

### Post by SevenMachines on 2012-06-15
linking libraries need to come after the objects they link against since --as-needed is enabled by default these days.
[http://www.gentoo.org/proj/en/qa/asneeded.xml](http://www.gentoo.org/proj/en/qa/asneeded.xml)

Look for a makefile, is there -lsomelib down as an LDFLAG? move these to LDLIBS and try

---

