---
title: "Compiling with reference to libboost-sys-dev"
date: 2011-12-27
forum: Packaging and Compiling Programs
---

### Post by jago25_98 on 2011-12-27
I want to compile [tortunnel]("http://www.thoughtcrime.org/software/tortunnel/"), a light client for tor.

This needs libboost. 

```
Network.o: In function `get_system_category':
/usr/include/boost/asio/error.hpp:220: undefined reference to `boost::system::system_category()'
Network.o: In function `error_code':
/usr/include/boost/system/error_code.hpp:315: undefined reference to `boost::system::system_category()'
/usr/include/boost/system/error_code.hpp:315: undefined reference to `boost::system::system_category()'
Network.o: In function `get_system_category':
/usr/include/boost/asio/error.hpp:220: undefined reference to `boost::system::system_category()'
Network.o:/usr/include/boost/asio/error.hpp:220: more undefined references to `boost::system::system_category()' follow
Network.o: In function `__static_initialization_and_destruction_0':
/usr/include/boost/system/error_code.hpp:214: undefined reference to `boost::system::generic_category()'
/usr/include/boost/system/error_code.hpp:215: undefined reference to `boost::system::generic_category()'
/usr/include/boost/system/error_code.hpp:216: undefined reference to `boost::system::system_category()'
Network.o: In function `get_system_category':
/usr/include/boost/asio/error.hpp:220: undefined reference to `boost::system::system_category()'
CreatedCell.o: In function `CreatedCell::isValid()':
/home/j/Downloads/tt/tortunnel/protocol/CreatedCell.cpp:45: undefined reference to `BN_num_bits'
CreatedCell.o: In function `CreatedCell::getKeyMaterial(unsigned char**, unsigned char**)':
/home/j/Downloads/tt/tortunnel/protocol/CreatedCell.cpp:49: undefined reference to `BN_num_bits'
/home/j/Downloads/tt/tortunnel/protocol/CreatedCell.cpp:49: undefined reference to `BN_bin2bn'
/home/j/Downloads/tt/tortunnel/protocol/CreatedCell.cpp:50: undefined reference to `DH_size'
/home/j/Downloads/tt/tortunnel/protocol/CreatedCell.cpp:51: undefined reference to `DH_compute_key'
/home/j/Downloads/tt/tortunnel/protocol/CreatedCell.cpp:52: undefined reference to `BN_num_bits'
/home/j/Downloads/tt/tortunnel/protocol/CreatedCell.cpp:54: undefined reference to `BN_free'
collect2: ld returned 1 exit status
make: *** [torproxy] Error 1

