---
title: "CURL not found. CMAKE not compiling."
date: 2014-05-04
forum: Packaging and Compiling Programs
---

### Post by DidierDrigbi on 2014-05-04
Hi.
**UBUNTU 14.04 Thrusty Tahr**
Today I experienced problem with CURL, while trying to install Doomsday emulator.
I prepared the folders:
> 
cd ~
mkdir doomsday
cd doomsday/
mkdir wad
mkdir jdoom

Then I downloaded the new Doomsday engine:

> wget -c [http://mesh.dl.sourceforge.net/sourceforge/deng/deng-1.9.0-beta6.9.tar.gz](http://mesh.dl.sourceforge.net/sourceforge/deng/deng-1.9.0-beta6.9.tar.gz)
tar -xzvf deng-1.9.0-beta6.9.tar.gz
cd deng-1.9.0-beta6.9/
cd doomsday/build/


I installed mandatory dependencies:
> 
sudo apt-get install cmake libsdl-mixer1.2 libsdl-dev libsdl-mixer1.2-dev libsdl-net1.2 libsdl-net1.2-dev

And here comes the problem. When I try to cmake the build, I get the error, that neither CURL nor CURSES are found.

> jasiek@step207:~/doomsday/deng-1.9.0-beta6.9/doomsday/build$ cmake ../
-- CURL was not found. Make sure CURL_LIBRARY and CURL_INCLUDE_DIR are set.
CMake Error at /usr/share/cmake-2.8/Modules/FindPackageHandleStandardArgs.cmake:108 (message):
  Could NOT find Curses (missing: CURSES_LIBRARY CURSES_INCLUDE_PATH)
Call Stack (most recent call first):
  /usr/share/cmake-2.8/Modules/FindPackageHandleStandardArgs.cmake:315 (_FPHSA_FAILURE_MESSAGE)
  /usr/share/cmake-2.8/Modules/FindCurses.cmake:159 (FIND_PACKAGE_HANDLE_STANDARD_ARGS)
  CMakeLists.txt:248 (FIND_PACKAGE)


-- Configuring incomplete, errors occurred!
See also "/home/jasiek/doomsday/deng-1.9.0-beta6.9/doomsday/build/CMakeFiles/CMakeOutput.log".
See also "/home/jasiek/doomsday/deng-1.9.0-beta6.9/doomsday/build/CMakeFiles/CMakeError.log".


I can't solve it, so i can't move to the next step, *make* command, as it is not ready. Does anyone know how to get rid of this problem?

---

### Post by Ubi_one_2014 on 2014-05-04
apt-get install curl ??

---

### Post by DidierDrigbi on 2014-05-04
Of course it is installed, as synaptic and command line say so.

---

### Post by Ubi_one_2014 on 2014-05-04
[http://stackoverflow.com/questions/4678926/cmake-cant-find-curses](http://stackoverflow.com/questions/4678926/cmake-cant-find-curses)

---

### Post by oldos2er on 2014-05-04
Moved to Packaging & Compiling Programs.

---

### Post by steeldriver on 2014-05-04
You don't just need curl, you need the appropriate curl development libraries + header files package - probably **libcurl4-gnutls-dev**

> **DidierDrigbi said:**
> Of course it is installed, as synaptic and command line say so.

Similarly for ncurses, it's likely **libncurses5-dev** (and possibly libncurses**w**5-dev) that you need

---

