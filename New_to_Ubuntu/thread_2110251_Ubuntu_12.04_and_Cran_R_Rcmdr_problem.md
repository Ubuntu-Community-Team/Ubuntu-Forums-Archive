---
title: "Ubuntu 12.04 and Cran R Rcmdr problem"
date: 2013-01-29
forum: New to Ubuntu
---

### Post by wfl on 2013-01-29
Hello Ubuntu users,

I would very much appreciate your assistance with the following please:
I'm trying to get Cran R's R commander working but I am not having any luck.

I am using Ubuntu 12.04.
I have installed Cran R (sudo apt-get install r-base-core). This is version 2.14.1
I have also installed Rcmdr (sudo apt-get install r-cran-rcmdr ). This is version 1.8-1-1. Everything seems to install OK, including dependencies. 
Trying to load the Rcmdr library in R gives the following message:

Loading Tcl/Tk interface ... done
> library(Rcmdr)
Loading required package: car
Loading required package: MASS
Loading required package: nnet
Error : .onAttach failed in attachNamespace() for 'Rcmdr', details:
  call: Commander()
  error: could not find function "assignInMyNamespace"
Error: package/namespace load failed for ‘Rcmdr’

I would appreciate any assistance please in getting this to work.

Thanks,

Regards,

Will.

---

### Post by monkeybrain2012 on 2013-01-29
There was a new requirement (don't remember which version) for R packages to have a namespace. so it could be that the package rcmdr in the repo is outdated (they usually are)

so instead of installing rcmdr from the repo via sudo apt-get can you remove the package first and reinstall it within R?

In the terminal type

```
sudo R
```and then at the R prompt
type 
```

install.packages('rcmdr')
```Then it will prompt you to choose a mirror to download the package.

**Edited:** If you start R without sudo the packages would be install in  your home directory, which is fine if you are the only user.

To get an up to date version of R you can either compile it (which is easy) or from this ppa

[https://launchpad.net/~marutter/+archive/rrutter](https://launchpad.net/~marutter/+archive/rrutter)

I usually install and update my R packages from within R rather than from repositories(to update, start R in the terminal with "sudo R" and then at the R prompt type "update.packages()" (no quotations)

Also if you need a GUI or IDE for R maybe you should checkout R studio. I found rcmdr to be primitive and buggy. I would rather use the terminal if I have to use rcmdr

[http://www.rstudio.com/](http://www.rstudio.com/)

---

### Post by wfl on 2013-01-30
Thank you for your reply monkeybrain2012.
I tried this, i.e. removed rcmdr, ran R as sudo and then within R did a  install.packages('rcmdr') 
I got the message

1: In getDependencies(pkgs, dependencies, available, lib) :
  package ‘rcmdr’ is not available (for R version 2.14.1)
2: Perhaps you meant ‘Rcmdr’ ? 

reran the command using Rcmdr this time, which seemed successful.
* installing *source* package ‘Rcmdr’ ...
** package ‘Rcmdr’ successfully unpacked and MD5 sums checked
** libs
gcc -std=gnu99 -I/usr/share/R/include      -fpic  -O3 -pipe  -g -c ismdi.c -o ismdi.o
gcc -std=gnu99 -shared -o Rcmdr.so ismdi.o -L/usr/lib/R/lib -lR
installing to /home/willf/R/x86_64-pc-linux-gnu-library/2.14/Rcmdr/libs
** R
** inst
** byte-compile and prepare package for lazy loading
** help
*** installing help indices
** building package indices ...
** testing if installed package can be loaded

* DONE (Rcmdr)

The downloaded packages are in
    ‘/tmp/RtmpFOEPKe/downloaded_packages’

Exiting R and running R again in standard user mode (i.e.  not sudo)
typing..
library(Rcmdr)

I get
 > library(Rcmdr)
Loading required package: car
Loading required package: MASS
Loading required package: nnet
Loading Tcl/Tk interface ... done

Also get a dialogue box instructing me of missing packages that need to be installed. I clicked YES, go ahead and install them.
This returns an error straight away..

Error : .onLoad failed in loadNamespace() for 'Rcmdr', details:
  call: structure(.External("dotTclObjv", objv, PACKAGE = "tcltk"), class = "tclObj")
  error: [tcl] bitmap "/home/willf/R/x86_64-pc-linux-gnu-library/2.14/Rcmdr/etc/R-logo.ico" not defined.

Error: package/namespace load failed for ‘Rcmdr’

Tried running R again in sudo mode, and running the same command i.e. library(Rcmdr). I get the same error message.
Tried loading/calling the tcltk library first and then the Rcmdr library but no good. Still get the above errors.

Any ideas?

---

### Post by monkeybrain2012 on 2013-01-30
Hmmm.. I don't know. I just tried install and run it myself and I have no problem. I have R 2.15.2 installed from the rrutter ppa above and installed Rcmder from within R (When I started Rcmdr there was a warning that it needs some further packages for some additional functions, since I am not going to use it,--removed it already,--I said no and the gui launched right the way, those additional packages are optional)

Edited: I may have an old version of R in an old machine with 11.04 which I haven't got around to update, will try install Rcmdr there tonight and see what happens.

---

### Post by monkeybrain2012 on 2013-01-30
Hi,

I checked, turned out that even on my old machine with Ubuntu 11.04 waiting to be removed the R version is updated(2.15.2) so I can't test with your version.

But I have tried installing Rcmdr in this machine, some observations may be helpful.

After installing I started Rcmdr and got the dialogue box saying that additional packages needed to be installed for full functioning of Rcmdr (the packages are lmtest, leaps and aplpack). I clicked "yes" and got a bunch of errors. Rcmdr did not load.

So I restarted R and typed library('Rcmdr') again and saw the same box, this time I clicked no, and the gui opens with no error this time. So I closed Rcmdr and then type detach("package:Rcmdr") 

I then manually installed those additional packages suggested in the dialogue boxvwith the install.packages() command. All three packages installed successfully, I then restarted Rcmdr and everything is working.

---

### Post by wfl on 2013-01-31
Thank you monkeybrain2012 for all your help. That sounds like a bit of a dose i.e. pain. I think I'll take your advice and try Rstudio.
Thanks again.

---