```

There are plenty of mentions of this:

[http://ubuntuforums.org/showthread.php?t=1392264](http://ubuntuforums.org/showthread.php?t=1392264)

But I don't really understand the programmer speak:
[http://vladimir_prus.blogspot.com/2009/06/linking-101.html](http://vladimir_prus.blogspot.com/2009/06/linking-101.html)

[http://ubuntuforums.org/showthread.php?t=1657777](http://ubuntuforums.org/showthread.php?t=1657777)

Here's what I have installed:
```
sudo apt-get install libboost*
[sudo] password for j: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libboost-program-options1.46.1' for regex 'libboost*'
Note, selecting 'libboost-iostreams1.46.1' for regex 'libboost*'
Note, selecting 'libboost-serialization1.46.1' for regex 'libboost*'
Note, selecting 'libboost1.46-dev' for regex 'libboost*'
Note, selecting 'libboost-graph1.46-dev' for regex 'libboost*'
Note, selecting 'libboost-dev' for regex 'libboost*'
Note, selecting 'libboost-python1.46.1' for regex 'libboost*'
Note, selecting 'libboost-dbg' for regex 'libboost*'
Note, selecting 'libboost1.46-dbg' for regex 'libboost*'
Note, selecting 'libboost-doc' for regex 'libboost*'
Note, selecting 'libboost1.46-doc' for regex 'libboost*'
Note, selecting 'libboost-serialization1.46-dev' for regex 'libboost*'
Note, selecting 'libboost-test1.46-dev' for regex 'libboost*'
Note, selecting 'libboost-graph1.46.1' for regex 'libboost*'
Note, selecting 'libboost-graph1.42-dev' for regex 'libboost*'
Note, selecting 'libboost-regex1.46.1' for regex 'libboost*'
Note, selecting 'libboost-iostreams-dev' for regex 'libboost*'
Note, selecting 'libboost-iostreams1.46-dev' for regex 'libboost*'
Note, selecting 'libboost-regex1.46-dev' for regex 'libboost*'
Note, selecting 'libboost-iostreams1.42-dev' for regex 'libboost*'
Note, selecting 'libboost-program-options1.46-dev' for regex 'libboost*'
Note, selecting 'libboost-program-options1.42-dev' for regex 'libboost*'
Note, selecting 'libboost-python-dev' for regex 'libboost*'
Note, selecting 'libboost-python1.46-dev' for regex 'libboost*'
Note, selecting 'libboost-python1.42-dev' for regex 'libboost*'
Note, selecting 'libboost-regex1.42-dev' for regex 'libboost*'
Note, selecting 'libboost-serialization-dev' for regex 'libboost*'
Note, selecting 'libboost-serialization1.42-dev' for regex 'libboost*'
Note, selecting 'libboost-test-dev' for regex 'libboost*'
Note, selecting 'libboost-test1.46.1' for regex 'libboost*'
Note, selecting 'libboost-test1.42-dev' for regex 'libboost*'
Note, selecting 'libboost1.42-dbg' for regex 'libboost*'
Note, selecting 'libboost-date-time1.46-dev' for regex 'libboost*'
Note, selecting 'libboost-filesystem1.46-dev' for regex 'libboost*'
Note, selecting 'libboost-math1.46-dev' for regex 'libboost*'
Note, selecting 'libboost-random1.46-dev' for regex 'libboost*'
Note, selecting 'libboost-signals1.46-dev' for regex 'libboost*'
Note, selecting 'libboost-system1.46-dev' for regex 'libboost*'
Note, selecting 'libboost-thread1.46-dev' for regex 'libboost*'
Note, selecting 'libboost-wave1.46-dev' for regex 'libboost*'
Note, selecting 'libboost1.42-dev' for regex 'libboost*'
Note, selecting 'libboost1.42-doc' for regex 'libboost*'
Note, selecting 'libboost-python1.35-dev' for regex 'libboost*'
Note, selecting 'libboost1.35-dbg' for regex 'libboost*'
Note, selecting 'libboost-date-time1.46.1' for regex 'libboost*'
Note, selecting 'libboost-system1.46.1' for regex 'libboost*'
Note, selecting 'libboost-thread1.46.1' for regex 'libboost*'
Note, selecting 'libboost-filesystem1.46.1' for regex 'libboost*'
Note, selecting 'libboost-wave1.46.1' for regex 'libboost*'
Note, selecting 'libboost-date-time-dev' for regex 'libboost*'
Note, selecting 'libboost-filesystem-dev' for regex 'libboost*'
Note, selecting 'libboost-program-options-dev' for regex 'libboost*'
Note, selecting 'libboost-regex-dev' for regex 'libboost*'
Note, selecting 'libboost-thread-dev' for regex 'libboost*'
Note, selecting 'libboost-signals1.46.1' for regex 'libboost*'
Note, selecting 'libboost-mpi1.46.1' for regex 'libboost*'
Note, selecting 'libboost-all-dev' for regex 'libboost*'
Note, selecting 'libboost-graph-dev' for regex 'libboost*'
Note, selecting 'libboost-graph-parallel-dev' for regex 'libboost*'
Note, selecting 'libboost-math-dev' for regex 'libboost*'
Note, selecting 'libboost-mpi-dev' for regex 'libboost*'
Note, selecting 'libboost-mpi-python-dev' for regex 'libboost*'
Note, selecting 'libboost-signals-dev' for regex 'libboost*'
Note, selecting 'libboost-system-dev' for regex 'libboost*'
Note, selecting 'libboost-wave-dev' for regex 'libboost*'
Note, selecting 'libboost-date-time1.42-dev' for regex 'libboost*'
Note, selecting 'libboost-date-time1.42.0' for regex 'libboost*'
Note, selecting 'libboost-date-time1.36-dev' for regex 'libboost*'
Note, selecting 'libboost-date-time1.37-dev' for regex 'libboost*'
Note, selecting 'libboost-date-time1.38-dev' for regex 'libboost*'
Note, selecting 'libboost-date-time1.39-dev' for regex 'libboost*'
Note, selecting 'libboost-date-time1.40-dev' for regex 'libboost*'
Note, selecting 'libboost-date-time1.41-dev' for regex 'libboost*'
Note, selecting 'libboost-filesystem1.42-dev' for regex 'libboost*'
Note, selecting 'libboost-filesystem1.42.0' for regex 'libboost*'
Note, selecting 'libboost-system1.42-dev' for regex 'libboost*'
Note, selecting 'libboost-filesystem1.35-dev' for regex 'libboost*'
Note, selecting 'libboost-filesystem1.36-dev' for regex 'libboost*'
Note, selecting 'libboost-filesystem1.37-dev' for regex 'libboost*'
Note, selecting 'libboost-filesystem1.38-dev' for regex 'libboost*'
Note, selecting 'libboost-filesystem1.39-dev' for regex 'libboost*'
Note, selecting 'libboost-filesystem1.40-dev' for regex 'libboost*'
Note, selecting 'libboost-filesystem1.41-dev' for regex 'libboost*'
Note, selecting 'libboost-system1.42.0' for regex 'libboost*'
Note, selecting 'libboost-graph-parallel1.46-dev' for regex 'libboost*'
Note, selecting 'libboost-graph-parallel1.46.1' for regex 'libboost*'
Note, selecting 'libboost-graph-parallel1.42-dev' for regex 'libboost*'
Note, selecting 'libboost-graph1.42.0' for regex 'libboost*'
Note, selecting 'libboost-graph1.35-dev' for regex 'libboost*'
Note, selecting 'libboost-graph1.36-dev' for regex 'libboost*'
Note, selecting 'libboost-graph1.37-dev' for regex 'libboost*'
Note, selecting 'libboost-graph1.38-dev' for regex 'libboost*'
Note, selecting 'libboost-graph1.39-dev' for regex 'libboost*'
Note, selecting 'libboost-graph1.40-dev' for regex 'libboost*'
Note, selecting 'libboost-graph1.41-dev' for regex 'libboost*'
Note, selecting 'libboost-regex1.42.0' for regex 'libboost*'
Note, selecting 'libboost-iostreams1.42.0' for regex 'libboost*'
Note, selecting 'libboost-iostreams1.35-dev' for regex 'libboost*'
Note, selecting 'libboost-iostreams1.36-dev' for regex 'libboost*'
Note, selecting 'libboost-iostreams1.37-dev' for regex 'libboost*'
Note, selecting 'libboost-iostreams1.38-dev' for regex 'libboost*'
Note, selecting 'libboost-iostreams1.39-dev' for regex 'libboost*'
Note, selecting 'libboost-iostreams1.40-dev' for regex 'libboost*'
Note, selecting 'libboost-iostreams1.41-dev' for regex 'libboost*'
Note, selecting 'libboost-math1.42-dev' for regex 'libboost*'
Note, selecting 'libboost-math1.42.0' for regex 'libboost*'
Note, selecting 'libboost-math1.40-dev' for regex 'libboost*'
Note, selecting 'libboost-math1.41-dev' for regex 'libboost*'
Note, selecting 'libboost-math1.46.1' for regex 'libboost*'
Note, selecting 'libboost-mpi1.46-dev' for regex 'libboost*'
Note, selecting 'libboost-mpi-python1.46-dev' for regex 'libboost*'
Note, selecting 'libboost-mpi-python1.46.1' for regex 'libboost*'
Note, selecting 'libboost-mpi-python1.42-dev' for regex 'libboost*'
Note, selecting 'libboost-mpi-python1.40.0' for regex 'libboost*'
Note, selecting 'libboost-mpi-python1.41.0' for regex 'libboost*'
Note, selecting 'libboost-mpi-python1.42.0' for regex 'libboost*'
Note, selecting 'libboost-mpi-python1.46.0' for regex 'libboost*'
Note, selecting 'libboost-mpi1.42-dev' for regex 'libboost*'
Note, selecting 'libboost-program-options1.42.0' for regex 'libboost*'
Note, selecting 'libboost-program-options1.35-dev' for regex 'libboost*'
Note, selecting 'libboost-program-options1.36-dev' for regex 'libboost*'
Note, selecting 'libboost-program-options1.37-dev' for regex 'libboost*'
Note, selecting 'libboost-program-options1.38-dev' for regex 'libboost*'
Note, selecting 'libboost-program-options1.39-dev' for regex 'libboost*'
Note, selecting 'libboost-program-options1.40-dev' for regex 'libboost*'
Note, selecting 'libboost-program-options1.41-dev' for regex 'libboost*'
Note, selecting 'libboost-python1.42.0' for regex 'libboost*'
Note, selecting 'libboost-python1.36-dev' for regex 'libboost*'
Note, selecting 'libboost-python1.37-dev' for regex 'libboost*'
Note, selecting 'libboost-python1.38-dev' for regex 'libboost*'
Note, selecting 'libboost-python1.39-dev' for regex 'libboost*'
Note, selecting 'libboost-python1.40-dev' for regex 'libboost*'
Note, selecting 'libboost-python1.41-dev' for regex 'libboost*'
Note, selecting 'libboost-random-dev' for regex 'libboost*'
Note, selecting 'libboost-random1.46.1' for regex 'libboost*'
Note, selecting 'libboost-regex1.35-dev' for regex 'libboost*'
Note, selecting 'libboost-regex1.36-dev' for regex 'libboost*'
Note, selecting 'libboost-regex1.37-dev' for regex 'libboost*'
Note, selecting 'libboost-regex1.38-dev' for regex 'libboost*'
Note, selecting 'libboost-regex1.39-dev' for regex 'libboost*'
Note, selecting 'libboost-regex1.40-dev' for regex 'libboost*'
Note, selecting 'libboost-regex1.41-dev' for regex 'libboost*'
Note, selecting 'libboost-serialization1.42.0' for regex 'libboost*'
Note, selecting 'libboost-serialization1.35-dev' for regex 'libboost*'
Note, selecting 'libboost-serialization1.36-dev' for regex 'libboost*'
Note, selecting 'libboost-serialization1.37-dev' for regex 'libboost*'
Note, selecting 'libboost-serialization1.38-dev' for regex 'libboost*'
Note, selecting 'libboost-serialization1.39-dev' for regex 'libboost*'
Note, selecting 'libboost-serialization1.40-dev' for regex 'libboost*'
Note, selecting 'libboost-serialization1.41-dev' for regex 'libboost*'
Note, selecting 'libboost-signals1.42-dev' for regex 'libboost*'
Note, selecting 'libboost-signals1.42.0' for regex 'libboost*'
Note, selecting 'libboost-signals1.35-dev' for regex 'libboost*'
Note, selecting 'libboost-signals1.36-dev' for regex 'libboost*'
Note, selecting 'libboost-signals1.37-dev' for regex 'libboost*'
Note, selecting 'libboost-signals1.38-dev' for regex 'libboost*'
Note, selecting 'libboost-signals1.39-dev' for regex 'libboost*'
Note, selecting 'libboost-signals1.40-dev' for regex 'libboost*'
Note, selecting 'libboost-signals1.41-dev' for regex 'libboost*'
Note, selecting 'libboost-system1.38-dev' for regex 'libboost*'
Note, selecting 'libboost-system1.39-dev' for regex 'libboost*'
Note, selecting 'libboost-system1.40-dev' for regex 'libboost*'
Note, selecting 'libboost-system1.41-dev' for regex 'libboost*'
Note, selecting 'libboost-test1.42.0' for regex 'libboost*'
Note, selecting 'libboost-test1.35-dev' for regex 'libboost*'
Note, selecting 'libboost-test1.36-dev' for regex 'libboost*'
Note, selecting 'libboost-test1.37-dev' for regex 'libboost*'
Note, selecting 'libboost-test1.38-dev' for regex 'libboost*'
Note, selecting 'libboost-test1.39-dev' for regex 'libboost*'
Note, selecting 'libboost-test1.40-dev' for regex 'libboost*'
Note, selecting 'libboost-test1.41-dev' for regex 'libboost*'
Note, selecting 'libboost-thread1.42-dev' for regex 'libboost*'
Note, selecting 'libboost-thread1.42.0' for regex 'libboost*'
Note, selecting 'libboost-thread1.35-dev' for regex 'libboost*'
Note, selecting 'libboost-thread1.36-dev' for regex 'libboost*'
Note, selecting 'libboost-thread1.37-dev' for regex 'libboost*'
Note, selecting 'libboost-thread1.38-dev' for regex 'libboost*'
Note, selecting 'libboost-thread1.39-dev' for regex 'libboost*'
Note, selecting 'libboost-thread1.40-dev' for regex 'libboost*'
Note, selecting 'libboost-thread1.41-dev' for regex 'libboost*'
Note, selecting 'libboost-wave1.42-dev' for regex 'libboost*'
Note, selecting 'libboost-wave1.42.0' for regex 'libboost*'
Note, selecting 'libboost-wave1.35-dev' for regex 'libboost*'
Note, selecting 'libboost-wave1.36-dev' for regex 'libboost*'
Note, selecting 'libboost-wave1.37-dev' for regex 'libboost*'
Note, selecting 'libboost-wave1.38-dev' for regex 'libboost*'
Note, selecting 'libboost-wave1.39-dev' for regex 'libboost*'
Note, selecting 'libboost-wave1.40-dev' for regex 'libboost*'
Note, selecting 'libboost-wave1.41-dev' for regex 'libboost*'
Note, selecting 'libboost1.42-all-dev' for regex 'libboost*'
Note, selecting 'libboost1.36-dbg' for regex 'libboost*'
Note, selecting 'libboost1.37-dbg' for regex 'libboost*'
Note, selecting 'libboost1.38-dbg' for regex 'libboost*'
Note, selecting 'libboost1.39-dbg' for regex 'libboost*'
Note, selecting 'libboost1.40-dbg' for regex 'libboost*'
Note, selecting 'libboost1.41-dbg' for regex 'libboost*'
Note, selecting 'libboost1.35-dev' for regex 'libboost*'
Note, selecting 'libboost1.36-dev' for regex 'libboost*'
Note, selecting 'libboost1.37-dev' for regex 'libboost*'
Note, selecting 'libboost1.38-dev' for regex 'libboost*'
Note, selecting 'libboost1.39-dev' for regex 'libboost*'
Note, selecting 'libboost1.40-dev' for regex 'libboost*'
Note, selecting 'libboost1.41-dev' for regex 'libboost*'
Note, selecting 'libboost1.35-doc' for regex 'libboost*'
Note, selecting 'libboost1.36-doc' for regex 'libboost*'
Note, selecting 'libboost1.37-doc' for regex 'libboost*'
Note, selecting 'libboost1.38-doc' for regex 'libboost*'
Note, selecting 'libboost1.39-doc' for regex 'libboost*'
Note, selecting 'libboost1.40-doc' for regex 'libboost*'
Note, selecting 'libboost1.41-doc' for regex 'libboost*'
Note, selecting 'libboost1.46-all-dev' for regex 'libboost*'
Note, selecting 'libboost-program-options1.40.0' for regex 'libboost*'
Note, selecting 'libboost-thread1.34.1' for regex 'libboost*'
Note, selecting 'libboost-system1.40.0' for regex 'libboost*'
Note, selecting 'libboost-python1.34.1' for regex 'libboost*'
Note, selecting 'libboost-filesystem1.40.0' for regex 'libboost*'
Note, selecting 'libboost-regex1.34.1' for regex 'libboost*'
Note, selecting 'libboost-program-options1.34.1' for regex 'libboost*'
Note, selecting 'libboost-regex1.40.0' for regex 'libboost*'
libboost-iostreams1.46.1 is already the newest version.
libboost-iostreams1.46.1 set to manually installed.
libboost-program-options1.46.1 is already the newest version.
libboost-program-options1.46.1 set to manually installed.
libboost-regex1.46.1 is already the newest version.
libboost-regex1.46.1 set to manually installed.
libboost-serialization1.46.1 is already the newest version.
libboost-serialization1.46.1 set to manually installed.
libboost1.46-dev is already the newest version.
libboost1.46-dev set to manually installed.
libboost-filesystem1.46.1 is already the newest version.
libboost-filesystem1.46.1 set to manually installed.
libboost-signals1.46.1 is already the newest version.
libboost-signals1.46.1 set to manually installed.
libboost-system1.46-dev is already the newest version.
libboost-system1.46.1 is already the newest version.
libboost-system1.46.1 set to manually installed.
libboost-thread1.42.0 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 libboost-date-time1.46-dev : Conflicts: libboost-date-time1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-filesystem1.46-dev : Conflicts: libboost-filesystem1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-graph1.46-dev : Conflicts: libboost-graph1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-iostreams1.46-dev : Conflicts: libboost-iostreams1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-math1.46-dev : Conflicts: libboost-math1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-program-options1.46-dev : Conflicts: libboost-program-options1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-python1.46-dev : Conflicts: libboost-python1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-regex1.46-dev : Conflicts: libboost-regex1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-serialization1.46-dev : Conflicts: libboost-serialization1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-signals1.46-dev : Conflicts: libboost-signals1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-system1.46-dev : Conflicts: libboost-system1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-test1.46-dev : Conflicts: libboost-test1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-thread1.46-dev : Conflicts: libboost-thread1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-wave1.46-dev : Conflicts: libboost-wave1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost1.46-dbg : Conflicts: libboost1.42-dbg but 1.42.0-4ubuntu2 is to be installed
 libboost1.46-dev : Conflicts: libboost1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost1.46-doc : Conflicts: libboost1.42-doc but 1.42.0-4ubuntu2 is to be installed
