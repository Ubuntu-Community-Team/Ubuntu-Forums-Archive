---
title: "tcl/tk support on trusty"
date: 2015-10-31
forum: Programming Talk
---

### Post by mark allyn on 2015-10-31
Hello everyone,

I am attempting to install an IDE (R Commander) for R, the statistical package.  When I attempt to do the installation R reports that my system does not support TCLTK.  I had thought that TCLTK was supported, but went ahead and installed TCL8.5 anyway.  Still no luck.  I've checked the tree and it appears to be located in /usr/lib.  Any suggestions?

Thanks,
Mark Allyn

---

### Post by tgalati4 on 2015-10-31
What version of Ubuntu?  In 14.04,* r-base* requires* r-core* which requires *tcl8.5* and *tk8.5*

```
apt-cache policy tcl8.5 tk8.5
```

---

### Post by mark allyn on 2015-11-02
Hello Tgalati4:

Thanks for responding.  Using your command, here's what comes back on the shell:
```


tcl8.5:
  Installed: 8.5.15-2ubuntu1
  Candidate: 8.5.15-2ubuntu1
  Version table:
 *** 8.5.15-2ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
tk8.5:
  Installed: 8.5.15-2ubuntu3
  Candidate: 8.5.15-2ubuntu3
  Version table:
 *** 8.5.15-2ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status

```

I'm not entirely sure what this is telling me in all details, but it appears that TCL and TK are both installed.  Any further suggestions?

Regards,
Mark

---

### Post by tgalati4 on 2015-11-03
```
sudo apt-get install -f
```

---

### Post by steeldriver on 2015-11-03
**How **are you attempting to install R Commander (as a pre-built binary package from the repo? using install.packages() from inside R, ...)? What is the actual error message?

---

### Post by mark allyn on 2015-12-08
Hello tgalati and steeldriver,

Sorry I was unable to respond timely to your suggestions--had shoulder surgery that rendered me one-handed.

Anyway, libtcl8.6.so and libtcl8.5.so (and similarly, libtk.so) along with the 8.5 versions are installed in /usr/lib/i386-linux-gnn/.  I will report back shortly on the precise error message from R as Steeldriver suggests.

Of course, it is possible that R's library search path is set to find them.., I suppose.

Cheers,
Mark

---

### Post by mark allyn on 2015-12-08
tgalati and steeldrivers:

The precise message from R is:

   
 error: Tcl/Tk support is not available on this system

Not very helpful, is it.  BTW, using an R command I set the library search path to TCL/TK so's.  

Mark

---

### Post by tgalati4 on 2015-12-08
I don't have R installed on this laptop, so I can't test it.  But, let's go back to basics.  It appears that you are running 64-bit packages (amd64).  But you also have 32-bit packages installed (anything in i386).  So perhaps you have a multiple-architecture system with both 64-bit and 32-bit packages.  There are some steps to perform to get this to work:  [https://cran.r-project.org/doc/manuals/r-release/R-admin.html#Multilib](https://cran.r-project.org/doc/manuals/r-release/R-admin.html#Multilib)

Do you have the recommended packages installed?

```
apt-cache policy r-recommended
```

It is a metapackage that includes the following:

> tgalati4@Mint17 ~ $ apt-cache depends r-recommended
r-recommended
  Depends: r-base-core
  Depends: r-cran-boot
  Depends: r-cran-cluster
  Depends: r-cran-foreign
  Depends: r-cran-kernsmooth
  Depends: r-cran-lattice
  Depends: r-cran-mgcv
  Depends: r-cran-nlme
  Depends: r-cran-rpart
  Depends: r-cran-survival
  Depends: r-cran-mass
  Depends: r-cran-class
  Depends: r-cran-nnet
  Depends: r-cran-spatial
  Depends: r-cran-codetools
  Depends: r-cran-matrix


---

### Post by steeldriver on 2015-12-08
Thanks for updating with the error message - for completeness, can you post the actual command(s) you are using for the install?

---

