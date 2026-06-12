---
title: "omnet++ installation error in ubuntu 11.04"
date: 2013-04-11
forum: New to Ubuntu
---

### Post by adilbashir09 on 2013-04-11
Hello friends,

I have been trying to install omnet++ 4.1 on ubuntu 11.04, but while i  enter the "make" command, the following errors are shown which stop the  installation:
Below are the few last lines of my terminal window.

bismillah@ubuntu:~/Desktop/omnetpp-4.1$ make
.
.
.
.
.
.
cp splitvec /home/bismillah/Desktop/omnetpp-4.1/bin
cp omnetpp /home/bismillah/Desktop/omnetpp-4.1/bin
cp omnest /home/bismillah/Desktop/omnetpp-4.1/bin
cd /home/bismillah/Desktop/omnetpp-4.1/out/gcc-release/src/utils  && /home/bismillah/Desktop/omnetpp-4.1/src/utils/install-prog  opp_lcg32_seedtool /home/bismillah/Desktop/omnetpp-4.1/bin
/bin/sh: /home/bismillah/Desktop/omnetpp-4.1/src/utils/install-prog: Permission denied
make[2]: *** [all] Error 126
make[2]: Leaving directory `/home/bismillah/Desktop/omnetpp-4.1/src/utils'
make[1]: *** [utils] Error 2
make[1]: Leaving directory `/home/bismillah/Desktop/omnetpp-4.1'
make: *** [allmodes] Error 2

the "NO_TCL=1 ./configure" command works well and i have set the PATH variable also. kindly help as soon as possible

---

### Post by mörgæs on 2013-04-11
Hi, welcome to the fora.

11.04 is obsolete, so I recommend a clean install of 12.04.2. 

After that: 
[http://pharos.ece.utexas.edu/wiki/index.php/How_to_Install_OMNeT%2B%2B_4.2.2_on_Ubuntu_12.04]("http://pharos.ece.utexas.edu/wiki/index.php/How_to_Install_OMNeT%2B%2B_4.2.2_on_Ubuntu_12.04")

---

