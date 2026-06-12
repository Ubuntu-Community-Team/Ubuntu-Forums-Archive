---
title: "C++ building binary, other systems and libraries"
date: 2013-03-18
forum: Programming Talk
---

### Post by slimjimmrtim on 2013-03-18
I am a C++ newbie. I have successfully made a project in Eclipse. But now I would like to use the program on another linux system and I don't know how to accomplish this.

I developed on an Ubuntu 13.04 (beta) 64bit system and would like to run the program on an Ubuntu 12.04 32bit system.

Eclipse creates a Debug folder which contains an executable file which I can execute from the terminal and works on the system which I developed on, but does it does not work on the other system. I just realized at very least the 64/32bit issue could cause this. Figuring out how to compile for another architecture is something I need to do.

The project makes use of a couple libraries which I am sure is complicating the matter too. I assume I will have to install these libraries on the other system? I would like to do as little of that as possible, but it isn't a huge deal. 

I could compile on the other system, but this would not be ideal, nor would it teach me how to share binaries with other people in the future.

My includes for the project look like

```
#include <iostream>
#include "./includes/twitcurl.h"
#include <cstring>
#include <Poco/Util/AbstractConfiguration.h>
#include <Poco/Util/XMLConfiguration.h>
#include <Poco/RegularExpression.h>
#include <Poco/String.h>
#include <stdlib.h>
#include <Poco/Net/HTTPClientSession.h>
#include <Poco/Net/HTTPRequest.h>
#include <Poco/Net/HTTPResponse.h>
#include <Poco/Net/StreamSocket.h>
#include <Poco/Net/SocketAddress.h>
#include <Poco/Net/SocketStream.h>
#include <Poco/StreamCopier.h>
#include <Poco/Path.h>
#include <Poco/URI.h>
#include <Poco/Exception.h>
#include <Poco/Net/HTTPStreamFactory.h>
#include <vector>
#include <sstream>
#include <fstream>
#include <Poco/Format.h>
#include <tidy/tidy.h>
#include <tidy/buffio.h>
#include <libxml++/libxml++.h>
#include <locale.h>
#include <string>
```

and I get two interesting blocks in the Eclipse console when I build the project

```
12:10:21 **** Incremental Build of configuration Debug for project ki ****
make all 
Building file: ../src/ki.cpp
Invoking: GCC C++ Compiler
g++ -I/usr/local/include/Poco -I/usr/include/c++/4.7/ -I/usr/include/c++/4.7.2/ -I/usr/include/glib-2.0 
-I/usr/lib/x86_64-linux-gnu/sigc++-2.0/include -I/usr/include/sigc++-2.0 
-I/usr/lib/x86_64-linux-gnu/glibmm-2.4/include -I/usr/lib/x86_64-linux-gnu/glib-2.0/include 
-I/usr/include/glibmm-2.4 -I/usr/include/libxml2 -I/usr/lib/libxml++-2.6/include -I/usr/include/libxml++-2.6 
-I/usr/local/lib -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"src/ki.d" -MT"src/ki.d" -o "src/ki.o" "../src/ki.cpp"
```

and

```
Finished building: ../src/ki.cpp
 
Building target: ki
Invoking: GCC C++ Linker
g++ -L/usr/local/lib/ -L/usr/include/libxml++-2.6/ -L/usr/include/ -L/usr/lib/ -L/usr/local/include/Poco/ 
-o "ki"  ./src/ki.o   -ltwitcurl -lglibmm-2.4 -lxml2 -lxml++-2.6 -ltidy -lPocoNet -lcurl -lPocoUtil -lPocoFoundation
Finished building target: ki
```

between the two blocks are some warnings which don't seem to be relevant.

Input on how to achieve my goals is appreciated. Thank you for your time.

---

### Post by nvteighen on 2013-03-21
Nope. Running a 64-bit program on a 32-bit machine is bound to fail. Why? Well, because a 64-bits machine has 8-bytes long memory addresses, while a 32-bit one has 4-bytes long addresses... Therefore, how would a 32-bit machine understand where 0x0123456789ABCDEF is if its address space ends at 0xFFFFFFFF?

In our GNU/Linux world, the best practice is to always distribute sources, not binaries and compile in-place... unless you are willing to mantain different packages for each and every architecture out there, but such workload is better handled by a full-fledged distro with a packaging system like Debian, Red Hat, etc. Just distribute sources with a sane Makefile (or perhaps autoconf...) and tell people which libraries and development files they have to install (those are the so-called "build dependencies" or "build-deps").

---

