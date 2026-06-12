---
title: "Trying to build c++ program with boost libraries"
date: 2008-09-13
forum: Packaging and Compiling Programs
---

### Post by thelamb on 2008-09-13
I was hoping someone could help me out with boost libraries, I'm trying a simple example from djj.com:

```

#include <boost/thread/thread.hpp>
#include <iostream>

void hello()
{
  std::cout <<
    "Hello world, I'm a thread!"
    << std::endl;
}

int main(int argc, char* argv[])
{
  boost::thread thrd(&hello);
  thrd.join();
  return 0;
}

```

I can get this running if I install the pre-compiled boost package, but it is outdated(version 1.34 and the latest is 1.36).

So I downloaded version 1.36 and followed the documentation(found here: [http://www.boost.org/doc/libs/1_36_0/more/getting_started/unix-variants.html#prepare-to-use-a-boost-library-binary](http://www.boost.org/doc/libs/1_36_0/more/getting_started/unix-variants.html#prepare-to-use-a-boost-library-binary) )

I did everything in section 5.1:
```
$ ./configure --prefix=/home/thelamb/boost --with-libraries=thread
$ make install
``` 

Now the compiler needs to know where to find the 'boost/thread/thread.cpp' from the #include so I make a symbolic link in '/usr/include' that goes to the newly made '/home/thelamb/boost/include/boost_1_36_0/boost'

This seems to work, the compiler does not complain that it cannot find thread.cpp, instead it sais: Undefined reference boost::join.

It says this because we need to link the compiler to the boost library.

When I installed boost via the package manager all I had to do was include the flag -lboost_thread and it worked(because the boost lib files are installed in /usr/lib then, but they are in /home/thelamb/boost/lib now).

So, all I can think of is I need to give the flag: -L/home/thelamb/boost/lib -lboost_thread  and it should work?
I'm telling the compiler where to look for the libs with the -L and I tell it to load boost_thread libs with the -l option.

But it seems to fail:
```
g++ masterserver.cpp -o masterserver -L/home/thelamb/boost/lib -lboost_thread
/usr/bin/ld: cannot find -lboost_thread
collect2: ld returned 1 exit status

```

Does anybody have a clue why? 

Thanks in advance.

EDIT:

Right, someone just helped me on IRC:
Instead of the -lboost_thread option I used -lboost_thread-gcc42-mt-1_36

It compiled then but when I ran it gave:
```
./masterserver: error while loading shared libraries: libboost_thread-gcc42-mt-1_36.so.1.36.0: cannot open shared object file: No such file or directory
```

So I created a symbolic link in /usr/lib to goes to this missing file in /home/thelamb/boost/lib and it worked.

I don't know if this solution is the most elegant.. if anyone has a better solution I'm all ears.

---

### Post by FooBarWidget on 2008-09-13
Your resulting binary must know where to locate libboost_thread-gcc-mt-something.so. There are multiple ways to achieve that:

1. By setting the LD_LIBRARY_PATH environment variable before running the binary. It must be point to your Boost lib path.
2. By compiling your binary with the -Wl,-rpath,/path-to-boost-lib option. This will embed the search path /path-to-boost-lib into the binary, so that upon running it, your system will automatically look in that folder for Boost as well.

---

