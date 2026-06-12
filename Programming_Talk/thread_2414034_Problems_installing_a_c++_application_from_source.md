---
title: "Problems installing a c++ application from source"
date: 2019-03-05
forum: Programming Talk
---

### Post by fred63 on 2019-03-05
greetings, I hope I have the right forum: edit: now that I have posted this I can see it probably should have gone in the subforum  [Packaging and Compiling Programs]("https://ubuntuforums.org/forumdisplay.php?f=44")

I am running Ubuntu Mate 18.04.2 LTS.

I am trying to install from source the program scid_vs_pc, which can be found here:  [http://scidvspc.sourceforge.net/](http://scidvspc.sourceforge.net/)

This is the first time I have tried installing from source

here are the installation instructions for the program;

```
4.0.1.  Linux , Unix


  Scid vs. PC requires Wish (Tcl/Tk) 8.5 or later (though 8.5.10 has
  nasty bugs and should be avoided), and a C++ compiler .
  Example packages required include "tcl, tk, tcl-devel, tk-devel" and
  "gcc-c++ , libstdc++"; but of course will vary with your distribution.


  The default installation directory is /usr/local, which is generally
  empty, but any version of Scid here will be overwritten. To install
  into /usr (for eg) use ./configure BINDIR=/usr/bin/
  SHAREDIR=/usr/share/scid/


  Installing from source:


  ______________________________________________________________________
  tar -xzf scid_vs_pc-4.19.tgz
  cd scid_vs_pc-4.19
  ./configure
  sudo make install
  scid
  ______________________________________________________________________


```
Here is the output from ./configure

```
fredh@fwh:~/chess/scid_vs_pc-4.19$ ./configure
Scid vs. PC configure - Makefile configuration program
    Renaming "Makefile" to "Makefile.bak"
    Tcl/Tk version: 8.6
    Your operating system is: Linux 4.18.0-15-generic
      NAME="Ubuntu"
VERSION="18.04.2 LTS (Bionic Beaver)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 18.04.2 LTS"
VERSION_ID="18.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=bionic
UBUNTU_CODENAME=bionic
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu 18.04.2 LTS"
    Location of "tcl.h": not found
    Location of "tk.h": not found
    Location of Tcl 8.6 library: /usr/lib/x86_64-linux-gnu
    Location of Tk 8.6 library: not found
    Location of X11 library: /usr/lib/x86_64-linux-gnu
    Checking if your system already has zlib installed: no.


Not all settings could be determined! See above for details.


The default Makefile was written.
You will need to edit it before you can compile Scid.

```
according to Synaptic, the following packages are installed:

```
tcl version 8.6.0+9
g++ version 4:7.3  dependency package

```
I'm not sure where to go from here. please advise.

---

### Post by webaake on 2019-03-05
As a general rule of thumb when compiling, the needed files and packages are so called development files (*.dev). They can be found in the Ubuntu repos and installed from there (99.9% anyway).

For example tcl ; the dev file that seems appropriate for your case should be "tcl8.6-dev" . Read the output of the configure command and look for the corresponding "dev files" install all needed dependencies and try to configure make again. (and again until all dependencies are met)

If you haven't already I recommend installing Synaptic package manager. (sudo apt install synaptic). It's one of the traditional Ubuntu package managers - and one of the best. Easy to do searches in and easy to add repos.

PS It's hard for programmers (source managers) to know which packages are installed in which distros and what they're called. So sometimes their install instructions for your distro/version aren't 100%. But by using intuition and dev files it usually works. Might need coffee......

---

### Post by fred63 on 2019-03-05
Thanks. By installing the dev files  tcl.dev and tk.dev, I was able to get the program installed and up and running

---

### Post by brunoeduardo-cc on 2019-04-11
use the following commands

sudo apt-get install tcl8.5-dev
sudo apt-get install tcl8.4-dev
sudo apt-get install tclx8.4-dev
sudo apt-get install tclcl-dev

---

