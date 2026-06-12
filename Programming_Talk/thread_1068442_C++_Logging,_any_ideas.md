---
title: "C++ Logging, any ideas?"
date: 2009-02-12
forum: Programming Talk
---

### Post by gvanto on 2009-02-12
I was wondering what people reckon a good way of logging in C++ would be?

Coming from a java background, I very much like log4j's system:
- it handles file output (and sizing) automatically
- very configurable
- easy to install and use in eclipse

Now, I've come across two loggers for C++ which seem
to be the C++ version of log4j: log4cxx (by apache) and log4cpp (by someone else: [http://log4cpp.sourceforge.net/](http://log4cpp.sourceforge.net/)[^] )

OK, so first attempt at getting log4cxx working in Eclipse (running on kubuntu) was not fruitful:
The apache website, nor anywwhere else has much info on getting log4cxx up and running in eclipse.
(after installing log4cxx via "sudo aptitude install liblog4cxx9c2a" and including the header files in my c++ project in eclipse, it says it cant find the header files... i've searched and cant find them either !)

I would so love to use log4cxx since it was built by Apache and probably works really well but I really dont want to waste hours
again trying to get it to work in Eclipse (or anywwhere else for that matter). Same with log4cpp

IF anyone knows of a good logging library / class which handles (log)file creation automatically and is easily used within eclipse (or a good tutorial showing how log4cxx can actually be installed and used), it would be much appreciated !!!!

gvanto
c++ logging newbie

---

### Post by eye208 on 2009-02-13
> **gvanto said:**
> OK, so first attempt at getting log4cxx working in Eclipse (running on kubuntu) was not fruitful:
The apache website, nor anywwhere else has much info on getting log4cxx up and running in eclipse.
(after installing log4cxx via "sudo aptitude install liblog4cxx9c2a" and including the header files in my c++ project in eclipse, it says it cant find the header files... i've searched and cant find them either !)
You forgot to install the dev package: liblog4cxx9-dev

---

### Post by gvanto on 2009-02-15
hey thanks alot eye208,

OK I've installed the lib package and now the header files are found, however my program still does not compile! Get a reference error as shown below (this is after following the [example on Apache's website]("http://logging.apache.org/log4cxx/index.html") exactly: 

> 
/*
 * testmain.cpp
 *
 *  Created on: 15/02/2009
 *      Author: pacific
 */

#include <iostream>
#include <cstdlib>
#include <stdio.h>
#include <string>
#include <stdlib.h>

#include "log4cxx/logger.h"
#include "log4cxx/basicconfigurator.h"
#include "log4cxx/helpers/exception.h"

using namespace log4cxx;
using namespace log4cxx::helpers;
using namespace std;

LoggerPtr   m_logger(Logger::getLogger("myApp"));
// this gives error
//undefined reference to `log4cxx::Logger::getLogger(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'

#define DO_MAIN 1
#ifdef DO_MAIN
int main(int argc, char *argv[]) {
	int rc = EXIT_SUCCESS;

	try {
		//Set up simple config that logs on console:
		BasicConfigurator::configure(); //call to static member

		LOG4CXX_INFO(m_logger, "entering appl" );
		cout << "testing " << endl;
		LOG4CXX_INFO(m_logger, "exiting appl" );

	}
	catch(Exception&) {
		rc = EXIT_FAILURE;
	}


	return 0;
}


#endif



Output: (Compiler)
> 
Building target: SocketClientServer
Invoking: GCC C++ Linker
g++  -o"SocketClientServer"  ./src/ClientSocket.o ./src/ServerSocket.o ./src/Socket.o ./src/main_SocketClientServer.o ./src/testmain.o   
./src/testmain.o: In function `__static_initialization_and_destruction_0':
/home/pacific/workspace/SocketClientServer/Debug/../src/testmain.cpp:22: undefined reference to `log4cxx::Logger::getLogger(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
./src/testmain.o: In function `main':
/home/pacific/workspace/SocketClientServer/Debug/../src/testmain.cpp:31: undefined reference to `log4cxx::BasicConfigurator::configure()'
/home/pacific/workspace/SocketClientServer/Debug/../src/testmain.cpp:33: undefined reference to `log4cxx::Logger::isInfoEnabled() const'
/home/pacific/workspace/SocketClientServer/Debug/../src/testmain.cpp:33: undefined reference to `log4cxx::Level::INFO'
/home/pacific/workspace/SocketClientServer/Debug/../src/testmain.cpp:33: undefined reference to `log4cxx::Logger::forcedLog(log4cxx::helpers::ObjectPtrT<log4cxx::Level> const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, char const*, int)'
/home/pacific/workspace/SocketClientServer/Debug/../src/testmain.cpp:35: undefined reference to `log4cxx::Logger::isInfoEnabled() const'
/home/pacific/workspace/SocketClientServer/Debug/../src/testmain.cpp:35: undefined reference to `log4cxx::Level::INFO'
/home/pacific/workspace/SocketClientServer/Debug/../src/testmain.cpp:35: undefined reference to `log4cxx::Logger::forcedLog(log4cxx::helpers::ObjectPtrT<log4cxx::Level> const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, char const*, int)'
collect2: ld returned 1 exit status
make: *** [SocketClientServer] Error 1




help would be much appreciated!!
gvanto
unhappy c++ logger

---

### Post by Zugzwang on 2009-02-15
> **gvanto said:**
> help would be much appreciated!!
gvanto
unhappy c++ logger

You did not tell the linker to link to that library. Simply including the .h files is not enough! Search for "undefined reference" errors in this forum to get fixing hints.

---

### Post by dwhitney67 on 2009-02-15
I saw this thread the other day, and I ignored it because I did not have a clue what the OP was asking.  Upon seeing the example code, now I gather the OP is merely trying to use a message logger for his application, perhaps as a debugger tool.

Is this correct?  If so, I may have a trivial logger that the OP can use.  Please let me know if you would like for me to post some code.

---

### Post by gvanto on 2009-02-15
Thanks Zugzwang, will see what I can  find on this.

Whitney thanks yeah would be great to see the logger you've got - does it manage file output?

btw: what is OP?

cheers,
gvanto

---

### Post by dwhitney67 on 2009-02-15
OP = Original Poster or Original Post, depending on the context.

What do you mean by "managing file output"?

---

### Post by openuser on 2009-09-30
Have you tried linking to the library files?

You need to link your program to the liblog4cxx's shared object files..

It is usually done during compilation using the following command
g++ yoursources.cpp -L{/path/to/library} -l{name_of_the_library}


In eclipse, check to make sure that your project is set up properly to link the log4cxx libraries upon build

---