E: Unable to correct problems, you have held broken packages.
j@laptop:~/Downloads/tt/tortunnel$ 

```

Do I need to edit the makefile to point manually to the right lib somehow? Perhaps ./configure has not detected it properly?

---

### Post by Bobhuber on 2011-12-27
sudo apt-get install libboost-system-dev

---

### Post by jago25_98 on 2011-12-27
> **Bobhuber said:**
> sudo apt-get install libboost-system-dev

Thanks, had indeed missed that one! 

But still the error (did a make clean and re-ran ./configure just in case):

```
Network.o: In function `error_code':
/usr/include/boost/system/error_code.hpp:315: undefined reference to `boost::system::system_category()'
Network.o: In function `get_system_category':
/usr/include/boost/asio/error.hpp:220: undefined reference to `boost::system::system_category()'
Network.o: In function `error_code':
/usr/include/boost/system/error_code.hpp:315: undefined reference to `boost::system::system_category()'
/usr/include/boost/system/error_code.hpp:315: undefined reference to `boost::system::system_category()'
Network.o: In function `get_system_category':
/usr/include/boost/asio/error.hpp:220: undefined reference to `boost::system::system_category()'
Network.o:/usr/include/boost/asio/error.hpp:220: more undefined references to `boost::system::system_category()' follow
Network.o: In function `__static_initialization_and_destruction_0':
/usr/include/boost/system/error_code.hpp:214: undefined reference to `boost::system::generic_category()'
/usr/include/boost/system/error_code.hpp:215: undefined reference to `boost::system::generic_category()'
/usr/include/boost/system/error_code.hpp:216: undefined reference to `boost::system::system_category()'
Network.o: In function `get_system_category':
/usr/include/boost/asio/error.hpp:220: undefined reference to `boost::system::system_category()'
CreatedCell.o: In function `CreatedCell::isValid()':
/home/j/Downloads/tt/tortunnel/protocol/CreatedCell.cpp:45: undefined reference to `BN_num_bits'
CreatedCell.o: In function `CreatedCell::getKeyMaterial(unsigned char**, unsigned char**)':
/home/j/Downloads/tt/tortunnel/protocol/CreatedCell.cpp:49: undefined reference to `BN_num_bits'
/home/j/Downloads/tt/tortunnel/protocol/CreatedCell.cpp:49: undefined reference to `BN_bin2bn'
/home/j/Downloads/tt/tortunnel/protocol/CreatedCell.cpp:50: undefined reference to `DH_size'
/home/j/Downloads/tt/tortunnel/protocol/CreatedCell.cpp:51: undefined reference to `DH_compute_key'
/home/j/Downloads/tt/tortunnel/protocol/CreatedCell.cpp:52: undefined reference to `BN_num_bits'
/home/j/Downloads/tt/tortunnel/protocol/CreatedCell.cpp:54: undefined reference to `BN_free'
collect2: ld returned 1 exit status
make: *** [torproxy] Error 1

```

