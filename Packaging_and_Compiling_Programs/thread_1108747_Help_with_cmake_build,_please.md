---
title: "Help with cmake build, please"
date: 2009-03-28
forum: Packaging and Compiling Programs
---

### Post by bcw on 2009-03-28
Hello,

I have a project that installs a shared library, a test application for it, and a header file to be used with the shared library.   The application (library) provides an entry point for translating ink strokes into text characters.

Here is what happens when I try to install with the archive I have now (attached at the end of the message):

```
bret@aphrodite:~/lab$ tar -xzf msinkclient-0.1.0.tar.gz
bret@aphrodite:~/lab$ cd msinkclient/
bret@aphrodite:~/lab/msinkclient$ cmake src
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Configuring done
-- Generating done
-- Build files have been written to: /home/bret/lab/msinkclient
bret@aphrodite:~/lab/msinkclient$ make
Scanning dependencies of target msinkclient
[ 33%] Building C object /home/bret/lab/dist/lib/CMakeFiles/msinkclient.dir/msinkclient.c.o
/home/bret/lab/msinkclient/src/lib/msinkclient.c:20: warning: &#8216;shift_state&#8217; defined but not used
Linking C shared library libmsinkclient.so
[ 33%] Built target msinkclient
Scanning dependencies of target msinkclient_static
[ 66%] Building C object /home/bret/lab/dist/lib/CMakeFiles/msinkclient_static.dir/msinkclient.c.o
/home/bret/lab/msinkclient/src/lib/msinkclient.c:20: warning: &#8216;shift_state&#8217; defined but not used
Linking C static library libmsinkclient.a
[ 66%] Built target msinkclient_static
Scanning dependencies of target msinkclienttest
[100%] Building C object /home/bret/lab/dist/bin/CMakeFiles/msinkclienttest.dir/msinkclienttest.c.o
Linking C executable msinkclienttest
[100%] Built target msinkclienttest
bret@aphrodite:~/lab/msinkclient$ sudo make install
[ 33%] Built target msinkclient
[ 66%] Built target msinkclient_static
[100%] Built target msinkclienttest
Install the project...
-- Install configuration: ""
-- Installing: /usr/local/lib/msinkclient/libmsinkclient.so.VERSION
-- Installing: /usr/local/lib/msinkclient/libmsinkclient.so
-- Installing: /usr/local/bin/msinkclienttest
-- Removed runtime path from "/usr/local/bin/msinkclienttest"
-- Installing: /usr/local/include/msinkclient.h

```

I can't figure out how to get the resolved value of VERSION instead of the literal text.  Can anyone help, please?  I am not knowledgeable about cmake, and I have read all I can find so far - I'm misunderstanding something.

If you're willing, I'd also very much like to develop a 'make uninstall' target as well.  Much thanks if you can provide concrete tips or links about that.

Regards,
Bret

---

### Post by bcw on 2009-03-29
Running from the appropriate folder works:

```
tar -xzf msinkclient-0.1.0.tar.gz
cd msinkclient
cmake .
make
sudo make install

```

---

