---
title: "[SOLVED] [CPP] Unable to find shared library at runtime."
date: 2008-10-25
forum: Programming Talk
---

### Post by sillv0r on 2008-10-25
Hi ya,

I'm attempting to write a tiny test program that uses apache's log4cxx library.

* I've compiled and 'installed' the library/dependencies and log4cxx.so appears to be in the directory /usr/local/lib.

* I wrote a small main.cpp file given below:
```

#include <log4cxx/basicconfigurator.h>
#include <log4cxx/log4cxx.h>

int main()
{
    log4cxx::BasicConfigurator::configure();
    log4cxx::LoggerPtr log(log4cxx::Logger::getLogger("main"));

    logger->error("Hello, World!");

    return EXIT_SUCCESS;
}

```

I compiled main.cpp as following:
```

g++ main.cpp -llog4cxx

```

g++ completes and generates an a.out file as expected.  Now, when I run the program it gives an error stating: "./a.out: error while loading shared libraries: liblog4cxx.so.10; cannot open shared object file: No such file or directory."


Obviously it's not finding the shared library. This could be to the fact that the library is located in /usr/local/lib as opposed to /usr/lib.

I've tried creating a link to the file from /usr/lib to /usr/local/lib without success, and this wouldn't have been a good solution anyways.

* What do I need to do to specify a directory where shared libraries can be found by the os loader?

Or am I missing how this whole shared library idea works?  (I'm still a noob.)


note: I'm using Ubuntu 8.04  If any additional information is needed please ask.

Any information is greatly appreciated.

---

### Post by nvteighen on 2008-10-25
This may make you laugh, but you have to tell the system you installed a new library by typing:

```

sudo ldconfig

```

(or alternatively, rebooting the system)

---

### Post by sillv0r on 2008-10-25
Nice.  That's what it was.

I've always seen that command issued after upgrading packages using apt-get.  Just never realized what it did.

Thanks a bunch!

---

