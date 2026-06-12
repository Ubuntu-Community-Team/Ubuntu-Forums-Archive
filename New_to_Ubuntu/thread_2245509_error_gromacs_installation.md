---
title: "error gromacs installation"
date: 2014-09-24
forum: New to Ubuntu
---

### Post by yaser2 on 2014-09-24
hi guys 
i got error after installed gromacs i installed the last version fftw  and cmake and after i installed gromacs-5.0 it was installed but when i  close terminal and open terminal another time and type this command  pdb2gmx and i get this command: install gromacs sudo apt-get install  gromacs .but i install it a dont know why i get this error.and when i  install this coomand gromacsVERSION 4.6.5 installed and its worked.what  can i do to installing gromacs-5.0.

thank you

---

### Post by steeldriver on 2014-09-24
Hello and welcome to the forums

Can you provide a link to the instructions you used to install gromacs? Since you appear to have installed it from source (rather than using the pre-built binary package from the repositories) it won't necessarily be located in a directory that's on your user's executable PATH. Perhaps the install process set a temporary PATH variable but didn't make it persistent by appending the new directory to the PATH in your .profile/.bashrc?

---

### Post by yaser2 on 2014-09-24
thank you for your reply

i used this website to download gromacs:  [http://www.gromacs.org/Downloads](http://www.gromacs.org/Downloads)
and i used this command for installing:
tar xfz gromacs-5.0.1.tar.gz
cd gromacs-5.0.1
mkdir build
cd build
cmake .. -DGMX_BUILD_OWN_FFTW=ON -DREGRESSIONTEST_DOWNLOAD=ON
make
make check
sudo make install
source /usr/local/gromacs/bin/GMXRC

but when i want used this:
-DREGRESSIONTEST_DOWNLOAD=ON

i got error that said cant download this and when i download it i cant install it actully idont know how can install this packag.

and this error:

Scanning dependencies of target regressiontests-notice
Regression tests not available
NOTE: Regression tests have not been run. If you want to run them from the build system, get the correct version of the regression tests package and set REGRESSIONTEST_PATH in CMake to point to it, or set REGRESSIONTEST_DOWNLOAD=ON.
Built target regressiontests-notice

---

### Post by yaser2 on 2014-09-24
hi 
how can i install regressiontests on ubuntu??

[http://gerrit.gromacs.org/download/regressiontests-5.0.1.tar.gz](http://gerrit.gromacs.org/download/regressiontests-5.0.1.tar.gz)

thank you

---

### Post by Vladlenin5000 on 2014-09-24
[http://www.gromacs.org/Developer_Zone/Programming_Guide/Regression_Tests](http://www.gromacs.org/Developer_Zone/Programming_Guide/Regression_Tests)

---

### Post by Vladlenin5000 on 2014-09-24
Do yourself a favor and go to the software center, search "gromacs", click more info, select the two optional packages if required for your intended use, then install...
Compiling from source and bleeding edge developer versions aren't meant for production usage, but for testing purposes only and by experienced users. Due to small differences in building environments several errors can happen. Most experienced user know what do when that happens and know how to interpret the messages; regular users don't.

---

### Post by bapoumba on 2014-09-24
Threads merged.

---

### Post by yaser2 on 2014-09-24
hi 

when i want use 
./gmxtest.pl all -noverbose

i get this error:

./gmxtest.pl all -noverbose
ERROR: Can not find executable gmx pdb2gmx in your path.
Please source GMXRC and try again.

---

