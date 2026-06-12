---
title: "CMake Error: The following variables are used in this project, but they are set to NO"
date: 2015-03-16
forum: New to Ubuntu
---

### Post by nur3 on 2015-03-16
.Building UHD...
=============> THIS WILL TAKE SOME TIME <=============

-- 
-- Configuring the python interpreter...
-- Python interpreter: /usr/bin/python2.7
-- Override with: -DPYTHON_EXECUTABLE=<path-to-python>
-- Using UHD Images Directory: OFF
-- Build type not specified: defaulting to release.
-- 
-- Configuring Boost C++ Libraries...
-- Could NOT find Boost
-- Boost include directories: Boost_INCLUDE_DIR-NOTFOUND
-- Boost library directories: 
-- Boost libraries: 
-- 
-- Python checking for Python version 2.6 or greater
-- Python checking for Python version 2.6 or greater - found
-- 
-- Python checking for Cheetah templates 2.0.0 or greater
-- Python checking for Cheetah templates 2.0.0 or greater - "import Cheetah" failed
-- 
-- Configuring LibUHD support...
--   Dependency Boost_FOUND = 0
--   Dependency HAVE_PYTHON_PLAT_MIN_VERSION = TRUE
--   Dependency HAVE_PYTHON_MODULE_CHEETAH = FALSE
--   Disabling LibUHD support.
--   Override with -DENABLE_LIBUHD=ON/OFF
-- 
-- Configuring Examples support...
--   Dependency ENABLE_LIBUHD = OFF
--   Disabling Examples support.
--   Override with -DENABLE_EXAMPLES=ON/OFF
-- 
-- Configuring Utils support...
--   Dependency ENABLE_LIBUHD = OFF
--   Disabling Utils support.
--   Override with -DENABLE_UTILS=ON/OFF
-- 
-- Configuring Tests support...
--   Dependency ENABLE_LIBUHD = OFF
--   Disabling Tests support.
--   Override with -DENABLE_TESTS=ON/OFF
-- Could NOT find Doxygen (missing:  DOXYGEN_EXECUTABLE) 
-- 
-- 
-- Configuring Manual support...
--   Dependency DOXYGEN_FOUND = NO
--   Disabling Manual support.
--   Override with -DENABLE_MANUAL=ON/OFF
-- 
-- 
-- Configuring API/Doxygen support...
--   Dependency DOXYGEN_FOUND = NO
--   Disabling API/Doxygen support.
--   Override with -DENABLE_DOXYGEN=ON/OFF
-- 
-- 
-- 
-- Configuring Man Pages support...
--   Dependency GZIP_FOUND = TRUE
--   Dependency NOT_WIN32 = TRUE
--   Enabling Man Pages support.
--   Override with -DENABLE_MAN_PAGES=ON/OFF
-- libs: dl;pthread;boost_date_time;boost_filesystem;boost_program_options;boost_regex;boost_system;boost_thread;boost_serialization
-- 
-- ######################################################
-- # UHD enabled components                              
-- ######################################################
--   * Man Pages
-- 
-- ######################################################
-- # UHD disabled components                             
-- ######################################################
--   * LibUHD
--   * Examples
--   * Utils
--   * Tests
--   * Manual
--   * API/Doxygen
-- 
-- Building version: 003.008.002-124-g306b5243
-- Using install prefix: /usr/local
CMake Error: The following variables are used in this project, but they are set to NOTFOUND.
Please set them or make sure they are set and tested correctly in the CMake files:
Boost_INCLUDE_DIR (ADVANCED)
   used as include directory in directory /home/userr/uhd/host
   used as include directory in directory /home/userr/uhd/host/docs

-- Configuring incomplete, errors occurred!
See also "/home/userr/uhd/host/build/CMakeFiles/CMakeOutput.log".
See also "/home/userr/uhd/host/build/CMakeFiles/CMakeError.log".
make: *** No rule to make target `clean'.  Stop.
make: *** No targets specified and no makefile found.  Stop.
UHD build apparently failed
Exiting UHD build

=======================================================================
If you have found this script useful and time-saving, consider a 
donation to help me keep build-gnuradio, simple_ra, SIDsuite,
meteor_detector, simple_fm_rcv, and multimode maintained and up to date.
A simple paypal transfer to [email]mleech@ripnet.com[/email] is all you need to do.
======================================================================
Send success/fail info to sbrac.org?n
:(

---

### Post by nur3 on 2015-03-16
[FONT=arial]i am use ubuntu 14.04 LTS. as i am installing gnuradio from this link:
[http://gnuradio.org/redmine/projects/gnuradio/wiki/InstallingGRFromSource](http://gnuradio.org/redmine/projects/gnuradio/wiki/InstallingGRFromSource)
[/FONT]
[FONT=arial](which install gnuradio &uhd) choose build from source
then i try ./build-gnuradio -v uhd_build
[/FONT]

---

### Post by Holger_Gehrke on 2015-03-16
Obviously the script doesn't download three of the dependencies of the program you're trying to build.
[LIST]
[*]the library Boost and it's headers (sudo apt-get install libboost-dev) 
[*]the Cheetah template engine / code generator for python (sudo apt-get install python-cheetah) 
[*]and the API-Documentation generator doxygen (sudo apt-get install doxygen) 
[/LIST]
Install these and try again.

---

### Post by nur3 on 2015-03-17
thanks holger_gehrke.

---

### Post by nur3 on 2015-03-17
UHD build/install apparently failed since I cannot find /usr/local/bin/uhd_find_devices
after doing make and make install
Exiting UHD build

what can i do?

---

### Post by Holger_Gehrke on 2015-03-17
The configuration script probably cached some of the decisions it made when the needed libraries were not available, among them the decision not to compile the utilities. Try calling the script with the option '--help' to find out if it has an option to erase or override this cache.  Or you can look for the file in which the script saved these decisions and erase it. It's probably a text file, it might be hidden (name beginning with a '.') and it was created after the download but before the compilation.

---

### Post by nur3 on 2015-03-17
userr@userr-Aspire-4755:~$ sudo --list
Matching Defaults entries for userr on userr-Aspire-4755:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin, timestamp_timeout=90

User userr may run the following commands on userr-Aspire-4755:
    (ALL : ALL) NOPASSWD: ALL
userr@userr-Aspire-4755:~$

---

