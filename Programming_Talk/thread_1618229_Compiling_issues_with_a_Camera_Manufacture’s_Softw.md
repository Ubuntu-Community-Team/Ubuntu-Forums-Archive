---
title: "Compiling issues with a Camera Manufacture’s Software"
date: 2010-11-10
forum: Programming Talk
---

### Post by primary_solution on 2010-11-10
Hi,

I am working on a project and I am trying to compile a set of sample  applications from a camera manufacture on Ubuntu version 10.10.

I have followed the README file which is embedded in the package at the following link:
[ftp://Pylon4Linux-ro:h50UZgkl@ftp.baslerweb.com]("ftp://Pylon4Linux-ro:h50UZgkl@ftp.baslerweb.com/") 

The instruction say to create a 'pylon' directory in /opt directory.   Then extract the package to this directory.  Finally, there is several  environment variables that need to be set.  I ran 'env' command in a  terminal and the environment variables were set.  LD_LIBRARY_PATH  variable I set in the /etc/bash.bashrc file.  Then verified it was set  in the terminal and it was.

According to the manufacture, to avoid issues where a user wanted to use  pylon (the camera and it's software) on a Linux distribution that  wasn't formally supported, they included a C++ compiler with all the  necessary libs to compile.  It is located in a sub directory of the  pylon directory I previously mentioned.  However, when I run the 'make'  command in this sub-directory I get a ton of errors that the compiler  can not find a bunch of include files like iostream, vector, exception,  etc.

Listed below is the list of errors I get when I run the 'make' command.

[HTML]
ian@testcptr:/opt/pylon/PylonSamples$ make
for d in AcquireContinuous AcquireContinuous_SoftTrigger AcquireSingleFrame AcquireSingleFrame_ChunkImage AcquireSingleFrame_Gen CameraEvents LookupTable ManyCamerasUnix ParametrizeCamera RegisterRemovalCallback UserSets WaitEx; do make -C $d \
        GENICAM_ROOT_V1_1="/opt/pylon" \
        PYLON_ROOT="/opt/pylon" \
        CXX="/opt/pylon/gcc-4.2.1/build/bin/g++ " \
        LD="/opt/pylon/gcc-4.2.1/build/bin/g++ " \
        CPPFLAGS="-I/opt/pylon/gcc-4.2.1/build/gcc-4.2.1/include/c++/4.2.1 -I/opt/pylon/include -I/opt/pylon/include/genicam -I/opt/pylon/include -DUSE_GIGE" \
        CXXFLAGS="" \
        LDFLAGS="-L/opt/pylon/lib -L/opt/pylon/lib-L/opt/pylon/gcc-4.2.1/build/lib -Wl,-E" \
        all; done
make[1]: Entering directory `/opt/pylon/PylonSamples/AcquireContinuous'
/opt/pylon/gcc-4.2.1/build/bin/g++  -I/opt/pylon/gcc-4.2.1/build/gcc-4.2.1/include/c++/4.2.1 -I/opt/pylon/include -I/opt/pylon/include/genicam -I/opt/pylon/include -DUSE_GIGE  -c -o AcquireContinuous.o AcquireContinuous.cpp
In file included from /opt/pylon/include/pylon/PylonIncludes.h:22,
                 from AcquireContinuous.cpp:6:
/opt/pylon/include/genicam/Base/GCString.h:34:18: error: string: No such file or directory
/opt/pylon/include/genicam/Base/GCString.h:36:20: error: iostream: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:23,
                 from AcquireContinuous.cpp:6:
/opt/pylon/include/genicam/Base/GCStringVector.h:186:18: error: vector: No such file or directory
In file included from /opt/pylon/include/genicam/Base/GCBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireContinuous.cpp:6:
/opt/pylon/include/genicam/Base/GCException.h:42:21: error: exception: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:43:19: error: cassert: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:44:19: error: cstdarg: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:45:19: error: sstream: No such file or directory
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:40,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireContinuous.cpp:6:
/opt/pylon/include/genicam/GenApi/Persistence.h:37:16: error: list: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:61,
                 from AcquireContinuous.cpp:6:
/opt/pylon/include/pylon/Device.h:27:18: error: bitset: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:22,
                 from AcquireContinuous.cpp:6:
/opt/pylon/include/genicam/Base/GCString.h:107: error: ISO C++ forbids declaration of ‘string’ with no type
/opt/pylon/include/genicam/Base/GCString.h:107: error: invalid use of ‘::’
/opt/pylon/include/genicam/Base/GCString.h:107: error: expected ‘;’ before ‘*’ token
/opt/pylon/include/genicam/Base/GCString.h:116: error: expected constructor, destructor, or type conversion before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:118: error: expected constructor, destructor, or type conversion before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:123: error: expected initializer before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:127: error: expected initializer before ‘&’ token
In file included from /opt/pylon/include/pylon/PylonIncludes.h:23,
                 from AcquireContinuous.cpp:6:
/opt/pylon/include/genicam/Base/GCStringVector.h:190: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/Base/GCStringVector.h:192: error: ‘GenICam::gcstring_vector’ has not been declared
/opt/pylon/include/genicam/Base/GCStringVector.h:193: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/Base/GCStringVector.h:198: error: ‘GenICam::gcstring_vector’ has not been declared
/opt/pylon/include/genicam/Base/GCStringVector.h:199: error: expected initializer before ‘operator’
In file included from /opt/pylon/include/genicam/Base/GCBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireContinuous.cpp:6:
/opt/pylon/include/genicam/Base/GCException.h:61: error: expected class-name before ‘{’ token
/opt/pylon/include/genicam/Base/GCException.h:175: error: expected unqualified-id before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:175: error: expected ‘,’ or ‘...’ before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:181: error: expected unqualified-id before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:181: error: expected ‘,’ or ‘...’ before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h: In member function ‘E GenICam::ExceptionReporter<E>::Report()’:
/opt/pylon/include/genicam/Base/GCException.h:177: error: ‘s’ was not declared in this scope
/opt/pylon/include/genicam/Base/GCException.h: In member function ‘E GenICam::ExceptionReporter<E>::Report()’:
/opt/pylon/include/genicam/Base/GCException.h:183: error: ‘str’ was not declared in this scope
In file included from /opt/pylon/include/genicam/Base/GCBase.h:39,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireContinuous.cpp:6:
/opt/pylon/include/genicam/Base/GCException.h: At global scope:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::RuntimeException>’:
/opt/pylon/include/genicam/Base/GCUtilities.h:51:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::RuntimeException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::RuntimeException]’
In file included from /opt/pylon/include/genicam/GenApi/IBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/Pointer.h:37,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireContinuous.cpp:6:
/opt/pylon/include/genicam/GenApi/Types.h:143: error: ‘gcstring_vector’ in namespace ‘GenICam’ does not name a type
In file included from /opt/pylon/include/genicam/GenApi/INode.h:39,
                 from /opt/pylon/include/genicam/GenApi/Pointer.h:38,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireContinuous.cpp:6:
/opt/pylon/include/genicam/GenApi/Container.h:377: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/GenApi/Container.h:378: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/GenApi/Container.h:381: error: ‘value_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Container.h:384: error: ‘GenApi::node_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:385: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:390: error: ‘GenApi::node_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:391: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:396: error: ‘GenApi::value_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:397: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:402: error: ‘GenApi::value_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:403: error: expected initializer before ‘operator’
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:38,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireContinuous.cpp:6:
/opt/pylon/include/genicam/GenApi/INode.h:53: error: ‘node_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/INode.h:101: error: ‘NodeList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/INode.h:119: error: ‘GenICam::gcstring_vector’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:39,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireContinuous.cpp:6:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::AccessException>’:
/opt/pylon/include/genicam/GenApi/IValue.h:94:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::AccessException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::AccessException]’
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:40,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireContinuous.cpp:6:
/opt/pylon/include/genicam/GenApi/ICategory.h:65: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ICategory.h:90: error: ‘FeatureList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:44,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireContinuous.cpp:6:
/opt/pylon/include/genicam/GenApi/IEnumeration.h:58: error: ‘StringList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/IEnumeration.h:61: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:51,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireContinuous.cpp:6:
/opt/pylon/include/genicam/GenApi/INodeMap.h:55: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:55,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireContinuous.cpp:6:
/opt/pylon/include/genicam/GenApi/ISelector.h:54: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:57: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:80: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:89: error: ‘FeatureList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireContinuous.cpp:6:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::LogicalErrorException>’:
/opt/pylon/include/genicam/GenApi/Pointer.h:101:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::LogicalErrorException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::LogicalErrorException]’
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:38,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireContinuous.cpp:6:
/opt/pylon/include/genicam/GenApi/NodeMapRef.h:84: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:40,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireContinuous.cpp:6:
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: ISO C++ forbids declaration of ‘istream’ with no type
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: ‘istream’ is neither function nor member function; cannot be declared friend
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: expected ‘;’ before ‘&’ token
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: ISO C++ forbids declaration of ‘ostream’ with no type
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: ‘ostream’ is neither function nor member function; cannot be declared friend
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: expected ‘;’ before ‘&’ token
/opt/pylon/include/genicam/GenApi/Persistence.h:79: error: ‘gcstring_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Persistence.h:82: error: ‘gcstring_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Persistence.h:89: error: expected initializer before ‘&’ token
AcquireContinuous.cpp:261: error: expected `}' at end of input
make[1]: *** [AcquireContinuous.o] Error 1
make[1]: Leaving directory `/opt/pylon/PylonSamples/AcquireContinuous'
make[1]: Entering directory `/opt/pylon/PylonSamples/AcquireContinuous_SoftTrigger'
/opt/pylon/gcc-4.2.1/build/bin/g++  -I/opt/pylon/gcc-4.2.1/build/gcc-4.2.1/include/c++/4.2.1 -I/opt/pylon/include -I/opt/pylon/include/genicam -I/opt/pylon/include -DUSE_GIGE  -c -o AcquireContinuous_SoftTrigger.o AcquireContinuous_SoftTrigger.cpp
In file included from /opt/pylon/include/pylon/PylonIncludes.h:22,
                 from AcquireContinuous_SoftTrigger.cpp:5:
/opt/pylon/include/genicam/Base/GCString.h:34:18: error: string: No such file or directory
/opt/pylon/include/genicam/Base/GCString.h:36:20: error: iostream: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:23,
                 from AcquireContinuous_SoftTrigger.cpp:5:
/opt/pylon/include/genicam/Base/GCStringVector.h:186:18: error: vector: No such file or directory
In file included from /opt/pylon/include/genicam/Base/GCBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireContinuous_SoftTrigger.cpp:5:
/opt/pylon/include/genicam/Base/GCException.h:42:21: error: exception: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:43:19: error: cassert: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:44:19: error: cstdarg: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:45:19: error: sstream: No such file or directory
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:40,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireContinuous_SoftTrigger.cpp:5:
/opt/pylon/include/genicam/GenApi/Persistence.h:37:16: error: list: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:61,
                 from AcquireContinuous_SoftTrigger.cpp:5:
/opt/pylon/include/pylon/Device.h:27:18: error: bitset: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:22,
                 from AcquireContinuous_SoftTrigger.cpp:5:
/opt/pylon/include/genicam/Base/GCString.h:107: error: ISO C++ forbids declaration of ‘string’ with no type
/opt/pylon/include/genicam/Base/GCString.h:107: error: invalid use of ‘::’
/opt/pylon/include/genicam/Base/GCString.h:107: error: expected ‘;’ before ‘*’ token
/opt/pylon/include/genicam/Base/GCString.h:116: error: expected constructor, destructor, or type conversion before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:118: error: expected constructor, destructor, or type conversion before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:123: error: expected initializer before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:127: error: expected initializer before ‘&’ token
In file included from /opt/pylon/include/pylon/PylonIncludes.h:23,
                 from AcquireContinuous_SoftTrigger.cpp:5:
/opt/pylon/include/genicam/Base/GCStringVector.h:190: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/Base/GCStringVector.h:192: error: ‘GenICam::gcstring_vector’ has not been declared
/opt/pylon/include/genicam/Base/GCStringVector.h:193: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/Base/GCStringVector.h:198: error: ‘GenICam::gcstring_vector’ has not been declared
/opt/pylon/include/genicam/Base/GCStringVector.h:199: error: expected initializer before ‘operator’
In file included from /opt/pylon/include/genicam/Base/GCBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireContinuous_SoftTrigger.cpp:5:
/opt/pylon/include/genicam/Base/GCException.h:61: error: expected class-name before ‘{’ token
/opt/pylon/include/genicam/Base/GCException.h:175: error: expected unqualified-id before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:175: error: expected ‘,’ or ‘...’ before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:181: error: expected unqualified-id before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:181: error: expected ‘,’ or ‘...’ before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h: In member function ‘E GenICam::ExceptionReporter<E>::Report()’:
/opt/pylon/include/genicam/Base/GCException.h:177: error: ‘s’ was not declared in this scope
/opt/pylon/include/genicam/Base/GCException.h: In member function ‘E GenICam::ExceptionReporter<E>::Report()’:
/opt/pylon/include/genicam/Base/GCException.h:183: error: ‘str’ was not declared in this scope
In file included from /opt/pylon/include/genicam/Base/GCBase.h:39,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireContinuous_SoftTrigger.cpp:5:
/opt/pylon/include/genicam/Base/GCException.h: At global scope:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::RuntimeException>’:
/opt/pylon/include/genicam/Base/GCUtilities.h:51:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::RuntimeException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::RuntimeException]’
In file included from /opt/pylon/include/genicam/GenApi/IBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/Pointer.h:37,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireContinuous_SoftTrigger.cpp:5:
/opt/pylon/include/genicam/GenApi/Types.h:143: error: ‘gcstring_vector’ in namespace ‘GenICam’ does not name a type
In file included from /opt/pylon/include/genicam/GenApi/INode.h:39,
                 from /opt/pylon/include/genicam/GenApi/Pointer.h:38,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireContinuous_SoftTrigger.cpp:5:
/opt/pylon/include/genicam/GenApi/Container.h:377: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/GenApi/Container.h:378: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/GenApi/Container.h:381: error: ‘value_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Container.h:384: error: ‘GenApi::node_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:385: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:390: error: ‘GenApi::node_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:391: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:396: error: ‘GenApi::value_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:397: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:402: error: ‘GenApi::value_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:403: error: expected initializer before ‘operator’
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:38,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireContinuous_SoftTrigger.cpp:5:
/opt/pylon/include/genicam/GenApi/INode.h:53: error: ‘node_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/INode.h:101: error: ‘NodeList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/INode.h:119: error: ‘GenICam::gcstring_vector’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:39,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireContinuous_SoftTrigger.cpp:5:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::AccessException>’:
/opt/pylon/include/genicam/GenApi/IValue.h:94:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::AccessException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::AccessException]’
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:40,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireContinuous_SoftTrigger.cpp:5:
/opt/pylon/include/genicam/GenApi/ICategory.h:65: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ICategory.h:90: error: ‘FeatureList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:44,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireContinuous_SoftTrigger.cpp:5:
/opt/pylon/include/genicam/GenApi/IEnumeration.h:58: error: ‘StringList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/IEnumeration.h:61: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:51,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireContinuous_SoftTrigger.cpp:5:
/opt/pylon/include/genicam/GenApi/INodeMap.h:55: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:55,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireContinuous_SoftTrigger.cpp:5:
/opt/pylon/include/genicam/GenApi/ISelector.h:54: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:57: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:80: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:89: error: ‘FeatureList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireContinuous_SoftTrigger.cpp:5:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::LogicalErrorException>’:
/opt/pylon/include/genicam/GenApi/Pointer.h:101:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::LogicalErrorException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::LogicalErrorException]’
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:38,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireContinuous_SoftTrigger.cpp:5:
/opt/pylon/include/genicam/GenApi/NodeMapRef.h:84: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:40,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireContinuous_SoftTrigger.cpp:5:
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: ISO C++ forbids declaration of ‘istream’ with no type
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: ‘istream’ is neither function nor member function; cannot be declared friend
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: expected ‘;’ before ‘&’ token
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: ISO C++ forbids declaration of ‘ostream’ with no type
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: ‘ostream’ is neither function nor member function; cannot be declared friend
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: expected ‘;’ before ‘&’ token
/opt/pylon/include/genicam/GenApi/Persistence.h:79: error: ‘gcstring_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Persistence.h:82: error: ‘gcstring_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Persistence.h:89: error: expected initializer before ‘&’ token
AcquireContinuous_SoftTrigger.cpp:256: error: expected `}' at end of input
make[1]: *** [AcquireContinuous_SoftTrigger.o] Error 1
make[1]: Leaving directory `/opt/pylon/PylonSamples/AcquireContinuous_SoftTrigger'
make[1]: Entering directory `/opt/pylon/PylonSamples/AcquireSingleFrame'
/opt/pylon/gcc-4.2.1/build/bin/g++  -I/opt/pylon/gcc-4.2.1/build/gcc-4.2.1/include/c++/4.2.1 -I/opt/pylon/include -I/opt/pylon/include/genicam -I/opt/pylon/include -DUSE_GIGE  -c -o AcquireSingleFrame.o AcquireSingleFrame.cpp
In file included from /opt/pylon/include/pylon/PylonIncludes.h:22,
                 from AcquireSingleFrame.cpp:10:
/opt/pylon/include/genicam/Base/GCString.h:34:18: error: string: No such file or directory
/opt/pylon/include/genicam/Base/GCString.h:36:20: error: iostream: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:23,
                 from AcquireSingleFrame.cpp:10:
/opt/pylon/include/genicam/Base/GCStringVector.h:186:18: error: vector: No such file or directory
In file included from /opt/pylon/include/genicam/Base/GCBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame.cpp:10:
/opt/pylon/include/genicam/Base/GCException.h:42:21: error: exception: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:43:19: error: cassert: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:44:19: error: cstdarg: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:45:19: error: sstream: No such file or directory
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:40,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame.cpp:10:
/opt/pylon/include/genicam/GenApi/Persistence.h:37:16: error: list: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:61,
                 from AcquireSingleFrame.cpp:10:
/opt/pylon/include/pylon/Device.h:27:18: error: bitset: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:22,
                 from AcquireSingleFrame.cpp:10:
/opt/pylon/include/genicam/Base/GCString.h:107: error: ISO C++ forbids declaration of ‘string’ with no type
/opt/pylon/include/genicam/Base/GCString.h:107: error: invalid use of ‘::’
/opt/pylon/include/genicam/Base/GCString.h:107: error: expected ‘;’ before ‘*’ token
/opt/pylon/include/genicam/Base/GCString.h:116: error: expected constructor, destructor, or type conversion before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:118: error: expected constructor, destructor, or type conversion before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:123: error: expected initializer before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:127: error: expected initializer before ‘&’ token
In file included from /opt/pylon/include/pylon/PylonIncludes.h:23,
                 from AcquireSingleFrame.cpp:10:
/opt/pylon/include/genicam/Base/GCStringVector.h:190: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/Base/GCStringVector.h:192: error: ‘GenICam::gcstring_vector’ has not been declared
/opt/pylon/include/genicam/Base/GCStringVector.h:193: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/Base/GCStringVector.h:198: error: ‘GenICam::gcstring_vector’ has not been declared
/opt/pylon/include/genicam/Base/GCStringVector.h:199: error: expected initializer before ‘operator’
In file included from /opt/pylon/include/genicam/Base/GCBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame.cpp:10:
/opt/pylon/include/genicam/Base/GCException.h:61: error: expected class-name before ‘{’ token
/opt/pylon/include/genicam/Base/GCException.h:175: error: expected unqualified-id before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:175: error: expected ‘,’ or ‘...’ before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:181: error: expected unqualified-id before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:181: error: expected ‘,’ or ‘...’ before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h: In member function ‘E GenICam::ExceptionReporter<E>::Report()’:
/opt/pylon/include/genicam/Base/GCException.h:177: error: ‘s’ was not declared in this scope
/opt/pylon/include/genicam/Base/GCException.h: In member function ‘E GenICam::ExceptionReporter<E>::Report()’:
/opt/pylon/include/genicam/Base/GCException.h:183: error: ‘str’ was not declared in this scope
In file included from /opt/pylon/include/genicam/Base/GCBase.h:39,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame.cpp:10:
/opt/pylon/include/genicam/Base/GCException.h: At global scope:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::RuntimeException>’:
/opt/pylon/include/genicam/Base/GCUtilities.h:51:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::RuntimeException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::RuntimeException]’
In file included from /opt/pylon/include/genicam/GenApi/IBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/Pointer.h:37,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame.cpp:10:
/opt/pylon/include/genicam/GenApi/Types.h:143: error: ‘gcstring_vector’ in namespace ‘GenICam’ does not name a type
In file included from /opt/pylon/include/genicam/GenApi/INode.h:39,
                 from /opt/pylon/include/genicam/GenApi/Pointer.h:38,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame.cpp:10:
/opt/pylon/include/genicam/GenApi/Container.h:377: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/GenApi/Container.h:378: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/GenApi/Container.h:381: error: ‘value_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Container.h:384: error: ‘GenApi::node_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:385: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:390: error: ‘GenApi::node_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:391: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:396: error: ‘GenApi::value_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:397: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:402: error: ‘GenApi::value_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:403: error: expected initializer before ‘operator’
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:38,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame.cpp:10:
/opt/pylon/include/genicam/GenApi/INode.h:53: error: ‘node_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/INode.h:101: error: ‘NodeList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/INode.h:119: error: ‘GenICam::gcstring_vector’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:39,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame.cpp:10:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::AccessException>’:
/opt/pylon/include/genicam/GenApi/IValue.h:94:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::AccessException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::AccessException]’
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:40,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame.cpp:10:
/opt/pylon/include/genicam/GenApi/ICategory.h:65: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ICategory.h:90: error: ‘FeatureList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:44,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame.cpp:10:
/opt/pylon/include/genicam/GenApi/IEnumeration.h:58: error: ‘StringList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/IEnumeration.h:61: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:51,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame.cpp:10:
/opt/pylon/include/genicam/GenApi/INodeMap.h:55: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:55,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame.cpp:10:
/opt/pylon/include/genicam/GenApi/ISelector.h:54: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:57: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:80: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:89: error: ‘FeatureList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame.cpp:10:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::LogicalErrorException>’:
/opt/pylon/include/genicam/GenApi/Pointer.h:101:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::LogicalErrorException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::LogicalErrorException]’
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:38,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame.cpp:10:
/opt/pylon/include/genicam/GenApi/NodeMapRef.h:84: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:40,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame.cpp:10:
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: ISO C++ forbids declaration of ‘istream’ with no type
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: ‘istream’ is neither function nor member function; cannot be declared friend
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: expected ‘;’ before ‘&’ token
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: ISO C++ forbids declaration of ‘ostream’ with no type
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: ‘ostream’ is neither function nor member function; cannot be declared friend
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: expected ‘;’ before ‘&’ token
/opt/pylon/include/genicam/GenApi/Persistence.h:79: error: ‘gcstring_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Persistence.h:82: error: ‘gcstring_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Persistence.h:89: error: expected initializer before ‘&’ token
AcquireSingleFrame.cpp:205: error: expected `}' at end of input
make[1]: *** [AcquireSingleFrame.o] Error 1
make[1]: Leaving directory `/opt/pylon/PylonSamples/AcquireSingleFrame'
make[1]: Entering directory `/opt/pylon/PylonSamples/AcquireSingleFrame_ChunkImage'
/opt/pylon/gcc-4.2.1/build/bin/g++  -I/opt/pylon/gcc-4.2.1/build/gcc-4.2.1/include/c++/4.2.1 -I/opt/pylon/include -I/opt/pylon/include/genicam -I/opt/pylon/include -DUSE_GIGE  -c -o AcquireSingleFrame_ChunkImage.o AcquireSingleFrame_ChunkImage.cpp
In file included from /opt/pylon/include/pylon/PylonIncludes.h:22,
                 from AcquireSingleFrame_ChunkImage.cpp:5:
