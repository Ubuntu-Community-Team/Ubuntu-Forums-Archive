---
title: "libdecodeqr0, A rookie programmer's efforts and confusion with public libraries"
date: 2009-10-07
forum: Programming Talk
---

### Post by Druke on 2009-10-07
**To the point:**
[INDENT]
libdecodeqr-examples sample programs do not work, I think I understand why, but not how to fix it, nor how this is supposed to work in the debian package system.

I'm not sure if it is a "bug" because I would need someone to reproduce it 8-[ .
[/INDENT]

**The longer part**
Google has a barcode logo today, and it made me interested in barcode programming. My friend mentioned japanese "qr code", and I was off on a storm of [wikipedia]("http://en.wikipedia.org/wiki/QR_Code") and [barely translated api pages]("http://trac.koka-in.org/libdecodeqr")

I installed libdecodeqr0 and libdecodeqr-dev from synaptic and began working on the [sample application on the api page]("http://trac.koka-in.org/libdecodeqr/browser/trunk/src/sample/simple/simpletest.cpp?rev=latest").

From there I had issues getting started because I wasn't sure how to include everything. The api site has:

```

#include <stdio.h>
#include <highgui.h>
#include "../../libdecodeqr/decodeqr.h"

```

naturally that had to change.

Highgui is part fo the opencv library, so "whereis opencv" showed me where stuff is. Sure enough, highgui was in there.

did the same for decodeqr.h

```

#include <stdio>
#include <opencv/highgui.h>
#include "/usr/include/decodeqr.h"

```

compiling now returned:

```
~$ g++ ./qrcode.cpp
./qrcode.cpp:1:17: error: stdio: No such file or directory
In file included from ./qrcode.cpp:3:
/usr/include/decodeqr.h:17:16: error: cv.h: No such file or directory

```

my gut reaction was to go into the decdeqr.h and change it's includes. But this turned into a slippery slop with more and more stuff breaking. So I reinstalled the package from syanptic and tried it's example programs.

```

$ libdecodeqr-simpletest
OpenCV ERROR: Null pointer (null filename)
	in function cvLoadImage, loadsave.cpp(380)
Terminating the application...
	called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...
	called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...
	called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...
	called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...
	called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...
	called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...
	called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...
	called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...
	called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...


```

so apparently this app includes opencv in other areas as well.

my options are now.. try and alter the program to not use openCV at all, or ask for advise.

So here I am.

Things I'd like to do
[LIST]
[*]Learn how one is **supposed** to include open libraries into programs.
[*]write a program to read in a qr code
[*]fix the libencodeqr-exmaples stuff on my end
[*]know how to make a patch to give to launchpad (I think I know where to find documentation on this)
[/LIST]

naturally: thanks in advance.

---

### Post by MadCow108 on 2009-10-07
when you install it over a package you should use the angle brackets to indicate the default include path (/usr/include mostly) and just navigate relative to that

If it doesn't work then use compiler include paths to tell the compiler to look for the stuff with -I/folder/with/headers

you should not edit the header includes of the installed package

the error with the example app seems to be that it expects a filename: OpenCV ERROR: Null pointer (**null filename**)

---

### Post by Druke on 2009-10-07
alright, so then in the case of my base program,

```

#include <stdio.h>
#include <opencv/highgui.h>
#include <decodeqr.h>

int main(int argc,char *argv[])
{
	return 0;
}

```

compiling returns:

```

$ g++ ./qrcode.cpp
In file included from ./qrcode.cpp:3:
/usr/include/decodeqr.h:17:16: error: cv.h: No such file or directory

```

from that error, I am assuming that there is an error in the way decodeqr.h calls cv.h 

(it in fact calls it via <cv.h>, which I think needs to be <opencv/cv.h>)

is that assumption incorrect?

---

### Post by MadCow108 on 2009-10-07
if the header is there then yes
but don't edit the header! Add the opencv folder with the headers to the include search path of the compiler

maybe there also is also pkg-config information available
check pkt-config --list-all to see if the library appears there

in that case compiling goes like this:
g++ `pkg-config --libs --cflags *name*` file.cpp

pkg-config is a program which prints all compile flags and libraries necessary to compile a program (as long as the package provides this information)

---

### Post by Druke on 2009-10-07
```
$ g++ `pkg-config --libs --cflags opencv` ./qrcode.cpp
```

made it able to compile! Thanks a bunch.

I imagine the pkg-config method is used to set up the same library on different directory structures. basically created a uniform method for using third party libraries...

---