---

### Post by oldos2er on 2011-12-27
Moved to Packaging and Compiling Programs.

---

### Post by jago25_98 on 2011-12-28
I'll switch to Sabyaron eventually but until then is there a way to pay for help with this question?

---

### Post by MadCow108 on 2011-12-28
the buildsystem of that program is broken.

apply this patch with patch -p1 <patchfile
then run autoreconf
then build as usual (configure && make)

```
--- tortunnel-0.3/Makefile.am	2011-09-20 04:06:11.000000000 +0200
+++ tortunnel-0.3/Makefile.am	2011-12-28 20:07:57.622783852 +0100
@@ -6,8 +6,10 @@
 torproxy_SOURCES = TorProxy.cpp TorProxy.h ShuffleStream.h protocol/RelayCellDispatcher.h protocol/HybridEncryption.h protocol/HybridEncryption.cpp protocol/Connection.cpp protocol/Connection.h protocol/Cell.cpp protocol/Cell.h protocol/Directory.cpp protocol/Directory.h protocol/RelayDataCell.h protocol/CreatedCell.h protocol/RelayCell.h protocol/RelayEndCell.h protocol/RelaySendMeCell.h protocol/ServerListing.cpp protocol/ServerListing.h util/Util.cpp protocol/Circuit.cpp protocol/Circuit.h protocol/CellEncrypter.cpp protocol/CellEncrypter.h protocol/RelayBeginCell.h protocol/CellListener.h protocol/RelayCellDispatcher.cpp protocol/CellConsumer.cpp protocol/CellConsumer.h ProxyShuffler.cpp protocol/CreateCell.cpp protocol/CreateCell.h protocol/CreatedCell.cpp TorTunnel.cpp TorTunnel.h SocksConnection.cpp SocksConnection.h util/Network.cpp ProxyShuffler.h util/Network.h util/Util.h
 
 
-torproxy_LDFLAGS = -lssl -lboost_system-mt
+torproxy_LDFLAGS = -pthread
+torproxy_LDADD = -lssl -lboost_system-mt -lcrypto
 
 torscanner_SOURCES = TorScanner.cpp TorScanner.h ShuffleStream.h protocol/RelayCellDispatcher.h protocol/HybridEncryption.h protocol/HybridEncryption.cpp protocol/Connection.cpp protocol/Connection.h protocol/Cell.cpp protocol/Cell.h protocol/Directory.cpp protocol/Directory.h protocol/RelayDataCell.h protocol/CreatedCell.h protocol/RelayCell.h protocol/RelayEndCell.h protocol/RelaySendMeCell.h protocol/ServerListing.cpp protocol/ServerListing.h util/Util.cpp protocol/Circuit.cpp protocol/Circuit.h protocol/CellEncrypter.cpp protocol/CellEncrypter.h protocol/RelayBeginCell.h protocol/CellListener.h protocol/RelayCellDispatcher.cpp protocol/CellConsumer.cpp protocol/CellConsumer.h ProxyShuffler.cpp protocol/CreateCell.cpp protocol/CreateCell.h protocol/CreatedCell.cpp TorTunnel.cpp TorTunnel.h util/Network.cpp protocol/ServerListingGroup.cpp protocol/ServerListingGroup.h util/Network.h util/Util.h
 
-torscanner_LDFLAGS = -lssl -lboost_system-mt
+torscanner_LDFLAGS = -pthread
+torscanner_LDADD = -lssl -lboost_system-mt -lcrypto

```