/opt/pylon/include/genicam/Base/GCString.h:34:18: error: string: No such file or directory
/opt/pylon/include/genicam/Base/GCString.h:36:20: error: iostream: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:23,
                 from AcquireSingleFrame_ChunkImage.cpp:5:
/opt/pylon/include/genicam/Base/GCStringVector.h:186:18: error: vector: No such file or directory
In file included from /opt/pylon/include/genicam/Base/GCBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame_ChunkImage.cpp:5:
/opt/pylon/include/genicam/Base/GCException.h:42:21: error: exception: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:43:19: error: cassert: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:44:19: error: cstdarg: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:45:19: error: sstream: No such file or directory
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:40,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame_ChunkImage.cpp:5:
/opt/pylon/include/genicam/GenApi/Persistence.h:37:16: error: list: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:61,
                 from AcquireSingleFrame_ChunkImage.cpp:5:
/opt/pylon/include/pylon/Device.h:27:18: error: bitset: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:22,
                 from AcquireSingleFrame_ChunkImage.cpp:5:
/opt/pylon/include/genicam/Base/GCString.h:107: error: ISO C++ forbids declaration of ‘string’ with no type
/opt/pylon/include/genicam/Base/GCString.h:107: error: invalid use of ‘::’
/opt/pylon/include/genicam/Base/GCString.h:107: error: expected ‘;’ before ‘*’ token
/opt/pylon/include/genicam/Base/GCString.h:116: error: expected constructor, destructor, or type conversion before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:118: error: expected constructor, destructor, or type conversion before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:123: error: expected initializer before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:127: error: expected initializer before ‘&’ token
In file included from /opt/pylon/include/pylon/PylonIncludes.h:23,
                 from AcquireSingleFrame_ChunkImage.cpp:5:
