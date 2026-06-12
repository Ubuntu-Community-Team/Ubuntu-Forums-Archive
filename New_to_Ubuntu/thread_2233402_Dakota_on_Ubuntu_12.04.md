---
title: "Dakota on Ubuntu 12.04"
date: 2014-07-08
forum: New to Ubuntu
---

### Post by chris258 on 2014-07-08
Hi,
this is my first post and I am glad to enter the ubuntu forum :)
I am trying to install Dakota ([http://dakota.sandia.gov/distributions/dakota/5.2/install.html](http://dakota.sandia.gov/distributions/dakota/5.2/install.html)) from binary executable on Ubuntu 12.04.
I wrote the following on terminal (based on [https://software.sandia.gov/trac/dakota/wiki/PlatformSpecificSetup](https://software.sandia.gov/trac/dakota/wiki/PlatformSpecificSetup) | [https://software.sandia.gov/trac/dakota/wiki/CMakeFAQ](https://software.sandia.gov/trac/dakota/wiki/CMakeFAQ) | [https://software.sandia.gov/trac/dakota/wiki/PrerequisitesForCompiling](https://software.sandia.gov/trac/dakota/wiki/PrerequisitesForCompiling) | 

sudo apt-get install g++ gfortran 
sudo apt-get install liblapack-dev libblas-dev

wget [http://www.cmake.org/files/v2.8/cmake-2.8.9.tar.gz](http://www.cmake.org/files/v2.8/cmake-2.8.9.tar.gz)
tar xzf cmake-2.8.9.tar.gz 
cd cmake-2.8.9
./bootstrap --prefix=$HOME/local --parallel=4
make -j 4
make install
export PATH=$HOME/local/bin:$PATH 

downloaded Boost 1.49 from   [http://freefr.dl.sourceforge.net/project/boost/boost/1.49.0/boost_1_49_0.tar.gz](http://freefr.dl.sourceforge.net/project/boost/boost/1.49.0/boost_1_49_0.tar.gz)

 and then typed 

 tar xzf boost_1_49_0.tar.gz 
cd boost_1_49_0
./bootstrap.sh --with-libraries=filesystem,program_options,regex,serialization,signals,system --prefix=${HOME}/local/boost/1.49
./b2 installsudo apt-get install libopenmpi-dev openmpi-bin openmpi-docsudo apt-get install xorg-dev libmotif-dev 

 Then entered in the Bash shell (gedit .bashrc):

export 	PATH=$PATH:$HOME/Dakota/bin:$HOME/Dakota/test  	
export 	LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$HOME/Dakota/bin:$HOME/Dakota/lib  	

saved and closed - when checking the version (dakota -v), it gives 
dakota: error while loading shared libraries: libdakota_src.so

anyone knows what am I doing wrong? 
after fixing the bshrc, is it already compiled or should I make additional steps?
thanks in advance!
Chris

---

### Post by sandyd on 2014-07-08
Moved to Absolute Beginners Section

---

