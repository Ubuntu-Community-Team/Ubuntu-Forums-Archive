---
title: "Where to get the apache2 development packages (I need APXS for FrontPage)"
date: 2005-12-09
forum: Repositories &amp; Backports
---

### Post by J-D-Cronin on 2005-12-09
Hi, I've installed the server version of Ubuntu and I'm trying to get the frontpage  2002 extensions installed, It says 
> Cannot find Apache apxs at /usr/sbin/apxs
ERROR: Unable to install mod_frontpage dso

Exiting due to an error! Please fix the error and try again.


I read in a tutorial (for Fedora) that you have to ....
> A typical problem that is encountered installing FPSE on Fedora is that when running the install script  fp_install.sh to install FPSE, the script is unable to build the module as the APXS file can not be found.

In case you are asking, "What is an APXS file?" It is basically a Perl module and normally sits in the bin directory of an Apache install. But, as I mentioned, it does not get installed by default. **However it is available as part of the httpd-devel package**. Just check to make sure that you do not have the package already. If for some reason you do have this you can skip this step.


what is the equivalent to this in Ubuntu?

---

### Post by J-D-Cronin on 2005-12-14
Ok, so I ended up compiling apache2 from source, so that problem is solved... Is there another way?

---

