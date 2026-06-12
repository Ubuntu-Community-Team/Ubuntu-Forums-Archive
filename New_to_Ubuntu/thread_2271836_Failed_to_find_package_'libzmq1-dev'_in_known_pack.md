---
title: "Failed to find package 'libzmq1-dev' in known package repositories"
date: 2015-04-02
forum: New to Ubuntu
---

### Post by raihana on 2015-04-02
Hi,

I'm a user of Ubuntu 14.04. I want to install GNUradio from source of this link:
[https://gnuradio.org/redmine/projects/gnuradio/wiki/InstallingGRFromSource](https://gnuradio.org/redmine/projects/gnuradio/wiki/InstallingGRFromSource)

```
userr@userr-X455LDB:~$ sudo apt-get install wget
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wget is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
userr@userr-X455LDB:~$ wget [http://www.sbrac.org/files/build-gnuradio](http://www.sbrac.org/files/build-gnuradio) && chmod a+x ./build-gnuradio && ./build-gnuradio -v
--2015-04-02 12:15:44--  [http://www.sbrac.org/files/build-gnuradio](http://www.sbrac.org/files/build-gnuradio)
Resolving [www.sbrac.org]("http://www.sbrac.org") ([www.sbrac.org]("http://www.sbrac.org"))... 67.212.80.242
Connecting to [www.sbrac.org]("http://www.sbrac.org") ([www.sbrac.org)|67.212.80.242|:80]("http://www.sbrac.org)|67.212.80.242|:80")... connected.
HTTP request sent, awaiting response... 200 OK
Length: 36178 (35K) [text/plain]
Saving to: &#8216;build-gnuradio&#8217;

100%[======================================>] 36,178      28.2KB/s   in 1.3s   

2015-04-02 12:15:48 (28.2 KB/s) - &#8216;build-gnuradio&#8217; saved [36178/36178]

This script will install Gnu Radio from current GIT sources
You will require Internet access from the computer on which this
script runs. You will also require SUDO access. You will require
approximately 500MB of free disk space to perform the build.
 
This script will, as a side-effect, remove any existing Gnu Radio
installation that was installed from your Linux distribution packages.
It must do this to prevent problems due to interference between
a linux-distribution-installed Gnu Radio/UHD and one installed from GIT source.
 
The whole process may take up to two hours to complete, depending on the
capabilities of your system.

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
NOTE: if you run into problems while running this script, you can re-run it with
the --verbose option to produce lots of diagnostic output to help debug problems.
This script has been written to anticipate some of the more common problems one might
encounter building ANY large, complex software package. But it is not pefect, and
there are certainly some situations it could encounter that it cannot deal with
gracefully. Altering the system configuration from something reasonably standard,
removing parts of the filesystem, moving system libraries around arbitrarily, etc,
it likely cannot cope with. It is just a script. It isn't intuitive or artificially
intelligent. It tries to make life a little easier for you, but at the end of the day
if it runs into trouble, a certain amount of knowledge on your part about
system configuration and idiosyncrasies will inevitably be necessary.


Proceed?y
Starting all functions at: Kha Apr 2 12:15:50 MYT 2015
SUDO privileges are required
Do you have SUDO privileges?y
Continuing with script
Installing prerequisites.
====> THIS MAY TAKE QUITE SOME TIME <=====
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libgnuradio-osmosdr0.0.0' for regex 'gnuradio-*'
Note, selecting 'libgnuradio-analog3.7.2.1' for regex 'gnuradio-*'
Note, selecting 'gnuradio' for regex 'gnuradio-*'
Note, selecting 'libgnuradio-comedi3.7.2.1' for regex 'gnuradio-*'
Note, selecting 'libgnuradio-fcdproplus0' for regex 'gnuradio-*'
Note, selecting 'libgnuradio-wavelet3.7.2.1' for regex 'gnuradio-*'
Note, selecting 'libgnuradio-filter3.7.2.1' for regex 'gnuradio-*'
Note, selecting 'libgnuradio-audio3.7.2.1' for regex 'gnuradio-*'
Note, selecting 'libgnuradio-video-sdl3.7.2.1' for regex 'gnuradio-*'
Note, selecting 'libgnuradio-digital3.7.2.1' for regex 'gnuradio-*'
Note, selecting 'libgnuradio-fec3.7.2.1' for regex 'gnuradio-*'
Note, selecting 'libgnuradio-runtime3.7.2.1' for regex 'gnuradio-*'
Note, selecting 'libgnuradio-uhd3.7.2.1' for regex 'gnuradio-*'
Note, selecting 'libgnuradio-wxgui3.7.2.1' for regex 'gnuradio-*'
Note, selecting 'libgnuradio-blocks3.7.2.1' for regex 'gnuradio-*'
Note, selecting 'gnuradio-dev' for regex 'gnuradio-*'
Note, selecting 'libgnuradio-atsc3.7.2.1' for regex 'gnuradio-*'
Note, selecting 'libgnuradio-fft3.7.2.1' for regex 'gnuradio-*'
Note, selecting 'libgnuradio-pmt3.7.2.1' for regex 'gnuradio-*'
Note, selecting 'libgnuradio-channels3.7.2.1' for regex 'gnuradio-*'
Note, selecting 'gnuradio-doc' for regex 'gnuradio-*'
Note, selecting 'libgnuradio-iqbalance0' for regex 'gnuradio-*'
Note, selecting 'libgnuradio-pager3.7.2.1' for regex 'gnuradio-*'
Note, selecting 'libgnuradio-fcd3.7.2.1' for regex 'gnuradio-*'
Note, selecting 'libgnuradio-trellis3.7.2.1' for regex 'gnuradio-*'
Note, selecting 'libgnuradio-noaa3.7.2.1' for regex 'gnuradio-*'
Note, selecting 'libgnuradio-vocoder3.7.2.1' for regex 'gnuradio-*'
Note, selecting 'libgnuradio-qtgui3.7.2.1' for regex 'gnuradio-*'
Package 'gnuradio' is not installed, so not removed
Package 'gnuradio-dev' is not installed, so not removed
Package 'gnuradio-doc' is not installed, so not removed
Package 'libgnuradio-analog3.7.2.1' is not installed, so not removed
Package 'libgnuradio-atsc3.7.2.1' is not installed, so not removed
Package 'libgnuradio-audio3.7.2.1' is not installed, so not removed
Package 'libgnuradio-blocks3.7.2.1' is not installed, so not removed
Package 'libgnuradio-channels3.7.2.1' is not installed, so not removed
Package 'libgnuradio-comedi3.7.2.1' is not installed, so not removed
Package 'libgnuradio-digital3.7.2.1' is not installed, so not removed
Package 'libgnuradio-fcd3.7.2.1' is not installed, so not removed
Package 'libgnuradio-fcdproplus0' is not installed, so not removed
Package 'libgnuradio-fec3.7.2.1' is not installed, so not removed
Package 'libgnuradio-fft3.7.2.1' is not installed, so not removed
Package 'libgnuradio-filter3.7.2.1' is not installed, so not removed
Package 'libgnuradio-iqbalance0' is not installed, so not removed
Package 'libgnuradio-noaa3.7.2.1' is not installed, so not removed
Package 'libgnuradio-osmosdr0.0.0' is not installed, so not removed
Package 'libgnuradio-pager3.7.2.1' is not installed, so not removed
Package 'libgnuradio-pmt3.7.2.1' is not installed, so not removed
Package 'libgnuradio-qtgui3.7.2.1' is not installed, so not removed
Package 'libgnuradio-runtime3.7.2.1' is not installed, so not removed
Package 'libgnuradio-trellis3.7.2.1' is not installed, so not removed
Package 'libgnuradio-uhd3.7.2.1' is not installed, so not removed
Package 'libgnuradio-video-sdl3.7.2.1' is not installed, so not removed
Package 'libgnuradio-vocoder3.7.2.1' is not installed, so not removed
Package 'libgnuradio-wavelet3.7.2.1' is not installed, so not removed
Package 'libgnuradio-wxgui3.7.2.1' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libgruel-*
E: Couldn't find any package by regex 'libgruel-*'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libgruel*
E: Couldn't find any package by regex 'libgruel*'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libgruel0*
E: Couldn't find any package by regex 'libgruel0*'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libgnuradio-osmosdr0.0.0' for regex 'libgnuradio*'
Note, selecting 'libgnuradio-analog3.7.2.1' for regex 'libgnuradio*'
Note, selecting 'libgnuradio-comedi3.7.2.1' for regex 'libgnuradio*'
Note, selecting 'libgnuradio-fcdproplus0' for regex 'libgnuradio*'
Note, selecting 'libgnuradio-wavelet3.7.2.1' for regex 'libgnuradio*'
Note, selecting 'libgnuradio-filter3.7.2.1' for regex 'libgnuradio*'
Note, selecting 'libgnuradio-audio3.7.2.1' for regex 'libgnuradio*'
Note, selecting 'libgnuradio-video-sdl3.7.2.1' for regex 'libgnuradio*'
Note, selecting 'libgnuradio-digital3.7.2.1' for regex 'libgnuradio*'
Note, selecting 'libgnuradio-fec3.7.2.1' for regex 'libgnuradio*'
Note, selecting 'libgnuradio-runtime3.7.2.1' for regex 'libgnuradio*'
Note, selecting 'libgnuradio-uhd3.7.2.1' for regex 'libgnuradio*'
Note, selecting 'libgnuradio-wxgui3.7.2.1' for regex 'libgnuradio*'
Note, selecting 'libgnuradio-blocks3.7.2.1' for regex 'libgnuradio*'
Note, selecting 'libgnuradio-atsc3.7.2.1' for regex 'libgnuradio*'
Note, selecting 'libgnuradio-fft3.7.2.1' for regex 'libgnuradio*'
Note, selecting 'libgnuradio-pmt3.7.2.1' for regex 'libgnuradio*'
Note, selecting 'libgnuradio-channels3.7.2.1' for regex 'libgnuradio*'
Note, selecting 'libgnuradio-iqbalance0' for regex 'libgnuradio*'
Note, selecting 'libgnuradio-pager3.7.2.1' for regex 'libgnuradio*'
Note, selecting 'libgnuradio-fcd3.7.2.1' for regex 'libgnuradio*'
Note, selecting 'libgnuradio-trellis3.7.2.1' for regex 'libgnuradio*'
Note, selecting 'libgnuradio-noaa3.7.2.1' for regex 'libgnuradio*'
Note, selecting 'libgnuradio-vocoder3.7.2.1' for regex 'libgnuradio*'
Note, selecting 'libgnuradio-qtgui3.7.2.1' for regex 'libgnuradio*'
Package 'libgnuradio-analog3.7.2.1' is not installed, so not removed
Package 'libgnuradio-atsc3.7.2.1' is not installed, so not removed
Package 'libgnuradio-audio3.7.2.1' is not installed, so not removed
Package 'libgnuradio-blocks3.7.2.1' is not installed, so not removed
Package 'libgnuradio-channels3.7.2.1' is not installed, so not removed
Package 'libgnuradio-comedi3.7.2.1' is not installed, so not removed
Package 'libgnuradio-digital3.7.2.1' is not installed, so not removed
Package 'libgnuradio-fcd3.7.2.1' is not installed, so not removed
Package 'libgnuradio-fcdproplus0' is not installed, so not removed
Package 'libgnuradio-fec3.7.2.1' is not installed, so not removed
Package 'libgnuradio-fft3.7.2.1' is not installed, so not removed
Package 'libgnuradio-filter3.7.2.1' is not installed, so not removed
Package 'libgnuradio-iqbalance0' is not installed, so not removed
Package 'libgnuradio-noaa3.7.2.1' is not installed, so not removed
Package 'libgnuradio-osmosdr0.0.0' is not installed, so not removed
Package 'libgnuradio-pager3.7.2.1' is not installed, so not removed
Package 'libgnuradio-pmt3.7.2.1' is not installed, so not removed
Package 'libgnuradio-qtgui3.7.2.1' is not installed, so not removed
Package 'libgnuradio-runtime3.7.2.1' is not installed, so not removed
Package 'libgnuradio-trellis3.7.2.1' is not installed, so not removed
Package 'libgnuradio-uhd3.7.2.1' is not installed, so not removed
Package 'libgnuradio-video-sdl3.7.2.1' is not installed, so not removed
Package 'libgnuradio-vocoder3.7.2.1' is not installed, so not removed
Package 'libgnuradio-wavelet3.7.2.1' is not installed, so not removed
Package 'libgnuradio-wxgui3.7.2.1' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package python-gnuradio*
E: Couldn't find any package by regex 'python-gnuradio*'
Checking for package libfontconfig1-dev
Checking for package libxrender-dev
Checking for package libpulse-dev
Checking for package swig
Checking for package g++
Checking for package automake
Checking for package autoconf
Checking for package libtool
Checking for package python-dev
Checking for package libfftw3-dev
Checking for package libcppunit-dev
Checking for package libboost-all-dev
Checking for package libusb-dev
Checking for package libusb-1.0-0-dev
Checking for package fort77
Checking for package libsdl1.2-dev
Checking for package python-wxgtk2.8
Checking for package git-core
Checking for package libqt4-dev
Checking for package python-numpy
Checking for package ccache
Checking for package python-opengl
Checking for package libgsl0-dev
Checking for package python-cheetah
Checking for package python-lxml
Checking for package doxygen
Checking for package qt4-default
Checking for package qt4-dev-tools
Checking for package libusb-1.0-0-dev
Checking for package libqwt5-qt4-dev
Checking for package libqwtplot3d-qt4-dev
Checking for package pyqt4-dev-tools
Checking for package python-qwt5-qt4
Checking for package cmake
Checking for package git-core
Checking for package wget
Checking for package libxi-dev
Checking for package python-docutils
Checking for package gtk2-engines-pixbuf
Checking for package r-base-dev
Checking for package python-tk
Checking for package liborc-0.4-0
Checking for package liborc-0.4-dev
Checking for package libasound2-dev
Checking for package python-gtk2
Checking for package libzmq1
Checking for package libzmq1-dev
Failed to find package 'libzmq1-dev' in known package repositories
Perhaps you need to add the Ubuntu universe or multiverse PPA?
see [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
exiting build

=======================================================================
If you have found this script useful and time-saving, consider a 
donation to help me keep build-gnuradio, simple_ra, SIDsuite,
meteor_detector, simple_fm_rcv, and multimode maintained and up to date.
A simple paypal transfer to [EMAIL="mleech@ripnet.com"]mleech@ripnet.com[/EMAIL] is all you need to do.
======================================================================
Send success/fail info to sbrac.org?n
```

***I already try sudo apt-get install libzmq -dev.
What can I do? I hope you can help me.

---

### Post by sandyd on 2015-04-02
Its a typo

Script should be installing libzmq-dev

Try doing this:
Open the script in gedit, replace the following bolded line
```

			PKGLIST="libfontconfig1-dev libxrender-dev libpulse-dev swig g++
			automake autoconf libtool python-dev libfftw3-dev
			libcppunit-dev libboost-all-dev libusb-dev libusb-1.0-0-dev fort77
			libsdl1.2-dev python-wxgtk2.8 git-core
			libqt4-dev python-numpy ccache python-opengl libgsl0-dev
			python-cheetah python-lxml doxygen qt4-default qt4-dev-tools libusb-1.0-0-dev
			libqwt5-qt4-dev libqwtplot3d-qt4-dev pyqt4-dev-tools python-qwt5-qt4
			cmake git-core wget libxi-dev python-docutils gtk2-engines-pixbuf r-base-dev python-tk
**			liborc-0.4-0 liborc-0.4-dev libasound2-dev python-gtk2 libzmq1 libzmq1-dev"**
			CMAKE_FLAG1=-DPythonLibs_FIND_VERSION:STRING="2.7"
			CMAKE_FLAG2=-DPythonInterp_FIND_VERSION:STRING="2.7"
			;;
```
with
```

			liborc-0.4-0 liborc-0.4-dev libasound2-dev python-gtk2 libzmq1 libzmq-dev"

```

---

### Post by raihana on 2015-04-02
Sorry, it was typo. sudo apt-get install libzmq-dev. What can I do? I hope you can help me.

---

### Post by sandyd on 2015-04-02
> **raihana said:**
> Sorry, it was typo. sudo apt-get install libzmq-dev. What can I do? I hope you can help me.

Download the file
```

wget http://www.sbrac.org/files/build-gnuradio
gedit build-gnuradio
```
Edit the file as specified in post #2, save and run
```

chmod a+x ./build-gnuradio && ./build-gnuradio -v
```

---

### Post by tedy58 on 2015-04-02
First I want to thanks to sandyd. 
Definitely I could say that the patch of the script made by  sandyd in post#2 work good. 

1. I use the script for building gnuradio from [here]("http://www.sbrac.org/files/build-gnuradio");
2. I Save the script as  build-gnuradio.sh;
2. Then I edit the saved script in directory like in the post#2;
```
$~/src/gnuradio/build-gnuradio.sh 
```
3. Finally I use:```

$chmod a+x  build-gnuradio.sh
$./build-gnuradio.sh && ./build-gnuradio.sh -v
```
and all is OK now.

---

### Post by akengineering on 2016-01-17
> **sandyd said:**
> Its a typo

Script should be installing libzmq-dev

Try doing this:
Open the script in gedit, replace the following bolded line
```

            PKGLIST="libfontconfig1-dev libxrender-dev libpulse-dev swig g++
            automake autoconf libtool python-dev libfftw3-dev
            libcppunit-dev libboost-all-dev libusb-dev libusb-1.0-0-dev fort77
            libsdl1.2-dev python-wxgtk2.8 git-core
            libqt4-dev python-numpy ccache python-opengl libgsl0-dev
            python-cheetah python-lxml doxygen qt4-default qt4-dev-tools libusb-1.0-0-dev
            libqwt5-qt4-dev libqwtplot3d-qt4-dev pyqt4-dev-tools python-qwt5-qt4
            cmake git-core wget libxi-dev python-docutils gtk2-engines-pixbuf r-base-dev python-tk
**            liborc-0.4-0 liborc-0.4-dev libasound2-dev python-gtk2 libzmq1 libzmq1-dev"**
            CMAKE_FLAG1=-DPythonLibs_FIND_VERSION:STRING="2.7"
            CMAKE_FLAG2=-DPythonInterp_FIND_VERSION:STRING="2.7"
            ;;
```
with
```

            liborc-0.4-0 liborc-0.4-dev libasound2-dev python-gtk2 libzmq1 libzmq-dev"

```
:
:I followed your instructions - and the file does not contain the code you called a typo... for uBuntu 15. the line says: liborc-0.4-0 liborc-0.4-dev libasound2-dev python-gtk2 libzmq libzmq-dev libzmq1 libzmq1-dev python-requests python-sphinx comedi-dev python-zmq"
: The file libzmq1 is present - the file libzmq1-dev is not

---

### Post by mc4man on 2016-01-19
> **akengineering said:**
> :
:I followed your instructions - and the file does not contain the code you called a typo... for uBuntu 15. the line says: liborc-0.4-0 liborc-0.4-dev libasound2-dev python-gtk2 libzmq libzmq-dev libzmq1 libzmq1-dev python-requests python-sphinx comedi-dev python-zmq"
: The file libzmq1 is present - the file libzmq1-dev is not
That's because the script was altered since last postings, still wrong but because they did include the 1 package needed the script should just go along it's merry way.

red don't exist, blue is possibly not needed in script, black is the one definitely needed in the script

[COLOR="#FF0000"]libzmq[/COLOR] [COLOR="#000000"]libzmq-dev[/COLOR] [COLOR="#0000FF"]libzmq1[/COLOR] [COLOR="#FF0000"]libzmq1-dev[/COLOR]

---