/opt/pylon/include/genicam/Base/GCStringVector.h:190: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/Base/GCStringVector.h:192: error: ‘GenICam::gcstring_vector’ has not been declared
/opt/pylon/include/genicam/Base/GCStringVector.h:193: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/Base/GCStringVector.h:198: error: ‘GenICam::gcstring_vector’ has not been declared
/opt/pylon/include/genicam/Base/GCStringVector.h:199: error: expected initializer before ‘operator’
In file included from /opt/pylon/include/genicam/Base/GCBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame_ChunkImage.cpp:5:
/opt/pylon/include/genicam/Base/GCException.h:61: error: expected class-name before ‘{’ token
/opt/pylon/include/genicam/Base/GCException.h:175: error: expected unqualified-id before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:175: error: expected ‘,’ or ‘...’ before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:181: error: expected unqualified-id before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:181: error: expected ‘,’ or ‘...’ before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h: In member function ‘E GenICam::ExceptionReporter<E>::Report()’:
/opt/pylon/include/genicam/Base/GCException.h:177: error: ‘s’ was not declared in this scope
/opt/pylon/include/genicam/Base/GCException.h: In member function ‘E GenICam::ExceptionReporter<E>::Report()’:
/opt/pylon/include/genicam/Base/GCException.h:183: error: ‘str’ was not declared in this scope
In file included from /opt/pylon/include/genicam/Base/GCBase.h:39,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame_ChunkImage.cpp:5:
/opt/pylon/include/genicam/Base/GCException.h: At global scope:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::RuntimeException>’:
/opt/pylon/include/genicam/Base/GCUtilities.h:51:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::RuntimeException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::RuntimeException]’
In file included from /opt/pylon/include/genicam/GenApi/IBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/Pointer.h:37,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame_ChunkImage.cpp:5:
/opt/pylon/include/genicam/GenApi/Types.h:143: error: ‘gcstring_vector’ in namespace ‘GenICam’ does not name a type
In file included from /opt/pylon/include/genicam/GenApi/INode.h:39,
                 from /opt/pylon/include/genicam/GenApi/Pointer.h:38,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame_ChunkImage.cpp:5:
/opt/pylon/include/genicam/GenApi/Container.h:377: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/GenApi/Container.h:378: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/GenApi/Container.h:381: error: ‘value_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Container.h:384: error: ‘GenApi::node_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:385: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:390: error: ‘GenApi::node_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:391: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:396: error: ‘GenApi::value_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:397: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:402: error: ‘GenApi::value_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:403: error: expected initializer before ‘operator’
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:38,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame_ChunkImage.cpp:5:
/opt/pylon/include/genicam/GenApi/INode.h:53: error: ‘node_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/INode.h:101: error: ‘NodeList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/INode.h:119: error: ‘GenICam::gcstring_vector’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:39,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame_ChunkImage.cpp:5:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::AccessException>’:
/opt/pylon/include/genicam/GenApi/IValue.h:94:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::AccessException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::AccessException]’
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:40,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame_ChunkImage.cpp:5:
/opt/pylon/include/genicam/GenApi/ICategory.h:65: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ICategory.h:90: error: ‘FeatureList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:44,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame_ChunkImage.cpp:5:
/opt/pylon/include/genicam/GenApi/IEnumeration.h:58: error: ‘StringList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/IEnumeration.h:61: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:51,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame_ChunkImage.cpp:5:
/opt/pylon/include/genicam/GenApi/INodeMap.h:55: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:55,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame_ChunkImage.cpp:5:
/opt/pylon/include/genicam/GenApi/ISelector.h:54: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:57: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:80: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:89: error: ‘FeatureList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame_ChunkImage.cpp:5:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::LogicalErrorException>’:
/opt/pylon/include/genicam/GenApi/Pointer.h:101:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::LogicalErrorException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::LogicalErrorException]’
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:38,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame_ChunkImage.cpp:5:
/opt/pylon/include/genicam/GenApi/NodeMapRef.h:84: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:40,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame_ChunkImage.cpp:5:
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: ISO C++ forbids declaration of ‘istream’ with no type
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: ‘istream’ is neither function nor member function; cannot be declared friend
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: expected ‘;’ before ‘&’ token
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: ISO C++ forbids declaration of ‘ostream’ with no type
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: ‘ostream’ is neither function nor member function; cannot be declared friend
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: expected ‘;’ before ‘&’ token
/opt/pylon/include/genicam/GenApi/Persistence.h:79: error: ‘gcstring_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Persistence.h:82: error: ‘gcstring_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Persistence.h:89: error: expected initializer before ‘&’ token
AcquireSingleFrame_ChunkImage.cpp:240: error: expected `}' at end of input
make[1]: *** [AcquireSingleFrame_ChunkImage.o] Error 1
make[1]: Leaving directory `/opt/pylon/PylonSamples/AcquireSingleFrame_ChunkImage'
make[1]: Entering directory `/opt/pylon/PylonSamples/AcquireSingleFrame_Gen'
/opt/pylon/gcc-4.2.1/build/bin/g++  -I/opt/pylon/gcc-4.2.1/build/gcc-4.2.1/include/c++/4.2.1 -I/opt/pylon/include -I/opt/pylon/include/genicam -I/opt/pylon/include -DUSE_GIGE  -c -o AcquireSingleFrame_Gen.o AcquireSingleFrame_Gen.cpp
In file included from /opt/pylon/include/pylon/PylonIncludes.h:22,
                 from AcquireSingleFrame_Gen.cpp:5:
/opt/pylon/include/genicam/Base/GCString.h:34:18: error: string: No such file or directory
/opt/pylon/include/genicam/Base/GCString.h:36:20: error: iostream: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:23,
                 from AcquireSingleFrame_Gen.cpp:5:
/opt/pylon/include/genicam/Base/GCStringVector.h:186:18: error: vector: No such file or directory
In file included from /opt/pylon/include/genicam/Base/GCBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame_Gen.cpp:5:
/opt/pylon/include/genicam/Base/GCException.h:42:21: error: exception: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:43:19: error: cassert: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:44:19: error: cstdarg: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:45:19: error: sstream: No such file or directory
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:40,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame_Gen.cpp:5:
/opt/pylon/include/genicam/GenApi/Persistence.h:37:16: error: list: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:61,
                 from AcquireSingleFrame_Gen.cpp:5:
/opt/pylon/include/pylon/Device.h:27:18: error: bitset: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:22,
                 from AcquireSingleFrame_Gen.cpp:5:
/opt/pylon/include/genicam/Base/GCString.h:107: error: ISO C++ forbids declaration of ‘string’ with no type
/opt/pylon/include/genicam/Base/GCString.h:107: error: invalid use of ‘::’
/opt/pylon/include/genicam/Base/GCString.h:107: error: expected ‘;’ before ‘*’ token
/opt/pylon/include/genicam/Base/GCString.h:116: error: expected constructor, destructor, or type conversion before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:118: error: expected constructor, destructor, or type conversion before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:123: error: expected initializer before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:127: error: expected initializer before ‘&’ token
In file included from /opt/pylon/include/pylon/PylonIncludes.h:23,
                 from AcquireSingleFrame_Gen.cpp:5:
/opt/pylon/include/genicam/Base/GCStringVector.h:190: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/Base/GCStringVector.h:192: error: ‘GenICam::gcstring_vector’ has not been declared
/opt/pylon/include/genicam/Base/GCStringVector.h:193: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/Base/GCStringVector.h:198: error: ‘GenICam::gcstring_vector’ has not been declared
/opt/pylon/include/genicam/Base/GCStringVector.h:199: error: expected initializer before ‘operator’
In file included from /opt/pylon/include/genicam/Base/GCBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame_Gen.cpp:5:
/opt/pylon/include/genicam/Base/GCException.h:61: error: expected class-name before ‘{’ token
/opt/pylon/include/genicam/Base/GCException.h:175: error: expected unqualified-id before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:175: error: expected ‘,’ or ‘...’ before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:181: error: expected unqualified-id before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:181: error: expected ‘,’ or ‘...’ before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h: In member function ‘E GenICam::ExceptionReporter<E>::Report()’:
/opt/pylon/include/genicam/Base/GCException.h:177: error: ‘s’ was not declared in this scope
/opt/pylon/include/genicam/Base/GCException.h: In member function ‘E GenICam::ExceptionReporter<E>::Report()’:
/opt/pylon/include/genicam/Base/GCException.h:183: error: ‘str’ was not declared in this scope
In file included from /opt/pylon/include/genicam/Base/GCBase.h:39,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame_Gen.cpp:5:
/opt/pylon/include/genicam/Base/GCException.h: At global scope:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::RuntimeException>’:
/opt/pylon/include/genicam/Base/GCUtilities.h:51:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::RuntimeException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::RuntimeException]’
In file included from /opt/pylon/include/genicam/GenApi/IBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/Pointer.h:37,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame_Gen.cpp:5:
/opt/pylon/include/genicam/GenApi/Types.h:143: error: ‘gcstring_vector’ in namespace ‘GenICam’ does not name a type
In file included from /opt/pylon/include/genicam/GenApi/INode.h:39,
                 from /opt/pylon/include/genicam/GenApi/Pointer.h:38,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame_Gen.cpp:5:
/opt/pylon/include/genicam/GenApi/Container.h:377: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/GenApi/Container.h:378: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/GenApi/Container.h:381: error: ‘value_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Container.h:384: error: ‘GenApi::node_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:385: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:390: error: ‘GenApi::node_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:391: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:396: error: ‘GenApi::value_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:397: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:402: error: ‘GenApi::value_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:403: error: expected initializer before ‘operator’
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:38,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame_Gen.cpp:5:
/opt/pylon/include/genicam/GenApi/INode.h:53: error: ‘node_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/INode.h:101: error: ‘NodeList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/INode.h:119: error: ‘GenICam::gcstring_vector’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:39,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame_Gen.cpp:5:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::AccessException>’:
/opt/pylon/include/genicam/GenApi/IValue.h:94:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::AccessException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::AccessException]’
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:40,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame_Gen.cpp:5:
/opt/pylon/include/genicam/GenApi/ICategory.h:65: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ICategory.h:90: error: ‘FeatureList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:44,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame_Gen.cpp:5:
/opt/pylon/include/genicam/GenApi/IEnumeration.h:58: error: ‘StringList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/IEnumeration.h:61: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:51,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame_Gen.cpp:5:
/opt/pylon/include/genicam/GenApi/INodeMap.h:55: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:55,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame_Gen.cpp:5:
/opt/pylon/include/genicam/GenApi/ISelector.h:54: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:57: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:80: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:89: error: ‘FeatureList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame_Gen.cpp:5:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::LogicalErrorException>’:
/opt/pylon/include/genicam/GenApi/Pointer.h:101:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::LogicalErrorException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::LogicalErrorException]’
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:38,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame_Gen.cpp:5:
/opt/pylon/include/genicam/GenApi/NodeMapRef.h:84: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:40,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from AcquireSingleFrame_Gen.cpp:5:
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: ISO C++ forbids declaration of ‘istream’ with no type
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: ‘istream’ is neither function nor member function; cannot be declared friend
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: expected ‘;’ before ‘&’ token
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: ISO C++ forbids declaration of ‘ostream’ with no type
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: ‘ostream’ is neither function nor member function; cannot be declared friend
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: expected ‘;’ before ‘&’ token
/opt/pylon/include/genicam/GenApi/Persistence.h:79: error: ‘gcstring_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Persistence.h:82: error: ‘gcstring_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Persistence.h:89: error: expected initializer before ‘&’ token
AcquireSingleFrame_Gen.cpp:186: error: expected `}' at end of input
make[1]: *** [AcquireSingleFrame_Gen.o] Error 1
make[1]: Leaving directory `/opt/pylon/PylonSamples/AcquireSingleFrame_Gen'
make[1]: Entering directory `/opt/pylon/PylonSamples/CameraEvents'
/opt/pylon/gcc-4.2.1/build/bin/g++  -I/opt/pylon/gcc-4.2.1/build/gcc-4.2.1/include/c++/4.2.1 -I/opt/pylon/include -I/opt/pylon/include/genicam -I/opt/pylon/include -DUSE_GIGE  -c -o CameraEvents.o CameraEvents.cpp
In file included from /opt/pylon/include/pylon/PylonIncludes.h:22,
                 from CameraEvents.cpp:7:
