---
title: "Compiling C++ classes into an so"
date: 2008-10-16
forum: Packaging and Compiling Programs
---

### Post by gmclachl on 2008-10-16
I am trying to compile a class I wrote into an .so but I can't seem to manage to get it to compile. 

The class is straightforward and is basically just a skeleton as I am playing about 

CurlWrapper.hpp

[PHP]#include <iostream>
#include <curl/curl.h>
#ifndef CURLWRAPPER_HPP_INCLUDED
#define CURLWRAPPER_HPP_INCLUDED


class CurlWrapper {

  private:
  CURL* curl;

  public:
  CurlWrapper();


};
#endif // CURLWRAPPER_HPP_INCLUDED

[/PHP]

CurlWrapper.cpp 

[PHP]#include "CurlWrapper.hpp"

using namespace std;

CurlWrapper::CurlWrapper() {

    int t = 5;
  cout << "T is: " << t;
}[/PHP]

and a simple main 
main.cpp 

[PHP]#include "CurlWrapper.hpp"

int main() {
 CurlWrapper wrapper;
 return 1;
}[/PHP]

I compile the so with the following lines in a makefile
[PHP]
CPP=g++
DEBUG=-g

CFLAGS = -Wall -fPIC  -c $$(pkg-config --cflags libcurl)
LDFLAGS =  $$(pkg-config --libs libcurl)

Debug:  CurlWrapper.cpp
        $(CPP) $(DEBUG) CurlWrapper.cpp -o CurlWrapper.o $(CFLAGS)
        $(CPP) -shared -o libCurlWrapper.so CurlWrapper.o $(LDFLAGS)[/PHP]

This all compiles fine but when I set my library path and try to compile the main method with 

[PHP]g++ main.cpp -o main[/PHP]

I get 
```

/tmp/ccnjWH4C.o: In function `main':
main.cpp:(.text+0x74): undefined reference to `CurlWrapper::CurlWrapper()'
collect2: ld returned 1 exit status
```

I have been happily compiling shared objects for c, but haven't had much exposure to c++ and shared objects. 

G

---

### Post by snova on 2008-10-16
It looks like you forgot to link the library. Try this instead:

```
g++ main.cpp -o main -lCurlWrapper
```

---

### Post by gmclachl on 2008-10-16
Hi, thanks for the reply, when I try that i get 

/usr/bin/ld: cannot find -lCurlWrapper
collect2: ld returned 1 exit status

However I thought adding the header would give it the class interface and setting the LD_LIBRARY_PATH would allow linking at runtime, rather than compile time?

*EDIT*
I was having a bit of a no brainer with above, but I got it working using the following
g++  main.cpp -o main -L. -lcw 

** I renamed the so to cw.so

---