---

### Post by jago25_98 on 2011-12-29
Thanks. Had to apt-get install libtool as well... now something else... 

```
j@laptop:~/Downloads/tortunnel-0.3$ autoreconf 
j@laptop:~/Downloads/tortunnel-0.3$ ./configure 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking whether the C compiler works... myes
checking for C compiler default output file name... a.out
checking for suffix of executables... a
checking whether we are cross compiling... kno
checking for suffix of object files... o
checking whether we are using the GNU C compiler... eyes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... 
none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
configure: creating ./config.status
config.status: creating Makefile
config.status: executing depfiles commands
j@laptop:~/Downloads/tortunnel-0.3$ make
g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE_URL=\"\" -DPACKAGE=\"tortunnel\" -DVERSION=\"0.3\" -I.    -ggdb -g -O2 -MT TorProxy.o -MD -MP -MF .deps/TorProxy.Tpo -c -o TorProxy.o TorProxy.cpp
In file included from TorTunnel.h:42:0,
                 from TorProxy.h:40,
                 from TorProxy.cpp:30:
protocol/Directory.h:74:3: error: ‘list’ in namespace ‘std’ does not name a type
make: *** [TorProxy.o] Error 1
j@laptop:~/Downloads/tortunnel-0.3$ 
```

---

### Post by MadCow108 on 2011-12-29
open protocol/Directory.h and add an #include <list> near the top.

---