/opt/pylon/include/genicam/Base/GCString.h:34:18: error: string: No such file or directory
/opt/pylon/include/genicam/Base/GCString.h:36:20: error: iostream: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:23,
                 from CameraEvents.cpp:7:
/opt/pylon/include/genicam/Base/GCStringVector.h:186:18: error: vector: No such file or directory
In file included from /opt/pylon/include/genicam/Base/GCBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from CameraEvents.cpp:7:
/opt/pylon/include/genicam/Base/GCException.h:42:21: error: exception: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:43:19: error: cassert: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:44:19: error: cstdarg: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:45:19: error: sstream: No such file or directory
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:40,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from CameraEvents.cpp:7:
/opt/pylon/include/genicam/GenApi/Persistence.h:37:16: error: list: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:61,
                 from CameraEvents.cpp:7:
/opt/pylon/include/pylon/Device.h:27:18: error: bitset: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:22,
                 from CameraEvents.cpp:7:
/opt/pylon/include/genicam/Base/GCString.h:107: error: ISO C++ forbids declaration of ‘string’ with no type
/opt/pylon/include/genicam/Base/GCString.h:107: error: invalid use of ‘::’
/opt/pylon/include/genicam/Base/GCString.h:107: error: expected ‘;’ before ‘*’ token
/opt/pylon/include/genicam/Base/GCString.h:116: error: expected constructor, destructor, or type conversion before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:118: error: expected constructor, destructor, or type conversion before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:123: error: expected initializer before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:127: error: expected initializer before ‘&’ token
In file included from /opt/pylon/include/pylon/PylonIncludes.h:23,
                 from CameraEvents.cpp:7:
/opt/pylon/include/genicam/Base/GCStringVector.h:190: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/Base/GCStringVector.h:192: error: ‘GenICam::gcstring_vector’ has not been declared
/opt/pylon/include/genicam/Base/GCStringVector.h:193: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/Base/GCStringVector.h:198: error: ‘GenICam::gcstring_vector’ has not been declared
/opt/pylon/include/genicam/Base/GCStringVector.h:199: error: expected initializer before ‘operator’
In file included from /opt/pylon/include/genicam/Base/GCBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from CameraEvents.cpp:7:
/opt/pylon/include/genicam/Base/GCException.h:61: error: expected class-name before ‘{’ token
/opt/pylon/include/genicam/Base/GCException.h:175: error: expected unqualified-id before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:175: error: expected ‘,’ or ‘...’ before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:181: error: expected unqualified-id before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:181: error: expected ‘,’ or ‘...’ before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h: In member function ‘E GenICam::ExceptionReporter<E>::Report()’:
/opt/pylon/include/genicam/Base/GCException.h:177: error: ‘s’ was not declared in this scope
/opt/pylon/include/genicam/Base/GCException.h: In member function ‘E GenICam::ExceptionReporter<E>::Report()’:
/opt/pylon/include/genicam/Base/GCException.h:183: error: ‘str’ was not declared in this scope
In file included from /opt/pylon/include/genicam/Base/GCBase.h:39,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from CameraEvents.cpp:7:
/opt/pylon/include/genicam/Base/GCException.h: At global scope:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::RuntimeException>’:
/opt/pylon/include/genicam/Base/GCUtilities.h:51:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::RuntimeException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::RuntimeException]’
In file included from /opt/pylon/include/genicam/GenApi/IBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/Pointer.h:37,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from CameraEvents.cpp:7:
/opt/pylon/include/genicam/GenApi/Types.h:143: error: ‘gcstring_vector’ in namespace ‘GenICam’ does not name a type
In file included from /opt/pylon/include/genicam/GenApi/INode.h:39,
                 from /opt/pylon/include/genicam/GenApi/Pointer.h:38,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from CameraEvents.cpp:7:
