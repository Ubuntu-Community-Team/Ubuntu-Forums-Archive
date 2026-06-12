---
title: "How to build Kftpgrabber from SVN? Problems encountered"
date: 2009-07-07
forum: Packaging and Compiling Programs
---

### Post by Colt45 on 2009-07-07
The main domain for Kftpgrabber ([www.kftp.org](www.kftp.org)) appears to have lapsed recently or possibly the project was terminated?

The most recent source and SVN still appears to be hosted by KDE.org
[http://websvn.kde.org/trunk/extragear/network/kftpgrabber/](http://websvn.kde.org/trunk/extragear/network/kftpgrabber/)

Following the directions retrieved below I attempted to build from SVN
[http://web.archive.org/web/20071019034550/www.kftp.org/misc/svn](http://web.archive.org/web/20071019034550/www.kftp.org/misc/svn)

-------------------------------------------------------------------------------------------------------
svn co -N svn://anonsvn.kde.org/home/kde/trunk/extragear/network
cd network
svn up kftpgrabber
svn co svn://anonsvn.kde.org/home/kde/branches/KDE/3.5/kde-common/admin
make -f Makefile.cvs
./configure --prefix=`kde-config --prefix` --enable-debug=full
make
su -c "make install"
-------------------------------------------------------------------------------------------------------

The first four lines go off without a hitch. However, when I type in "make -f Makefile.cvs"

I receive this error.

###@******:~/network$ make -f Makefile.cvs
make: Makefile.cvs: No such file or directory
make: *** No rule to make target `Makefile.cvs'. Stop.

Could someone please list how to properly compile Kftpgrabber from SVN from start to finish?

Thanks

---

### Post by Colt45 on 2009-07-09
Ok, well after a very long amount of research it turns out I can answer my own question.

In short, the SVN build instructions were outdated and no longer accurate..
Here's are the steps I went through to build the latest kftpgrabber from SVN.

Checkinstall substituted for "make install" so you can create a package and have an entry in Synaptic
for easy removal

If you want the latest KDE4 version, the instructions would be:
===========================================================================================

1. Install kdelibs5-dev
   sudo apt-get install kdelibs5-dev

2. Install cmake
   sudo apt-get install cmake

3. Install libssh2-1 and libssh2-dev
   sudo apt-get install libssh2-1
   sudo apt-get install libssh2-dev

4. Create a txt file, name it FindLibSSH2.cmake

5. Open FindLibSSH2.cmake with a text editor

6. Paste the following text

###########################################################################################
#
# kftpgrabber-svn needs FindLibSSH2 cmake module, so if you don't have that module,
# add this file in /usr/share/cmake-2.6/Modules
#
# - Try to find the libssh2 library
# Once done this will define
#
# LIBSSH2_FOUND - system has the libssh2 library
# LIBSSH2_INCLUDE_DIR - the libssh2 include directory
# LIBSSH2_LIBRARY - the libssh2 library name

if (LIBSSH2_INCLUDE_DIR AND LIBSSH2_LIBRARY)
set(LibSSH2_FIND_QUIETLY TRUE)
endif (LIBSSH2_INCLUDE_DIR AND LIBSSH2_LIBRARY)

FIND_PATH(LIBSSH2_INCLUDE_DIR libssh2.h)

FIND_LIBRARY(LIBSSH2_LIBRARY NAMES ssh2)

include(FindPackageHandleStandardArgs)
FIND_PACKAGE_HANDLE_STANDARD_ARGS(LibSSH2 DEFAULT_MSG LIBSSH2_INCLUDE_DIR LIBSSH2_LIBRARY)

MARK_AS_ADVANCED(LIBSSH2_INCLUDE_DIR LIBSSH2_LIBRARY)

###########################################################################################

7. Save FindLibSSH2.cmake and exit the text editor

8. Copy FindLibSSH2.cmake to /usr/share/cmake-2.6/Modules

9. Download & Compile

svn co svn://anonsvn.kde.org/home/kde/trunk/extragear/network/kftpgrabber
mkdir kftpgrabber-build
cd kftpgrabber-build
cmake ../kftpgrabber
make
sudo checkinstall

10. Change owner info
   press 1
   youruser@youruser

11. NOTE: !! You must change build information !!
   press 3
   0.8.99

12. success!! cookies for everyone.

---

