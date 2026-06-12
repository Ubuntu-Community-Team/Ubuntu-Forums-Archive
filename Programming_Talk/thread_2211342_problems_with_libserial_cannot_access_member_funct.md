---
title: "problems with libserial: cannot access member functions"
date: 2014-03-15
forum: Programming Talk
---

### Post by thisisbasil on 2014-03-15
I am trying to play around with LibSerial. I built and installed the package, but I am having issues accessing any SerialStream member functions
  e.g. the following code (ls_ex.cpp) fails:
  [HTML]#include <SerialStream.h>
#include <iostream>
#include <string>
#include <cstring>
#include <cstdlib>
#include <cstdio>
#include <cerrno>
using namespace std;
using namespace LibSerial;

int main(int count, char* parms[])
{
    if (count != 2)
        exit(1);

    //open port
    string fname = parms[1];
    SerialStream port(fname);
    cout << port.isOpen() << endl;
    port.Close();

    return 0;
}  [/HTML]I have tried compiling it in the following ways:

  [HTML]g++ -o ls_ex ls_ex.cpp /usr/local/lib/libserial.a /usr/local/lib/libserial.so
g++ -o ls_ex ls_ex.cpp -lserial -L/usr/local/lib/
g++ -o ls_ex ls_ex.cpp -static -lserial -L/usr/local/lib/[/HTML]  But, when I compile, I get the following error:

  [HTML]ls_ex.cpp: In function ‘int main(int, char**)’:    ls_ex.cpp:45:15: error: ‘class LibSerial::SerialStream’ has no member named ‘isOpen’

  [/HTML]
I assume I am compiling it wrong because its easy enough to look at  the code and see that isOpen() is indeed public. Also, why am I even  able to instantiate SerialStream just fine but the compiler blows up  when I try to call *any* member function?

---

### Post by steeldriver on 2014-03-15
The standard /usr/include/SerialStream.h appears to have IsOpen (upper case I)

```

$ grep -i isopen /usr/include/SerialStream.h
            const bool IsOpen() const ;
        SerialStream::IsOpen() const {

```

If your local version defines isOpen (lower case i) then maybe the problem is that it is finding the system header file  - in which case you need an include directive to find the local header file e.g.

```

g++ -o ls_ex **-I/usr/local/include** ls_ex.cpp  -L/usr/local/lib -lserial

```

---

### Post by thisisbasil on 2014-03-15
Yeah, so I'll just crawl into a hole and die now. Haven't had that big of a brain fart since freshman year, which was many moons ago.  Thanks for looking out though. This library should work for usb port communications too right?

---