/opt/pylon/include/genicam/GenApi/Container.h:377: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/GenApi/Container.h:378: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/GenApi/Container.h:381: error: ‘value_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Container.h:384: error: ‘GenApi::node_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:385: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:390: error: ‘GenApi::node_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:391: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:396: error: ‘GenApi::value_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:397: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:402: error: ‘GenApi::value_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:403: error: expected initializer before ‘operator’
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:38,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from CameraEvents.cpp:7:
/opt/pylon/include/genicam/GenApi/INode.h:53: error: ‘node_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/INode.h:101: error: ‘NodeList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/INode.h:119: error: ‘GenICam::gcstring_vector’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:39,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from CameraEvents.cpp:7:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::AccessException>’:
/opt/pylon/include/genicam/GenApi/IValue.h:94:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::AccessException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::AccessException]’
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:40,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from CameraEvents.cpp:7:
/opt/pylon/include/genicam/GenApi/ICategory.h:65: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ICategory.h:90: error: ‘FeatureList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:44,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from CameraEvents.cpp:7:
/opt/pylon/include/genicam/GenApi/IEnumeration.h:58: error: ‘StringList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/IEnumeration.h:61: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:51,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from CameraEvents.cpp:7:
/opt/pylon/include/genicam/GenApi/INodeMap.h:55: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:55,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from CameraEvents.cpp:7:
/opt/pylon/include/genicam/GenApi/ISelector.h:54: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:57: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:80: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:89: error: ‘FeatureList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from CameraEvents.cpp:7:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::LogicalErrorException>’:
/opt/pylon/include/genicam/GenApi/Pointer.h:101:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::LogicalErrorException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::LogicalErrorException]’
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:38,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from CameraEvents.cpp:7:
/opt/pylon/include/genicam/GenApi/NodeMapRef.h:84: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:40,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from CameraEvents.cpp:7:
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: ISO C++ forbids declaration of ‘istream’ with no type
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: ‘istream’ is neither function nor member function; cannot be declared friend
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: expected ‘;’ before ‘&’ token
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: ISO C++ forbids declaration of ‘ostream’ with no type
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: ‘ostream’ is neither function nor member function; cannot be declared friend
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: expected ‘;’ before ‘&’ token
/opt/pylon/include/genicam/GenApi/Persistence.h:79: error: ‘gcstring_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Persistence.h:82: error: ‘gcstring_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Persistence.h:89: error: expected initializer before ‘&’ token
CameraEvents.cpp:383: error: expected `}' at end of input
make[1]: *** [CameraEvents.o] Error 1
make[1]: Leaving directory `/opt/pylon/PylonSamples/CameraEvents'
make[1]: Entering directory `/opt/pylon/PylonSamples/LookupTable'
/opt/pylon/gcc-4.2.1/build/bin/g++  -I/opt/pylon/gcc-4.2.1/build/gcc-4.2.1/include/c++/4.2.1 -I/opt/pylon/include -I/opt/pylon/include/genicam -I/opt/pylon/include -DUSE_GIGE  -c -o LookupTable.o LookupTable.cpp
In file included from /opt/pylon/include/pylon/PylonIncludes.h:22,
                 from LookupTable.cpp:7:
/opt/pylon/include/genicam/Base/GCString.h:34:18: error: string: No such file or directory
/opt/pylon/include/genicam/Base/GCString.h:36:20: error: iostream: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:23,
                 from LookupTable.cpp:7:
/opt/pylon/include/genicam/Base/GCStringVector.h:186:18: error: vector: No such file or directory
In file included from /opt/pylon/include/genicam/Base/GCBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from LookupTable.cpp:7:
/opt/pylon/include/genicam/Base/GCException.h:42:21: error: exception: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:43:19: error: cassert: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:44:19: error: cstdarg: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:45:19: error: sstream: No such file or directory
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:40,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from LookupTable.cpp:7:
/opt/pylon/include/genicam/GenApi/Persistence.h:37:16: error: list: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:61,
                 from LookupTable.cpp:7:
/opt/pylon/include/pylon/Device.h:27:18: error: bitset: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:22,
                 from LookupTable.cpp:7:
/opt/pylon/include/genicam/Base/GCString.h:107: error: ISO C++ forbids declaration of ‘string’ with no type
/opt/pylon/include/genicam/Base/GCString.h:107: error: invalid use of ‘::’
/opt/pylon/include/genicam/Base/GCString.h:107: error: expected ‘;’ before ‘*’ token
/opt/pylon/include/genicam/Base/GCString.h:116: error: expected constructor, destructor, or type conversion before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:118: error: expected constructor, destructor, or type conversion before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:123: error: expected initializer before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:127: error: expected initializer before ‘&’ token
In file included from /opt/pylon/include/pylon/PylonIncludes.h:23,
                 from LookupTable.cpp:7:
/opt/pylon/include/genicam/Base/GCStringVector.h:190: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/Base/GCStringVector.h:192: error: ‘GenICam::gcstring_vector’ has not been declared
/opt/pylon/include/genicam/Base/GCStringVector.h:193: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/Base/GCStringVector.h:198: error: ‘GenICam::gcstring_vector’ has not been declared
/opt/pylon/include/genicam/Base/GCStringVector.h:199: error: expected initializer before ‘operator’
In file included from /opt/pylon/include/genicam/Base/GCBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from LookupTable.cpp:7:
/opt/pylon/include/genicam/Base/GCException.h:61: error: expected class-name before ‘{’ token
/opt/pylon/include/genicam/Base/GCException.h:175: error: expected unqualified-id before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:175: error: expected ‘,’ or ‘...’ before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:181: error: expected unqualified-id before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:181: error: expected ‘,’ or ‘...’ before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h: In member function ‘E GenICam::ExceptionReporter<E>::Report()’:
/opt/pylon/include/genicam/Base/GCException.h:177: error: ‘s’ was not declared in this scope
/opt/pylon/include/genicam/Base/GCException.h: In member function ‘E GenICam::ExceptionReporter<E>::Report()’:
/opt/pylon/include/genicam/Base/GCException.h:183: error: ‘str’ was not declared in this scope
In file included from /opt/pylon/include/genicam/Base/GCBase.h:39,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from LookupTable.cpp:7:
/opt/pylon/include/genicam/Base/GCException.h: At global scope:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::RuntimeException>’:
/opt/pylon/include/genicam/Base/GCUtilities.h:51:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::RuntimeException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::RuntimeException]’
In file included from /opt/pylon/include/genicam/GenApi/IBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/Pointer.h:37,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from LookupTable.cpp:7:
/opt/pylon/include/genicam/GenApi/Types.h:143: error: ‘gcstring_vector’ in namespace ‘GenICam’ does not name a type
In file included from /opt/pylon/include/genicam/GenApi/INode.h:39,
                 from /opt/pylon/include/genicam/GenApi/Pointer.h:38,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from LookupTable.cpp:7:
/opt/pylon/include/genicam/GenApi/Container.h:377: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/GenApi/Container.h:378: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/GenApi/Container.h:381: error: ‘value_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Container.h:384: error: ‘GenApi::node_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:385: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:390: error: ‘GenApi::node_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:391: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:396: error: ‘GenApi::value_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:397: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:402: error: ‘GenApi::value_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:403: error: expected initializer before ‘operator’
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:38,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from LookupTable.cpp:7:
/opt/pylon/include/genicam/GenApi/INode.h:53: error: ‘node_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/INode.h:101: error: ‘NodeList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/INode.h:119: error: ‘GenICam::gcstring_vector’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:39,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from LookupTable.cpp:7:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::AccessException>’:
/opt/pylon/include/genicam/GenApi/IValue.h:94:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::AccessException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::AccessException]’
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:40,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from LookupTable.cpp:7:
/opt/pylon/include/genicam/GenApi/ICategory.h:65: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ICategory.h:90: error: ‘FeatureList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:44,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from LookupTable.cpp:7:
/opt/pylon/include/genicam/GenApi/IEnumeration.h:58: error: ‘StringList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/IEnumeration.h:61: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:51,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from LookupTable.cpp:7:
/opt/pylon/include/genicam/GenApi/INodeMap.h:55: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:55,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from LookupTable.cpp:7:
/opt/pylon/include/genicam/GenApi/ISelector.h:54: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:57: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:80: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:89: error: ‘FeatureList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from LookupTable.cpp:7:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::LogicalErrorException>’:
/opt/pylon/include/genicam/GenApi/Pointer.h:101:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::LogicalErrorException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::LogicalErrorException]’
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:38,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from LookupTable.cpp:7:
/opt/pylon/include/genicam/GenApi/NodeMapRef.h:84: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:40,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from LookupTable.cpp:7:
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: ISO C++ forbids declaration of ‘istream’ with no type
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: ‘istream’ is neither function nor member function; cannot be declared friend
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: expected ‘;’ before ‘&’ token
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: ISO C++ forbids declaration of ‘ostream’ with no type
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: ‘ostream’ is neither function nor member function; cannot be declared friend
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: expected ‘;’ before ‘&’ token
/opt/pylon/include/genicam/GenApi/Persistence.h:79: error: ‘gcstring_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Persistence.h:82: error: ‘gcstring_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Persistence.h:89: error: expected initializer before ‘&’ token
LookupTable.cpp:123: error: expected `}' at end of input
make[1]: *** [LookupTable.o] Error 1
make[1]: Leaving directory `/opt/pylon/PylonSamples/LookupTable'
make[1]: Entering directory `/opt/pylon/PylonSamples/ManyCamerasUnix'
/opt/pylon/gcc-4.2.1/build/bin/g++  -I/opt/pylon/gcc-4.2.1/build/gcc-4.2.1/include/c++/4.2.1 -I/opt/pylon/include -I/opt/pylon/include/genicam -I/opt/pylon/include -DUSE_GIGE  -c -o ManyCamerasUnix.o ManyCamerasUnix.cpp
In file included from /opt/pylon/include/pylon/PylonIncludes.h:22,
                 from CGrabThread.h:5,
                 from ManyCamerasUnix.cpp:5:
/opt/pylon/include/genicam/Base/GCString.h:34:18: error: string: No such file or directory
/opt/pylon/include/genicam/Base/GCString.h:36:20: error: iostream: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:23,
                 from CGrabThread.h:5,
                 from ManyCamerasUnix.cpp:5:
/opt/pylon/include/genicam/Base/GCStringVector.h:186:18: error: vector: No such file or directory
In file included from /opt/pylon/include/genicam/Base/GCBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from CGrabThread.h:5,
                 from ManyCamerasUnix.cpp:5:
/opt/pylon/include/genicam/Base/GCException.h:42:21: error: exception: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:43:19: error: cassert: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:44:19: error: cstdarg: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:45:19: error: sstream: No such file or directory
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:40,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from CGrabThread.h:5,
                 from ManyCamerasUnix.cpp:5:
/opt/pylon/include/genicam/GenApi/Persistence.h:37:16: error: list: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:61,
                 from CGrabThread.h:5,
                 from ManyCamerasUnix.cpp:5:
/opt/pylon/include/pylon/Device.h:27:18: error: bitset: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:22,
                 from CGrabThread.h:5,
                 from ManyCamerasUnix.cpp:5:
/opt/pylon/include/genicam/Base/GCString.h:107: error: ISO C++ forbids declaration of ‘string’ with no type
/opt/pylon/include/genicam/Base/GCString.h:107: error: invalid use of ‘::’
/opt/pylon/include/genicam/Base/GCString.h:107: error: expected ‘;’ before ‘*’ token
/opt/pylon/include/genicam/Base/GCString.h:116: error: expected constructor, destructor, or type conversion before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:118: error: expected constructor, destructor, or type conversion before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:123: error: expected initializer before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:127: error: expected initializer before ‘&’ token
In file included from /opt/pylon/include/pylon/PylonIncludes.h:23,
                 from CGrabThread.h:5,
                 from ManyCamerasUnix.cpp:5:
/opt/pylon/include/genicam/Base/GCStringVector.h:190: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/Base/GCStringVector.h:192: error: ‘GenICam::gcstring_vector’ has not been declared
/opt/pylon/include/genicam/Base/GCStringVector.h:193: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/Base/GCStringVector.h:198: error: ‘GenICam::gcstring_vector’ has not been declared
/opt/pylon/include/genicam/Base/GCStringVector.h:199: error: expected initializer before ‘operator’
In file included from /opt/pylon/include/genicam/Base/GCBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from CGrabThread.h:5,
                 from ManyCamerasUnix.cpp:5:
/opt/pylon/include/genicam/Base/GCException.h:61: error: expected class-name before ‘{’ token
/opt/pylon/include/genicam/Base/GCException.h:175: error: expected unqualified-id before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:175: error: expected ‘,’ or ‘...’ before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:181: error: expected unqualified-id before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:181: error: expected ‘,’ or ‘...’ before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h: In member function ‘E GenICam::ExceptionReporter<E>::Report()’:
/opt/pylon/include/genicam/Base/GCException.h:177: error: ‘s’ was not declared in this scope
/opt/pylon/include/genicam/Base/GCException.h: In member function ‘E GenICam::ExceptionReporter<E>::Report()’:
/opt/pylon/include/genicam/Base/GCException.h:183: error: ‘str’ was not declared in this scope
In file included from /opt/pylon/include/genicam/Base/GCBase.h:39,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from CGrabThread.h:5,
                 from ManyCamerasUnix.cpp:5:
/opt/pylon/include/genicam/Base/GCException.h: At global scope:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::RuntimeException>’:
/opt/pylon/include/genicam/Base/GCUtilities.h:51:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::RuntimeException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::RuntimeException]’
In file included from /opt/pylon/include/genicam/GenApi/IBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/Pointer.h:37,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from CGrabThread.h:5,
                 from ManyCamerasUnix.cpp:5:
/opt/pylon/include/genicam/GenApi/Types.h:143: error: ‘gcstring_vector’ in namespace ‘GenICam’ does not name a type
In file included from /opt/pylon/include/genicam/GenApi/INode.h:39,
                 from /opt/pylon/include/genicam/GenApi/Pointer.h:38,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from CGrabThread.h:5,
                 from ManyCamerasUnix.cpp:5:
/opt/pylon/include/genicam/GenApi/Container.h:377: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/GenApi/Container.h:378: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/GenApi/Container.h:381: error: ‘value_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Container.h:384: error: ‘GenApi::node_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:385: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:390: error: ‘GenApi::node_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:391: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:396: error: ‘GenApi::value_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:397: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:402: error: ‘GenApi::value_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:403: error: expected initializer before ‘operator’
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:38,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from CGrabThread.h:5,
                 from ManyCamerasUnix.cpp:5:
/opt/pylon/include/genicam/GenApi/INode.h:53: error: ‘node_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/INode.h:101: error: ‘NodeList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/INode.h:119: error: ‘GenICam::gcstring_vector’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:39,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from CGrabThread.h:5,
                 from ManyCamerasUnix.cpp:5:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::AccessException>’:
/opt/pylon/include/genicam/GenApi/IValue.h:94:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::AccessException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::AccessException]’
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:40,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from CGrabThread.h:5,
                 from ManyCamerasUnix.cpp:5:
