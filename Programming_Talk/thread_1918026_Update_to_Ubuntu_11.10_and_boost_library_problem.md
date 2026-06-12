---
title: "Update to Ubuntu 11.10 and boost library problem"
date: 2012-01-31
forum: Programming Talk
---

### Post by erotavlas on 2012-01-31
Hi,

I was using with success the boost library with Ubuntu 11.04. Now, after the updated (cursed) to latest version of Ubuntu, the boost library is updated from version 1.42 to version 1.46. I can find the library in the correct path /usr/lib/*.* but when I try to compile I get the linker error:
```

g++ -m64 -std=gnu++0x -pg    -l:libboost_filesystem.so.1.46.1 -o sim node.o: In function `__static_initialization_and_destruction_0':
/usr/include/boost/system/error_code.hpp:214: undefined reference to `boost::system::generic_category()'
/usr/include/boost/system/error_code.hpp:215: undefined reference to `boost::system::generic_category()'
/usr/include/boost/system/error_code.hpp:216: undefined reference to `boost::system::system_category()'
build/Debug/GNU-Linux-x86/_ext/1076063616/node.o: In function `boost::filesystem3::path::codecvt()':
/usr/include/boost/filesystem/v3/path.hpp:377: undefined reference to `boost::filesystem3::path::wchar_t_codecvt_facet()'
build/Debug/GNU-Linux-x86/_ext/1076063616/node.o: In function `boost::filesystem3::create_directories(boost::filesystem3::path const&)':
/usr/include/boost/filesystem/v3/operations.hpp:318: undefined reference to `boost::filesystem3::detail::create_directories(boost::filesystem3::path const&, boost::system::error_code*)'
build/Debug/GNU-Linux-x86/_ext/867083813/simulator.o: In function `__static_initialization_and_destruction_0':
/usr/include/boost/system/error_code.hpp:214: undefined reference to `boost::system::generic_category()'
/usr/include/boost/system/error_code.hpp:215: undefined reference to `boost::system::generic_category()'
/usr/include/boost/system/error_code.hpp:216: undefined reference to `boost::system::system_category()'
build/Debug/GNU-Linux-x86/_ext/1076063616/cascade.o: In function `__static_initialization_and_destruction_0':
/usr/include/boost/system/error_code.hpp:214: undefined reference to `boost::system::generic_category()'
/usr/include/boost/system/error_code.hpp:215: undefined reference to `boost::system::generic_category()'
/usr/include/boost/system/error_code.hpp:216: undefined reference to `boost::system::system_category()'

```Where could be the problem? I have also tried to change from -l:libboost_filesystem.so.1.46.1 to -lboost_filesystem without success.

Thank you

---

### Post by Zugzwang on 2012-01-31
> **erotavlas said:**
> 
Where could be the problem? I have also tried to change from -l:libboost_filesystem.so.1.46.1 to -lboost_filesystem without success.


You should use the latter. After a library upgrade, make sure to rebuild the whole project, typically ensured by either removing all .o files manually or running "make clean" whenever applicable (the latter should be preferred as it is simpler). Also, make sure that "-lboost_filesystem" occurs *after* the reference to node.o in the compilation command, as the order of arguments is important. I've read here somewhere that this has recently changed...

---

### Post by erotavlas on 2012-01-31
> **Zugzwang said:**
> You should use the latter. After a library upgrade, make sure to rebuild the whole project, typically ensured by either removing all .o files manually or running "make clean" whenever applicable (the latter should be preferred as it is simpler). Also, make sure that "-lboost_filesystem" occurs *after* the reference to node.o in the compilation command, as the order of arguments is important. I've read here somewhere that this has recently changed...

I have tried to use both but the result is the same while with Ubuntu 11.04 with both worked well. The Ubuntu 11.10 has the new version 1.46.1 of the library and I have to install it with the command apt-get install libboost1.46-all-dev while in the Ubuntu 11.04 with apt-get install libboost*.
In the Ubuntu 11.10 if I try to install libboost* I get the following messages.

```

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
libboost-graph1.46-dev is already the newest version.
libboost-graph1.46-dev set to manually installed.
libboost-graph1.46.1 is already the newest version.
libboost-graph1.46.1 set to manually installed.
libboost-iostreams1.46-dev is already the newest version.
libboost-iostreams1.46-dev set to manually installed.
libboost-iostreams1.46.1 is already the newest version.
libboost-iostreams1.46.1 set to manually installed.
libboost-program-options1.46-dev is already the newest version.
libboost-program-options1.46-dev set to manually installed.
libboost-program-options1.46.1 is already the newest version.
libboost-program-options1.46.1 set to manually installed.
libboost-python1.46-dev is already the newest version.
libboost-python1.46-dev set to manually installed.
libboost-python1.46.1 is already the newest version.
libboost-python1.46.1 set to manually installed.
libboost-regex1.46-dev is already the newest version.
libboost-regex1.46-dev set to manually installed.
libboost-regex1.46.1 is already the newest version.
libboost-regex1.46.1 set to manually installed.
libboost-serialization1.46-dev is already the newest version.
libboost-serialization1.46-dev set to manually installed.
libboost-serialization1.46.1 is already the newest version.
libboost-test1.46-dev is already the newest version.
libboost-test1.46-dev set to manually installed.
libboost-test1.46.1 is already the newest version.
libboost-test1.46.1 set to manually installed.
libboost1.46-dev is already the newest version.
libboost1.46-dev set to manually installed.
libboost-date-time1.46-dev is already the newest version.
libboost-date-time1.46-dev set to manually installed.
libboost-date-time1.46.1 is already the newest version.
libboost-date-time1.46.1 set to manually installed.
libboost-filesystem1.46-dev is already the newest version.
libboost-filesystem1.46-dev set to manually installed.
libboost-filesystem1.46.1 is already the newest version.
libboost-filesystem1.46.1 set to manually installed.
libboost-graph-parallel1.46-dev is already the newest version.
libboost-graph-parallel1.46-dev set to manually installed.
libboost-graph-parallel1.46.1 is already the newest version.
libboost-graph-parallel1.46.1 set to manually installed.
libboost-math1.46-dev is already the newest version.
libboost-math1.46-dev set to manually installed.
libboost-math1.46.1 is already the newest version.
libboost-math1.46.1 set to manually installed.
libboost-mpi-python1.46-dev is already the newest version.
libboost-mpi-python1.46-dev set to manually installed.
libboost-mpi-python1.46.1 is already the newest version.
libboost-mpi-python1.46.1 set to manually installed.
libboost-mpi1.46-dev is already the newest version.
libboost-mpi1.46-dev set to manually installed.
libboost-mpi1.46.1 is already the newest version.
libboost-mpi1.46.1 set to manually installed.
libboost-random1.46-dev is already the newest version.
libboost-random1.46-dev set to manually installed.
libboost-random1.46.1 is already the newest version.
libboost-random1.46.1 set to manually installed.
libboost-signals1.46-dev is already the newest version.
libboost-signals1.46-dev set to manually installed.
libboost-signals1.46.1 is already the newest version.
libboost-signals1.46.1 set to manually installed.
libboost-system1.46-dev is already the newest version.
libboost-system1.46-dev set to manually installed.
libboost-system1.46.1 is already the newest version.
libboost-system1.46.1 set to manually installed.
libboost-thread1.46-dev is already the newest version.
libboost-thread1.46-dev set to manually installed.
libboost-thread1.46.1 is already the newest version.
libboost-thread1.46.1 set to manually installed.
libboost-wave1.46-dev is already the newest version.
libboost-wave1.46-dev set to manually installed.
libboost-wave1.46.1 is already the newest version.
libboost-wave1.46.1 set to manually installed.
libboost1.46-all-dev is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
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

```

---

### Post by Zugzwang on 2012-01-31
> **erotavlas said:**
> I have tried to use both but the result is the same while with Ubuntu 11.04 with both worked well. The Ubuntu 11.10 has the new version 1.46.1 of the library and I have to install it with the command apt-get install libboost1.46-all-dev while in the Ubuntu 11.04 with apt-get install libboost*.
In the Ubuntu 11.10 if I try to install libboost* I get the following messages.


What about the possible ways to solve your problems that I've posted. Did they work? These were:
[LIST]
[*]After a library upgrade, make sure to rebuild the whole project, typically ensured by either removing all .o files manually or running "make clean" whenever applicable (the latter should be preferred as it is simpler).
[*] Also, make sure that "-lboost_filesystem" occurs *after* the reference to node.o in the compilation command, as the order of arguments is important.
[/LIST]

---

### Post by erotavlas on 2012-01-31
> **Zugzwang said:**
> What about the possible ways to solve your problems that I've posted. Did they work? These were:
[LIST]
[*]After a library upgrade, make sure to rebuild the whole project, typically ensured by either removing all .o files manually or running "make clean" whenever applicable (the latter should be preferred as it is simpler).
[*] Also, make sure that "-lboost_filesystem" occurs *after* the reference to node.o in the compilation command, as the order of arguments is important.
[/LIST]


Yes, I have followed your suggestions but without success.

---

### Post by Zugzwang on 2012-01-31
Ok, then try adding -lboost_system as well. It might be that this is only needed in newer boost versions. 

Make sure that the linking command actually used looks like this, regardless of the fact that this didn't fix any problems previously.

g++ -m64 -std=gnu++0x -pg -o sim node.o -lboost_filesystem -lboost_system

In any case, the order of the libraries is important - they must come *after* node.o, and boost_system must come *after* boost_filesystem. Also, don't use the version number of boost in the file name to link against.

Finally, check that there is no locally installed boost version in /usr/local that you accidentally try to link against.

---

### Post by erotavlas on 2012-01-31
> **Zugzwang said:**
> Ok, then try adding -lboost_system as well. It might be that this is only needed in newer boost versions. 

Make sure that the linking command actually used looks like this, regardless of the fact that this didn't fix any problems previously.

g++ -m64 -std=gnu++0x -pg -o sim node.o -lboost_filesystem -lboost_system

In any case, the order of the libraries is important - they must come *after* node.o, and boost_system must come *after* boost_filesystem. Also, don't use the version number of boost in the file name to link against.

Finally, check that there is no locally installed boost version in /usr/local that you accidentally try to link against.

Hi,

with your suggestion I can compile a dummy program but if try to compile my program, Netbeans puts the -lboost_filesystem -lboost_system options before the -o option and so it does not work. Do you know how can I change the options order in Netbeans 7.1? Thank you

---

### Post by gateway67 on 2012-01-31
> **erotavlas said:**
> Hi,

with your suggestion I can compile a dummy program but if try to compile my program, Netbeans puts the -lboost_filesystem -lboost_system options before the -o option and so it does not work. Do you know how can I change the options order in Netbeans 7.1? Thank you


Sigh...  try this...


1.  Right-click on Project Name.

2.  Select Properties

3.  Select Build -> Linker from Categories

4.  Select "..." button associated with Libraries (near lower right side of dialog box)

5.  From pop-up dialog, select Add Library...

6.  Navigate to /usr/lib

7.  Select libboost_system.so

8.  Repeat Step 7, but for libboost_filesystem.so

9.  Select Ok, Ok, etc... to close all dialog boxes

10.  Rebuild your project.

---

### Post by erotavlas on 2012-02-01
> **gateway67 said:**
> Sigh...  try this...


1.  Right-click on Project Name.

2.  Select Properties

3.  Select Build -> Linker from Categories

4.  Select "..." button associated with Libraries (near lower right side of dialog box)

5.  From pop-up dialog, select Add Library...

6.  Navigate to /usr/lib

7.  Select libboost_system.so

8.  Repeat Step 7, but for libboost_filesystem.so

9.  Select Ok, Ok, etc... to close all dialog boxes

10.  Rebuild your project.

Yes this is a "official" procedure to add a library to a project while I have used the additional options field. Unfortunately using your suggestions the result does not change and I get the same linking error.

---

### Post by Zugzwang on 2012-02-01
> **erotavlas said:**
> Yes this is a "official" procedure to add a library to a project while I have used the additional options field. Unfortunately using your suggestions the result does not change and I get the same linking error.

Interesting. Please copy&paste the updated full result of the compilation process (including the g++ command that Netbeans used for linking) and the error here. At least the one with the undefined reference to "boost::filesystem3::path::wchar_t_codecvt_facet" should have gone away. 

This will help up to find the cause of the problem.

---

### Post by erotavlas on 2012-02-01
> **Zugzwang said:**
> Interesting. Please copy&paste the updated full result of the compilation process (including the g++ command that Netbeans used for linking) and the error here. At least the one with the undefined reference to "boost::filesystem3::path::wchar_t_codecvt_facet" should have gone away. 

This will help up to find the cause of the problem.

This is the output of Netbeans...

```

g++ -m64 -std=gnu++0x -pg -pedantic    -o dist/Debug/GNU-Linux-x86/sim 
build/Debug/GNU-Linux-x86/_ext/1076063616/node.o: In function `__static_initialization_and_destruction_0':
/usr/include/boost/system/error_code.hpp:214: undefined reference to `boost::system::generic_category()'
/usr/include/boost/system/error_code.hpp:215: undefined reference to `boost::system::generic_category()'
/usr/include/boost/system/error_code.hpp:216: undefined reference to `boost::system::system_category()'
build/Debug/GNU-Linux-x86/_ext/1076063616/node.o: In function `boost::filesystem3::path::codecvt()':
/usr/include/boost/filesystem/v3/path.hpp:377: undefined reference to `boost::filesystem3::path::wchar_t_codecvt_facet()'
build/Debug/GNU-Linux-x86/_ext/1076063616/node.o: In function `boost::filesystem3::create_directories(boost::filesystem3::path const&)':
/usr/include/boost/filesystem/v3/operations.hpp:318: undefined reference to `boost::filesystem3::detail::create_directories(boost::filesystem3::path const&, boost::system::error_code*)'
build/Debug/GNU-Linux-x86/_ext/867083813/simulator.o: In function `__static_initialization_and_destruction_0':
/usr/include/boost/system/error_code.hpp:214: undefined reference to `boost::system::generic_category()'
/usr/include/boost/system/error_code.hpp:215: undefined reference to `boost::system::generic_category()'
/usr/include/boost/system/error_code.hpp:216: undefined reference to `boost::system::system_category()'
build/Debug/GNU-Linux-x86/_ext/1076063616/cascade.o: In function `__static_initialization_and_destruction_0':
/usr/include/boost/system/error_code.hpp:214: undefined reference to `boost::system::generic_category()'
/usr/include/boost/system/error_code.hpp:215: undefined reference to `boost::system::generic_category()'
/usr/include/boost/system/error_code.hpp:216: undefined reference to `boost::system::system_category()'
collect2: ld returned 1 exit status
make[2]: *** [dist/Debug/GNU-Linux-x86/sim] Error 1
make[2]: Leaving directory `/home/project'
make[1]: *** [.build-conf] Error 2
make[1]: Leaving directory `/home/project'
make: *** [.build-impl] Error 2

```

---

### Post by Zugzwang on 2012-02-02
The problem is that in your Netbeans output, there is no sign that the libraries to link against are given as parameter to the linker. Apparently, the linker is called as follows:

```

g++ -m64 -std=gnu++0x -pg -pedantic    -o dist/Debug/GNU-Linux-x86/sim 
build/Debug/GNU-Linux-x86/_ext/1076063616/node.o

```

As we wrote, there should be a "-lboost_filesystem -lboost_system" appended to the command. You will need to convince Netbeans to do so.

---

### Post by erotavlas on 2012-02-02
> **Zugzwang said:**
> The problem is that in your Netbeans output, there is no sign that the libraries to link against are given as parameter to the linker. Apparently, the linker is called as follows:

```

g++ -m64 -std=gnu++0x -pg -pedantic    -o dist/Debug/GNU-Linux-x86/sim 
build/Debug/GNU-Linux-x86/_ext/1076063616/node.o

```As we wrote, there should be a "-lboost_filesystem -lboost_system" appended to the command. You will need to convince Netbeans to do so.


Thank you. I have solved putting the link to library in both places (as library and additional options), I don't know why...

---

### Post by turboscrew on 2012-02-10
I have similar errors.

Does this ("stripped") have something to do with it?

```
ubuntu:/usr/lib$ file *Poco*
libPocoCryptod.so:      broken symbolic link to `libPocoCryptod.so.9'
libPocoCrypto.so:       symbolic link to `libPocoCrypto.so.9'
libPocoCrypto.so.9:     ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped
libPocoDatad.so:        broken symbolic link to `libPocoDatad.so.9'
libPocoData.so:         symbolic link to `libPocoData.so.9'
libPocoData.so.9:       ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped
libPocoFoundationd.so:  broken symbolic link to `libPocoFoundationd.so.9'
libPocoFoundation.so:   symbolic link to `libPocoFoundation.so.9'
libPocoFoundation.so.9: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped

```

[edit]

Also:

ubuntu:/usr/lib$ nm libPocoNet.so.9
nm: libPocoNet.so.9: no symbols

---

### Post by turboscrew on 2012-02-10
Ahh...
Poco only has shared libraries, and the switch "-shared" was missing...

---

### Post by jiggersplat on 2012-10-31
I'm having a similar problem using cmake.  It should be linking against boost_system and boost_thread which are both in /usr/lib and boost headers are in /usr/include

```
Linking CXX executable ../../../bin/navigation
cd /home/dan/workspace/tewm/src/nodes/navigation && /usr/bin/cmake -E cmake_link_script CMakeFiles/navigation-bin.dir/link.txt --verbose=1
/usr/bin/c++   -g    CMakeFiles/navigation-bin.dir/main.cpp.o CMakeFiles/navigation-bin.dir/navigationnode.cpp.o  -o ../../../bin/navigation -rdynamic -L/home/dan/workspace/tewm/lib -lpthread -lzmq -lprotobuf -lboost_system -lboost_thread-mt ../../../lib/libtewmproto.a -lregistry -llogger -lzmq -lprotobuf ../../../lib/libtewmproto.a -Wl,-rpath,/home/dan/workspace/tewm/lib 
/home/dan/workspace/tewm/lib/liblogger.a(logger.cpp.o): In function `__static_initialization_and_destruction_0':
/usr/include/boost/system/error_code.hpp:214: undefined reference to `boost::system::generic_category()'
/usr/include/boost/system/error_code.hpp:215: undefined reference to `boost::system::generic_category()'
/usr/include/boost/system/error_code.hpp:216: undefined reference to `boost::system::system_category()'
/home/dan/workspace/tewm/lib/liblogger.a(logger.cpp.o): In function `void boost::this_thread::sleep<boost::date_time::subsecond_duration<boost::posix_time::time_duration, 1000l> >(boost::date_time::subsecond_duration<boost::posix_time::time_duration, 1000l> const&)':
/usr/include/boost/thread/pthread/thread_data.hpp:200: undefined reference to `boost::this_thread::sleep(boost::posix_time::ptime const&)'
collect2: ld returned 1 exit status
```

---

