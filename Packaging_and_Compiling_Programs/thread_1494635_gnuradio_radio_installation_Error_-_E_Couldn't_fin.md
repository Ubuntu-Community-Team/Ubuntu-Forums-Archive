---
title: "gnuradio radio installation: Error - E: Couldn't find package lib libboost-all-dev"
date: 2010-05-27
forum: Packaging and Compiling Programs
---

### Post by ph.anilsharma on 2010-05-27
Hi everyone , 
 As i am new in this part of the world , hope mistakes will be  ignored... I use ubuntu 10.04 , and i am trying to run Gnuradio  on my  system.I was trying to update the dependencies using the command  

$ sudo apt-get -y install libfontconfig1-dev libxrender-dev  libpulse-dev swig g++ automake libtool python-dev libfftw3-dev \ 
libcppunit-dev libboost-all-dev libusb-dev fort77 sdcc  sdcc-libraries \ 
libsdl1.2-dev python-wxgtk2.8 subversion git-core guile-1.8-dev \ 
libqt4-dev python-numpy ccache python-opengl libgsl0-dev \ 
python-cheetah python-lxml doxygen qt4-dev-tools \ 
libqwt5-qt4-dev libqwtplot3d-qt4-dev pyqt4-dev-tools 

but i got an out put with error saying ,

 - - - - - - 
 - - - - - - 
 - - - - - - 
E: Couldn't find package lib libboost-all-dev. 
Can any one guide me to resolve the dependencies and hence i can  install gnuradio in my system .
Please do provide me the best and most simple way to install the gnuradio without any problem.
i have also referred to many forums and also the gnu official site installation guide but of no output :confused:
A small spark could be a lighthouse for me.Thanks 
Thanking you all in advance.

---

### Post by SevenMachines on 2010-05-27
Hi there, can I just clear up what you are trying to do? If you are trying to install gnuradio this is already in the ubuntu repositories (along with 1000's of others!) and can be installed from,
1. The Ubuntu Software Centre in the main menu
2. A package manager such as synaptic in the main menu->system->prefrences
3 or the command line 
$ sudo apt-get install gnuradio

[See Installing Software in the Ubuntu Help Guide for more]("https://help.ubuntu.com/10.04/add-applications/C/index.html")
If this is what you're trying to do questions should go into one of the [main support forums ]("http://ubuntuforums.org/forumdisplay.php?f=327")

If this isnt what you want just reply here. 

Compiling dependency likely to be libboost1.40-all-dev (the versioned libboost dev packages seem to be the preferred format these days) although it should really use the specific boost dev packages it needs rather than use the 'all' meta-package, but thats a packaging thing :)

---