/opt/pylon/include/genicam/GenApi/ICategory.h:65: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ICategory.h:90: error: ‘FeatureList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:44,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from CGrabThread.h:5,
                 from ManyCamerasUnix.cpp:5:
/opt/pylon/include/genicam/GenApi/IEnumeration.h:58: error: ‘StringList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/IEnumeration.h:61: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:51,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from CGrabThread.h:5,
                 from ManyCamerasUnix.cpp:5:
/opt/pylon/include/genicam/GenApi/INodeMap.h:55: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:55,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from CGrabThread.h:5,
                 from ManyCamerasUnix.cpp:5:
/opt/pylon/include/genicam/GenApi/ISelector.h:54: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:57: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:80: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:89: error: ‘FeatureList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from CGrabThread.h:5,
                 from ManyCamerasUnix.cpp:5:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::LogicalErrorException>’:
/opt/pylon/include/genicam/GenApi/Pointer.h:101:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::LogicalErrorException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::LogicalErrorException]’
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:38,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from CGrabThread.h:5,
                 from ManyCamerasUnix.cpp:5:
/opt/pylon/include/genicam/GenApi/NodeMapRef.h:84: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:40,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from CGrabThread.h:5,
                 from ManyCamerasUnix.cpp:5:
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: ISO C++ forbids declaration of ‘istream’ with no type
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: ‘istream’ is neither function nor member function; cannot be declared friend
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: expected ‘;’ before ‘&’ token
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: ISO C++ forbids declaration of ‘ostream’ with no type
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: ‘ostream’ is neither function nor member function; cannot be declared friend
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: expected ‘;’ before ‘&’ token
/opt/pylon/include/genicam/GenApi/Persistence.h:79: error: ‘gcstring_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Persistence.h:82: error: ‘gcstring_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Persistence.h:89: error: expected initializer before ‘&’ token
ManyCamerasUnix.cpp:195: error: expected `}' at end of input
make[1]: *** [ManyCamerasUnix.o] Error 1
make[1]: Leaving directory `/opt/pylon/PylonSamples/ManyCamerasUnix'
make[1]: Entering directory `/opt/pylon/PylonSamples/ParametrizeCamera'
/opt/pylon/gcc-4.2.1/build/bin/g++  -I/opt/pylon/gcc-4.2.1/build/gcc-4.2.1/include/c++/4.2.1 -I/opt/pylon/include -I/opt/pylon/include/genicam -I/opt/pylon/include -DUSE_GIGE  -c -o ParametrizeCamera.o ParametrizeCamera.cpp
In file included from /opt/pylon/include/pylon/PylonIncludes.h:22,
                 from ParametrizeCamera.cpp:6:
/opt/pylon/include/genicam/Base/GCString.h:34:18: error: string: No such file or directory
/opt/pylon/include/genicam/Base/GCString.h:36:20: error: iostream: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:23,
                 from ParametrizeCamera.cpp:6:
/opt/pylon/include/genicam/Base/GCStringVector.h:186:18: error: vector: No such file or directory
In file included from /opt/pylon/include/genicam/Base/GCBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from ParametrizeCamera.cpp:6:
/opt/pylon/include/genicam/Base/GCException.h:42:21: error: exception: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:43:19: error: cassert: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:44:19: error: cstdarg: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:45:19: error: sstream: No such file or directory
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:40,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from ParametrizeCamera.cpp:6:
/opt/pylon/include/genicam/GenApi/Persistence.h:37:16: error: list: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:61,
                 from ParametrizeCamera.cpp:6:
/opt/pylon/include/pylon/Device.h:27:18: error: bitset: No such file or directory
ParametrizeCamera.cpp:27:19: error: iomanip: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:22,
                 from ParametrizeCamera.cpp:6:
/opt/pylon/include/genicam/Base/GCString.h:107: error: ISO C++ forbids declaration of ‘string’ with no type
/opt/pylon/include/genicam/Base/GCString.h:107: error: invalid use of ‘::’
/opt/pylon/include/genicam/Base/GCString.h:107: error: expected ‘;’ before ‘*’ token
/opt/pylon/include/genicam/Base/GCString.h:116: error: expected constructor, destructor, or type conversion before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:118: error: expected constructor, destructor, or type conversion before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:123: error: expected initializer before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:127: error: expected initializer before ‘&’ token
In file included from /opt/pylon/include/pylon/PylonIncludes.h:23,
                 from ParametrizeCamera.cpp:6:
/opt/pylon/include/genicam/Base/GCStringVector.h:190: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/Base/GCStringVector.h:192: error: ‘GenICam::gcstring_vector’ has not been declared
/opt/pylon/include/genicam/Base/GCStringVector.h:193: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/Base/GCStringVector.h:198: error: ‘GenICam::gcstring_vector’ has not been declared
/opt/pylon/include/genicam/Base/GCStringVector.h:199: error: expected initializer before ‘operator’
In file included from /opt/pylon/include/genicam/Base/GCBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from ParametrizeCamera.cpp:6:
/opt/pylon/include/genicam/Base/GCException.h:61: error: expected class-name before ‘{’ token
/opt/pylon/include/genicam/Base/GCException.h:175: error: expected unqualified-id before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:175: error: expected ‘,’ or ‘...’ before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:181: error: expected unqualified-id before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:181: error: expected ‘,’ or ‘...’ before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h: In member function ‘E GenICam::ExceptionReporter<E>::Report()’:
/opt/pylon/include/genicam/Base/GCException.h:177: error: ‘s’ was not declared in this scope
/opt/pylon/include/genicam/Base/GCException.h: In member function ‘E GenICam::ExceptionReporter<E>::Report()’:
/opt/pylon/include/genicam/Base/GCException.h:183: error: ‘str’ was not declared in this scope
In file included from /opt/pylon/include/genicam/Base/GCBase.h:39,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from ParametrizeCamera.cpp:6:
/opt/pylon/include/genicam/Base/GCException.h: At global scope:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::RuntimeException>’:
/opt/pylon/include/genicam/Base/GCUtilities.h:51:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::RuntimeException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::RuntimeException]’
In file included from /opt/pylon/include/genicam/GenApi/IBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/Pointer.h:37,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from ParametrizeCamera.cpp:6:
/opt/pylon/include/genicam/GenApi/Types.h:143: error: ‘gcstring_vector’ in namespace ‘GenICam’ does not name a type
In file included from /opt/pylon/include/genicam/GenApi/INode.h:39,
                 from /opt/pylon/include/genicam/GenApi/Pointer.h:38,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from ParametrizeCamera.cpp:6:
/opt/pylon/include/genicam/GenApi/Container.h:377: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/GenApi/Container.h:378: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/GenApi/Container.h:381: error: ‘value_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Container.h:384: error: ‘GenApi::node_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:385: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:390: error: ‘GenApi::node_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:391: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:396: error: ‘GenApi::value_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:397: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:402: error: ‘GenApi::value_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:403: error: expected initializer before ‘operator’
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:38,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from ParametrizeCamera.cpp:6:
/opt/pylon/include/genicam/GenApi/INode.h:53: error: ‘node_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/INode.h:101: error: ‘NodeList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/INode.h:119: error: ‘GenICam::gcstring_vector’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:39,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from ParametrizeCamera.cpp:6:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::AccessException>’:
/opt/pylon/include/genicam/GenApi/IValue.h:94:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::AccessException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::AccessException]’
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:40,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from ParametrizeCamera.cpp:6:
/opt/pylon/include/genicam/GenApi/ICategory.h:65: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ICategory.h:90: error: ‘FeatureList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:44,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from ParametrizeCamera.cpp:6:
/opt/pylon/include/genicam/GenApi/IEnumeration.h:58: error: ‘StringList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/IEnumeration.h:61: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:51,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from ParametrizeCamera.cpp:6:
/opt/pylon/include/genicam/GenApi/INodeMap.h:55: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:55,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from ParametrizeCamera.cpp:6:
/opt/pylon/include/genicam/GenApi/ISelector.h:54: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:57: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:80: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:89: error: ‘FeatureList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from ParametrizeCamera.cpp:6:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::LogicalErrorException>’:
/opt/pylon/include/genicam/GenApi/Pointer.h:101:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::LogicalErrorException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::LogicalErrorException]’
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:38,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from ParametrizeCamera.cpp:6:
/opt/pylon/include/genicam/GenApi/NodeMapRef.h:84: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:40,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from ParametrizeCamera.cpp:6:
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: ISO C++ forbids declaration of ‘istream’ with no type
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: ‘istream’ is neither function nor member function; cannot be declared friend
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: expected ‘;’ before ‘&’ token
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: ISO C++ forbids declaration of ‘ostream’ with no type
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: ‘ostream’ is neither function nor member function; cannot be declared friend
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: expected ‘;’ before ‘&’ token
/opt/pylon/include/genicam/GenApi/Persistence.h:79: error: ‘gcstring_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Persistence.h:82: error: ‘gcstring_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Persistence.h:89: error: expected initializer before ‘&’ token
ParametrizeCamera.cpp:156: error: expected `}' at end of input
make[1]: *** [ParametrizeCamera.o] Error 1
make[1]: Leaving directory `/opt/pylon/PylonSamples/ParametrizeCamera'
make[1]: Entering directory `/opt/pylon/PylonSamples/RegisterRemovalCallback'
/opt/pylon/gcc-4.2.1/build/bin/g++  -I/opt/pylon/gcc-4.2.1/build/gcc-4.2.1/include/c++/4.2.1 -I/opt/pylon/include -I/opt/pylon/include/genicam -I/opt/pylon/include -DUSE_GIGE  -c -o RegisterRemovalCallback.o RegisterRemovalCallback.cpp
In file included from /opt/pylon/include/pylon/PylonIncludes.h:22,
                 from RegisterRemovalCallback.cpp:16:
/opt/pylon/include/genicam/Base/GCString.h:34:18: error: string: No such file or directory
/opt/pylon/include/genicam/Base/GCString.h:36:20: error: iostream: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:23,
                 from RegisterRemovalCallback.cpp:16:
/opt/pylon/include/genicam/Base/GCStringVector.h:186:18: error: vector: No such file or directory
In file included from /opt/pylon/include/genicam/Base/GCBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from RegisterRemovalCallback.cpp:16:
/opt/pylon/include/genicam/Base/GCException.h:42:21: error: exception: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:43:19: error: cassert: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:44:19: error: cstdarg: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:45:19: error: sstream: No such file or directory
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:40,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from RegisterRemovalCallback.cpp:16:
/opt/pylon/include/genicam/GenApi/Persistence.h:37:16: error: list: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:61,
                 from RegisterRemovalCallback.cpp:16:
/opt/pylon/include/pylon/Device.h:27:18: error: bitset: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:22,
                 from RegisterRemovalCallback.cpp:16:
/opt/pylon/include/genicam/Base/GCString.h:107: error: ISO C++ forbids declaration of ‘string’ with no type
/opt/pylon/include/genicam/Base/GCString.h:107: error: invalid use of ‘::’
/opt/pylon/include/genicam/Base/GCString.h:107: error: expected ‘;’ before ‘*’ token
/opt/pylon/include/genicam/Base/GCString.h:116: error: expected constructor, destructor, or type conversion before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:118: error: expected constructor, destructor, or type conversion before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:123: error: expected initializer before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:127: error: expected initializer before ‘&’ token
In file included from /opt/pylon/include/pylon/PylonIncludes.h:23,
                 from RegisterRemovalCallback.cpp:16:
/opt/pylon/include/genicam/Base/GCStringVector.h:190: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/Base/GCStringVector.h:192: error: ‘GenICam::gcstring_vector’ has not been declared
/opt/pylon/include/genicam/Base/GCStringVector.h:193: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/Base/GCStringVector.h:198: error: ‘GenICam::gcstring_vector’ has not been declared
/opt/pylon/include/genicam/Base/GCStringVector.h:199: error: expected initializer before ‘operator’
In file included from /opt/pylon/include/genicam/Base/GCBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from RegisterRemovalCallback.cpp:16:
/opt/pylon/include/genicam/Base/GCException.h:61: error: expected class-name before ‘{’ token
/opt/pylon/include/genicam/Base/GCException.h:175: error: expected unqualified-id before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:175: error: expected ‘,’ or ‘...’ before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:181: error: expected unqualified-id before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:181: error: expected ‘,’ or ‘...’ before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h: In member function ‘E GenICam::ExceptionReporter<E>::Report()’:
/opt/pylon/include/genicam/Base/GCException.h:177: error: ‘s’ was not declared in this scope
/opt/pylon/include/genicam/Base/GCException.h: In member function ‘E GenICam::ExceptionReporter<E>::Report()’:
/opt/pylon/include/genicam/Base/GCException.h:183: error: ‘str’ was not declared in this scope
In file included from /opt/pylon/include/genicam/Base/GCBase.h:39,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from RegisterRemovalCallback.cpp:16:
/opt/pylon/include/genicam/Base/GCException.h: At global scope:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::RuntimeException>’:
/opt/pylon/include/genicam/Base/GCUtilities.h:51:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::RuntimeException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::RuntimeException]’
In file included from /opt/pylon/include/genicam/GenApi/IBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/Pointer.h:37,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from RegisterRemovalCallback.cpp:16:
/opt/pylon/include/genicam/GenApi/Types.h:143: error: ‘gcstring_vector’ in namespace ‘GenICam’ does not name a type
In file included from /opt/pylon/include/genicam/GenApi/INode.h:39,
                 from /opt/pylon/include/genicam/GenApi/Pointer.h:38,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from RegisterRemovalCallback.cpp:16:
/opt/pylon/include/genicam/GenApi/Container.h:377: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/GenApi/Container.h:378: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/GenApi/Container.h:381: error: ‘value_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Container.h:384: error: ‘GenApi::node_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:385: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:390: error: ‘GenApi::node_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:391: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:396: error: ‘GenApi::value_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:397: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:402: error: ‘GenApi::value_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:403: error: expected initializer before ‘operator’
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:38,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from RegisterRemovalCallback.cpp:16:
/opt/pylon/include/genicam/GenApi/INode.h:53: error: ‘node_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/INode.h:101: error: ‘NodeList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/INode.h:119: error: ‘GenICam::gcstring_vector’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:39,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from RegisterRemovalCallback.cpp:16:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::AccessException>’:
/opt/pylon/include/genicam/GenApi/IValue.h:94:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::AccessException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::AccessException]’
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:40,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from RegisterRemovalCallback.cpp:16:
/opt/pylon/include/genicam/GenApi/ICategory.h:65: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ICategory.h:90: error: ‘FeatureList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:44,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from RegisterRemovalCallback.cpp:16:
/opt/pylon/include/genicam/GenApi/IEnumeration.h:58: error: ‘StringList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/IEnumeration.h:61: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:51,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from RegisterRemovalCallback.cpp:16:
/opt/pylon/include/genicam/GenApi/INodeMap.h:55: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:55,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from RegisterRemovalCallback.cpp:16:
/opt/pylon/include/genicam/GenApi/ISelector.h:54: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:57: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:80: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:89: error: ‘FeatureList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from RegisterRemovalCallback.cpp:16:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::LogicalErrorException>’:
/opt/pylon/include/genicam/GenApi/Pointer.h:101:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::LogicalErrorException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::LogicalErrorException]’
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:38,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from RegisterRemovalCallback.cpp:16:
/opt/pylon/include/genicam/GenApi/NodeMapRef.h:84: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:40,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from RegisterRemovalCallback.cpp:16:
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: ISO C++ forbids declaration of ‘istream’ with no type
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: ‘istream’ is neither function nor member function; cannot be declared friend
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: expected ‘;’ before ‘&’ token
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: ISO C++ forbids declaration of ‘ostream’ with no type
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: ‘ostream’ is neither function nor member function; cannot be declared friend
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: expected ‘;’ before ‘&’ token
/opt/pylon/include/genicam/GenApi/Persistence.h:79: error: ‘gcstring_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Persistence.h:82: error: ‘gcstring_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Persistence.h:89: error: expected initializer before ‘&’ token
RegisterRemovalCallback.cpp:229: error: expected `}' at end of input
make[1]: *** [RegisterRemovalCallback.o] Error 1
make[1]: Leaving directory `/opt/pylon/PylonSamples/RegisterRemovalCallback'
make[1]: Entering directory `/opt/pylon/PylonSamples/UserSets'
/opt/pylon/gcc-4.2.1/build/bin/g++  -I/opt/pylon/gcc-4.2.1/build/gcc-4.2.1/include/c++/4.2.1 -I/opt/pylon/include -I/opt/pylon/include/genicam -I/opt/pylon/include -DUSE_GIGE  -c -o UserSets.o UserSets.cpp
In file included from /opt/pylon/include/pylon/PylonIncludes.h:22,
                 from UserSets.cpp:5:
/opt/pylon/include/genicam/Base/GCString.h:34:18: error: string: No such file or directory
/opt/pylon/include/genicam/Base/GCString.h:36:20: error: iostream: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:23,
                 from UserSets.cpp:5:
/opt/pylon/include/genicam/Base/GCStringVector.h:186:18: error: vector: No such file or directory
In file included from /opt/pylon/include/genicam/Base/GCBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from UserSets.cpp:5:
/opt/pylon/include/genicam/Base/GCException.h:42:21: error: exception: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:43:19: error: cassert: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:44:19: error: cstdarg: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:45:19: error: sstream: No such file or directory
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:40,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from UserSets.cpp:5:
/opt/pylon/include/genicam/GenApi/Persistence.h:37:16: error: list: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:61,
                 from UserSets.cpp:5:
/opt/pylon/include/pylon/Device.h:27:18: error: bitset: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:22,
                 from UserSets.cpp:5:
/opt/pylon/include/genicam/Base/GCString.h:107: error: ISO C++ forbids declaration of ‘string’ with no type
/opt/pylon/include/genicam/Base/GCString.h:107: error: invalid use of ‘::’
/opt/pylon/include/genicam/Base/GCString.h:107: error: expected ‘;’ before ‘*’ token
/opt/pylon/include/genicam/Base/GCString.h:116: error: expected constructor, destructor, or type conversion before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:118: error: expected constructor, destructor, or type conversion before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:123: error: expected initializer before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:127: error: expected initializer before ‘&’ token
In file included from /opt/pylon/include/pylon/PylonIncludes.h:23,
                 from UserSets.cpp:5:
/opt/pylon/include/genicam/Base/GCStringVector.h:190: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/Base/GCStringVector.h:192: error: ‘GenICam::gcstring_vector’ has not been declared
/opt/pylon/include/genicam/Base/GCStringVector.h:193: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/Base/GCStringVector.h:198: error: ‘GenICam::gcstring_vector’ has not been declared
/opt/pylon/include/genicam/Base/GCStringVector.h:199: error: expected initializer before ‘operator’
In file included from /opt/pylon/include/genicam/Base/GCBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from UserSets.cpp:5:
/opt/pylon/include/genicam/Base/GCException.h:61: error: expected class-name before ‘{’ token
/opt/pylon/include/genicam/Base/GCException.h:175: error: expected unqualified-id before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:175: error: expected ‘,’ or ‘...’ before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:181: error: expected unqualified-id before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:181: error: expected ‘,’ or ‘...’ before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h: In member function ‘E GenICam::ExceptionReporter<E>::Report()’:
/opt/pylon/include/genicam/Base/GCException.h:177: error: ‘s’ was not declared in this scope
/opt/pylon/include/genicam/Base/GCException.h: In member function ‘E GenICam::ExceptionReporter<E>::Report()’:
/opt/pylon/include/genicam/Base/GCException.h:183: error: ‘str’ was not declared in this scope
In file included from /opt/pylon/include/genicam/Base/GCBase.h:39,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from UserSets.cpp:5:
/opt/pylon/include/genicam/Base/GCException.h: At global scope:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::RuntimeException>’:
/opt/pylon/include/genicam/Base/GCUtilities.h:51:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::RuntimeException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::RuntimeException]’
In file included from /opt/pylon/include/genicam/GenApi/IBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/Pointer.h:37,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from UserSets.cpp:5:
/opt/pylon/include/genicam/GenApi/Types.h:143: error: ‘gcstring_vector’ in namespace ‘GenICam’ does not name a type
In file included from /opt/pylon/include/genicam/GenApi/INode.h:39,
                 from /opt/pylon/include/genicam/GenApi/Pointer.h:38,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from UserSets.cpp:5:
/opt/pylon/include/genicam/GenApi/Container.h:377: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/GenApi/Container.h:378: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/GenApi/Container.h:381: error: ‘value_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Container.h:384: error: ‘GenApi::node_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:385: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:390: error: ‘GenApi::node_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:391: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:396: error: ‘GenApi::value_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:397: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:402: error: ‘GenApi::value_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:403: error: expected initializer before ‘operator’
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:38,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from UserSets.cpp:5:
/opt/pylon/include/genicam/GenApi/INode.h:53: error: ‘node_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/INode.h:101: error: ‘NodeList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/INode.h:119: error: ‘GenICam::gcstring_vector’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:39,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from UserSets.cpp:5:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::AccessException>’:
/opt/pylon/include/genicam/GenApi/IValue.h:94:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::AccessException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::AccessException]’
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:40,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from UserSets.cpp:5:
/opt/pylon/include/genicam/GenApi/ICategory.h:65: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ICategory.h:90: error: ‘FeatureList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:44,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from UserSets.cpp:5:
/opt/pylon/include/genicam/GenApi/IEnumeration.h:58: error: ‘StringList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/IEnumeration.h:61: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:51,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from UserSets.cpp:5:
/opt/pylon/include/genicam/GenApi/INodeMap.h:55: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:55,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from UserSets.cpp:5:
/opt/pylon/include/genicam/GenApi/ISelector.h:54: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:57: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:80: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:89: error: ‘FeatureList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from UserSets.cpp:5:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::LogicalErrorException>’:
/opt/pylon/include/genicam/GenApi/Pointer.h:101:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::LogicalErrorException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::LogicalErrorException]’
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:38,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from UserSets.cpp:5:
/opt/pylon/include/genicam/GenApi/NodeMapRef.h:84: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:40,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from UserSets.cpp:5:
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: ISO C++ forbids declaration of ‘istream’ with no type
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: ‘istream’ is neither function nor member function; cannot be declared friend
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: expected ‘;’ before ‘&’ token
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: ISO C++ forbids declaration of ‘ostream’ with no type
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: ‘ostream’ is neither function nor member function; cannot be declared friend
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: expected ‘;’ before ‘&’ token
/opt/pylon/include/genicam/GenApi/Persistence.h:79: error: ‘gcstring_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Persistence.h:82: error: ‘gcstring_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Persistence.h:89: error: expected initializer before ‘&’ token
UserSets.cpp:120: error: expected `}' at end of input
make[1]: *** [UserSets.o] Error 1
make[1]: Leaving directory `/opt/pylon/PylonSamples/UserSets'
make[1]: Entering directory `/opt/pylon/PylonSamples/WaitEx'
/opt/pylon/gcc-4.2.1/build/bin/g++  -I/opt/pylon/gcc-4.2.1/build/gcc-4.2.1/include/c++/4.2.1 -I/opt/pylon/include -I/opt/pylon/include/genicam -I/opt/pylon/include -DUSE_GIGE  -c -o WaitEx.o WaitEx.cpp
In file included from /opt/pylon/include/pylon/PylonIncludes.h:22,
                 from WaitEx.cpp:12:
/opt/pylon/include/genicam/Base/GCString.h:34:18: error: string: No such file or directory
/opt/pylon/include/genicam/Base/GCString.h:36:20: error: iostream: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:23,
                 from WaitEx.cpp:12:
/opt/pylon/include/genicam/Base/GCStringVector.h:186:18: error: vector: No such file or directory
In file included from /opt/pylon/include/genicam/Base/GCBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from WaitEx.cpp:12:
/opt/pylon/include/genicam/Base/GCException.h:42:21: error: exception: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:43:19: error: cassert: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:44:19: error: cstdarg: No such file or directory
/opt/pylon/include/genicam/Base/GCException.h:45:19: error: sstream: No such file or directory
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:40,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from WaitEx.cpp:12:
/opt/pylon/include/genicam/GenApi/Persistence.h:37:16: error: list: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:61,
                 from WaitEx.cpp:12:
/opt/pylon/include/pylon/Device.h:27:18: error: bitset: No such file or directory
In file included from /opt/pylon/include/pylon/PylonIncludes.h:22,
                 from WaitEx.cpp:12:
/opt/pylon/include/genicam/Base/GCString.h:107: error: ISO C++ forbids declaration of ‘string’ with no type
/opt/pylon/include/genicam/Base/GCString.h:107: error: invalid use of ‘::’
/opt/pylon/include/genicam/Base/GCString.h:107: error: expected ‘;’ before ‘*’ token
/opt/pylon/include/genicam/Base/GCString.h:116: error: expected constructor, destructor, or type conversion before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:118: error: expected constructor, destructor, or type conversion before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:123: error: expected initializer before ‘&’ token
/opt/pylon/include/genicam/Base/GCString.h:127: error: expected initializer before ‘&’ token
In file included from /opt/pylon/include/pylon/PylonIncludes.h:23,
                 from WaitEx.cpp:12:
/opt/pylon/include/genicam/Base/GCStringVector.h:190: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/Base/GCStringVector.h:192: error: ‘GenICam::gcstring_vector’ has not been declared
/opt/pylon/include/genicam/Base/GCStringVector.h:193: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/Base/GCStringVector.h:198: error: ‘GenICam::gcstring_vector’ has not been declared
/opt/pylon/include/genicam/Base/GCStringVector.h:199: error: expected initializer before ‘operator’
In file included from /opt/pylon/include/genicam/Base/GCBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from WaitEx.cpp:12:
/opt/pylon/include/genicam/Base/GCException.h:61: error: expected class-name before ‘{’ token
/opt/pylon/include/genicam/Base/GCException.h:175: error: expected unqualified-id before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:175: error: expected ‘,’ or ‘...’ before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:181: error: expected unqualified-id before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h:181: error: expected ‘,’ or ‘...’ before ‘&’ token
/opt/pylon/include/genicam/Base/GCException.h: In member function ‘E GenICam::ExceptionReporter<E>::Report()’:
/opt/pylon/include/genicam/Base/GCException.h:177: error: ‘s’ was not declared in this scope
/opt/pylon/include/genicam/Base/GCException.h: In member function ‘E GenICam::ExceptionReporter<E>::Report()’:
/opt/pylon/include/genicam/Base/GCException.h:183: error: ‘str’ was not declared in this scope
In file included from /opt/pylon/include/genicam/Base/GCBase.h:39,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:34,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from WaitEx.cpp:12:
/opt/pylon/include/genicam/Base/GCException.h: At global scope:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::RuntimeException>’:
/opt/pylon/include/genicam/Base/GCUtilities.h:51:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::RuntimeException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::RuntimeException]’
In file included from /opt/pylon/include/genicam/GenApi/IBase.h:36,
                 from /opt/pylon/include/genicam/GenApi/Pointer.h:37,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from WaitEx.cpp:12:
/opt/pylon/include/genicam/GenApi/Types.h:143: error: ‘gcstring_vector’ in namespace ‘GenICam’ does not name a type
In file included from /opt/pylon/include/genicam/GenApi/INode.h:39,
                 from /opt/pylon/include/genicam/GenApi/Pointer.h:38,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from WaitEx.cpp:12:
/opt/pylon/include/genicam/GenApi/Container.h:377: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/GenApi/Container.h:378: error: expected initializer before ‘<’ token
/opt/pylon/include/genicam/GenApi/Container.h:381: error: ‘value_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Container.h:384: error: ‘GenApi::node_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:385: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:390: error: ‘GenApi::node_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:391: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:396: error: ‘GenApi::value_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:397: error: expected initializer before ‘operator’
/opt/pylon/include/genicam/GenApi/Container.h:402: error: ‘GenApi::value_vector’ has not been declared
/opt/pylon/include/genicam/GenApi/Container.h:403: error: expected initializer before ‘operator’
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:38,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from WaitEx.cpp:12:
/opt/pylon/include/genicam/GenApi/INode.h:53: error: ‘node_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/INode.h:101: error: ‘NodeList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/INode.h:119: error: ‘GenICam::gcstring_vector’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:39,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from WaitEx.cpp:12:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::AccessException>’:
/opt/pylon/include/genicam/GenApi/IValue.h:94:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::AccessException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::AccessException]’
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:40,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from WaitEx.cpp:12:
/opt/pylon/include/genicam/GenApi/ICategory.h:65: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ICategory.h:90: error: ‘FeatureList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:44,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from WaitEx.cpp:12:
/opt/pylon/include/genicam/GenApi/IEnumeration.h:58: error: ‘StringList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/IEnumeration.h:61: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:51,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from WaitEx.cpp:12:
/opt/pylon/include/genicam/GenApi/INodeMap.h:55: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/Pointer.h:55,
                 from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from WaitEx.cpp:12:
/opt/pylon/include/genicam/GenApi/ISelector.h:54: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:57: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:80: error: ‘FeatureList_t’ has not been declared
/opt/pylon/include/genicam/GenApi/ISelector.h:89: error: ‘FeatureList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:37,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from WaitEx.cpp:12:
/opt/pylon/include/genicam/Base/GCException.h: In instantiation of ‘GenICam::ExceptionReporter<GenICam::LogicalErrorException>’:
/opt/pylon/include/genicam/GenApi/Pointer.h:101:   instantiated from here
/opt/pylon/include/genicam/Base/GCException.h:181: error: ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::LogicalErrorException]’ cannot be overloaded
/opt/pylon/include/genicam/Base/GCException.h:175: error: with ‘E GenICam::ExceptionReporter<E>::Report() [with E = GenICam::LogicalErrorException]’
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:38,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from WaitEx.cpp:12:
/opt/pylon/include/genicam/GenApi/NodeMapRef.h:84: error: ‘NodeList_t’ has not been declared
In file included from /opt/pylon/include/genicam/GenApi/GenApi.h:40,
                 from /opt/pylon/include/pylon/PylonIncludes.h:32,
                 from WaitEx.cpp:12:
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: ISO C++ forbids declaration of ‘istream’ with no type
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: ‘istream’ is neither function nor member function; cannot be declared friend
/opt/pylon/include/genicam/GenApi/Persistence.h:72: error: expected ‘;’ before ‘&’ token
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: ISO C++ forbids declaration of ‘ostream’ with no type
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: ‘ostream’ is neither function nor member function; cannot be declared friend
/opt/pylon/include/genicam/GenApi/Persistence.h:75: error: expected ‘;’ before ‘&’ token
/opt/pylon/include/genicam/GenApi/Persistence.h:79: error: ‘gcstring_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Persistence.h:82: error: ‘gcstring_vector’ does not name a type
/opt/pylon/include/genicam/GenApi/Persistence.h:89: error: expected initializer before ‘&’ token
WaitEx.cpp:293: error: expected `}' at end of input
make[1]: *** [WaitEx.o] Error 1
make[1]: Leaving directory `/opt/pylon/PylonSamples/WaitEx'
make: *** [all] Error 2
[/HTML]Listed below is the list of environment variables that are set based on the manufactures suggestion:

export PYLON_ROOT=/opt/pylon    
export GENICAM_ROOT_V1_1=/opt/pylon 
export GENICAM_CACHE=$PYLON_ROOT/xml_cache
export LD_LIBRARY_PATH=$PYLON_ROOT/lib:$PYLON_ROOT/gcc-4.2.1/build/lib:$LD_LIBRARY_PATH

Also, listed below is make file used to build the sample applications

[HTML]
# Makefile for Basler pylon sample program
.PHONY            : all clean

# for 64-bit builds, set LIBDIR to lib64
LIBDIR    = lib

# the program to build
SUBDIRS            := AcquireContinuous AcquireContinuous_SoftTrigger AcquireSingleFrame \
               AcquireSingleFrame_ChunkImage AcquireSingleFrame_Gen CameraEvents \
               LookupTable ManyCamerasUnix ParametrizeCamera RegisterRemovalCallback UserSets \
               WaitEx

# Build tools and flags
CXX            :=  $(PYLON_ROOT)/gcc-4.2.1/build/bin/g++ #/usr/bin/g++

LD            :=  $(PYLON_ROOT)/gcc-4.2.1/build/bin/g++ #/usr/bin/g++

CPPFLAGS        := -I$(PYLON_ROOT)/gcc-4.2.1/build/gcc-4.2.1/include/c++/4.2.1\
                   -I$(GENICAM_ROOT_V1_1)/include -I$(GENICAM_ROOT_V1_1)/include/genicam \
               -I$(PYLON_ROOT)/include -DUSE_GIGE

CXXFLAGS        :=                #e.g., CXXFLAGS=-g -O0 for debugging

LDFLAGS            := -L$(PYLON_ROOT)/$(LIBDIR) -L$(GENICAM_ROOT_V1_1)/$(LIBDIR)-L$(PYLON_ROOT)/gcc-4.2.1/build/lib -Wl,-E
LIBS            := -lpylonbase

all clean        :
    for d in $(SUBDIRS); do $(MAKE) -C $$d \
        GENICAM_ROOT_V1_1="$(GENICAM_ROOT_V1_1)" \
        PYLON_ROOT="$(PYLON_ROOT)" \
[/HTML]

Any help would be greatly appreciated.

---

### Post by dwhitney67 on 2010-11-10
Please provide a listing of the files that are located in the following directory: /opt/pylon/gcc-4.2.1/build/gcc-4.2.1/include/c++/4.2.1

P.S.  Have you considered using the Ubuntu 10.10 native g++ compiler?

---

### Post by primary_solution on 2010-11-10
Thanks for the help.  I can't find the 'include' portion of the directory you listed.  I am open to using the native compiler (comes with 'build-essentials') I was just trying to follow the manufacture suggestion.

```

ian@testcptr:/opt/pylon/gcc-4.2.1/build/gcc-4.2.1$ ls
info  libexec  man  share

```

update:
I think you are on to something.  I had a look at the 'make' file and saw the path you noted and the include portion does not exist in the directory structure.  So, I fired off an email to the manufacture.

---

