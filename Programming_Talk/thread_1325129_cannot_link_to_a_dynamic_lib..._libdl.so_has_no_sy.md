---
title: "cannot link to a dynamic lib... libdl.so has no symbols ?@#!"
date: 2009-11-13
forum: Programming Talk
---

### Post by lemonsf on 2009-11-13
Greetings,

Just porting some libs to nix, and I have a problem compiling a dynamic lib... All the code has ported ok, compilation fine, but linking not so ( no punn intended! ). Any help on this would be much appreciated...

My problem is when it comes to linking a static lib that itself links to a dynamic lib... 
```

g++ main.cpp -L./ -lstaticLib -o main

```
I get the error
```

.//libstaticLib.a(staticLib.o): In function 'staticFunc(int)':
staticLib.cpp:(.text+0x16): undefined reference to 'dlopen'
staticLib.cpp:(.text+0x39): undefined reference to 'dlsym'
collect2: ld returned 1 exit status

```
which means it can't find 'dlsym' and 'dlopen'.. fair enough, so I locate the 'libdl.so' which contains these functions, but when I list the symbols...
```

nm -s /usr/lib/libdl.so
nm: libdl.so: no symbols

```
This can't be right can it? 
Why would there be the 'shell' to the dynamic lib but with nothing in it? I've tried re-installing build-essential but still the same libdl.so...

All the source that I have used, and the commands to compile are below.. In summary main ( main.cpp ) calls "staticFunc(int)" ( in staticLib.cpp which is compiled to libstaticLib.a ), which in turn calls "dynamicFunc(int)" ( in dynamicLib.cpp which is compiled to libdynamicLib.so )... Hope I haven't confused anyone yet...

The code: ( N.B This is code is cross-platform )

main.cpp
```

#include "liba.h"
#include <iostream>

int main( int argc, char** argv )
{
    int result = staticFunc( 1 );
    std::cout << "result : " << result;
    return 0;
}

```

staticLib.h
```

#ifndef STATICLIB_INCLUDE
#define STATICLIB_INCLUDE

int staticFunc( int );

#endif

```

staticLib.cpp
```

#include "staticLib.h"
#include "dynamicLib.h"

#ifdef WIN32
#include "windows.h"
#define GETFUNCTION GetProcAddress
#else
#include <dlfcn.h>
#define GETFUNCTION dlsym
#endif

typedef int (*_dynamicFunc)( int );

int staticFunc( int val )
{
#ifdef WIN32
    HINSTANCE dInst = LoadLibrary( "dynamicLib.dll" );
#else
    void* dInst = dlopen( "./libdynamicLib.so", RTLD_LAZY );
#endif

    if ( dInst )
    {
        _dynamicFunc function = 0;
        function = (_dynamicFunc) GETFUNCTION( dInst, "dyanmicFunc" );
        
        if ( function )
            return function( val );
    }
    return 0;
}

```

dynamicLib.h
```

#ifndef DYNAMICLIB_INCLUDE
#define DYNAMICLIB_INCLUDE

#ifdef WIN32
#define dllEXPORT __declspec( dllexport )
#else
#define dllEXPORT
#endif

#ifdef __cplusplus
extern "C"
{
#endif

dllEXPORT int dynamicFunc( int );

#ifdef __cplusplus
}
#endif

#endif

```

dyanmicLib.cpp
```

#include "dynamicLib.h"

#ifdef WIN32
BOOL WINAPI DllMain( HINSTANCE dllInst, DWORD reason, LPVOID reserved ) { return true; }
#endif

dllEXPORT int dynamicFunc( int value )
{
    return ++value;
}

```

to create the dynamic lib..
```

g++ -c -fPIC dynamicLib.cpp -o d.o
ld -G d.o -o libdynamicLib.so

```
which creates libdyanmicLib.so, no problems... then to create the static lib
```

g++ -c staticLib.cpp -L./ -ldynamicLib -o s.o
ar -rv libstaticLib.a s.o

```
which creates libstaticLib.a, again no problems...so to compile and link main.cpp
```

g++ main.cpp -L./ -lstaticLib -o main

```
from which I get...
```

.//libstaticLib.a(staticLib.o): In function 'staticFunc(int)':
staticLib.cpp:(.text+0x16): undefined reference to 'dlopen'
staticLib.cpp:(.text+0x39): undefined reference to 'dlsym'
collect2: ld returned 1 exit status

```

Many thanks in advance for your time, any help on this would be appricated..

---

### Post by dwhitney67 on 2009-11-13
Your link statement should appear as:
```

g++ main.cpp -L./ -lstaticLib **-ldl** -o main

```
Read the manpage for dlopen() (and the like) and the need to specify -ldl will be revealed to you.

---

### Post by lemonsf on 2009-11-13
Many thanks dwhitney67, once again you fixed my problem...it works, however linking to the libdl.so doesn't make complete sense to me, since its not main.cpp that needs to know about dlopen(), dlsym() and dlclose()... these are located in the static lib, all the main.cpp should need to know for linking is where to find the static lib.. if anything libdl.so should be linked to when compiling staticLib.cpp. I tried this but got the same error. 

This means that anyone else who uses the static library must perfom all the linking for the static library, and not just linking the static library itself. That seems a bit unintuitive, or is this by design?

Many thanks for getting me an end result though.

---

### Post by Arndt on 2009-11-13
> **lemonsf said:**
> Many thanks dwhitney67, once again you fixed my problem...it works, however linking to the libdl.so doesn't make complete sense to me, since its not main.cpp that needs to know about dlopen(), dlsym() and dlclose()... these are located in the static lib, all the main.cpp should need to know for linking is where to find the static lib.. if anything libdl.so should be linked to when compiling staticLib.cpp. I tried this but got the same error. 

This means that anyone else who uses the static library must perfom all the linking for the static library, and not just linking the static library itself. That seems a bit unintuitive, or is this by design?

Many thanks for getting me an end result though.

"Linked to when compiled" doesn't make sense. There's one linking operation, which uses all previously created .o and .a files, as well as external libraries.

You seem to want a sort of prelinked static library, with all its references resolved. That makes some sense, but it's not the way Unix linking is traditionally done. For one thing, it would mean that you couldn't make use of an updated component library without rebuilding the prelinked library. It would also make the .a files in the system a lot larger, which was an important issue back then.

---

### Post by lemonsf on 2009-11-13
> **Arndt said:**
> "Linked to when compiled" doesn't make sense.

Sorry meant to say "Linked to when built"

> **Arndt said:**
> You seem to want a sort of prelinked static library, with all its references resolved

Indeed, this is exactly what I want, as you quite rightly said, size used to be an issue, but in my case it isn't any more..

> **Arndt said:**
> For one thing, it would mean that you couldn't make use of an updated component library without rebuilding the prelinked library

So in the case from above, does this mean that if I update the dyanmic library ( which the static one links to ), I would need to rebuild the static library, does this not defy the point of having a dynamically linked library? 

I would like to keep things to be as "Traditionally Unix" as possible, but I'm beginning to get the impression that this might not work the way I want. ](*,)

Thanks for your reply Arndt.

---

### Post by lemonsf on 2009-11-13
Also, does anyone know why I had the original problem of no symbols in libdl.so?

```

nm -s /usr/lib/libdl.so
nm: libdl.so: no symbols

```

Thanks for you replies

---

### Post by dwhitney67 on 2009-11-13
> **lemonsf said:**
> Also, does anyone know why I had the original problem of no symbols in libdl.so?

```

nm -s /usr/lib/libdl.so
nm: libdl.so: no symbols

```

Thanks for you replies

The file has been stripped of its symbols.  This is typical (procedure) after building the C library.  Well, at least it was when I built a Linux OS based on CLFS (Cross-Compiled Linux From Scratch).

---

### Post by Arndt on 2009-11-13
> **lemonsf said:**
> Sorry meant to say "Linked to when built"



Indeed, this is exactly what I want, as you quite rightly said, size used to be an issue, but in my case it isn't any more..



So in the case from above, does this mean that if I update the dyanmic library ( which the static one links to ), I would need to rebuild the static library, does this not defy the point of having a dynamically linked library? 

I would like to keep things to be as "Traditionally Unix" as possible, but I'm beginning to get the impression that this might not work the way I want. ](*,)

Thanks for your reply Arndt.

One thing you can do, but I don't know if it's a good idea, is to add the .o files from libdl.a into your .a file. Then the final linking shouldn't have to mention -ldl.

---

### Post by lemonsf on 2009-11-13
> **dwhitney67 said:**
> The file has been stripped of its symbols.  This is typical (procedure) after building the C library.  Well, at least it was when I built a Linux OS based on CLFS (Cross-Compiled Linux From Scratch).
Of course... they are 'release' versions. Many thanks

---

### Post by lemonsf on 2009-11-13
> **Arndt said:**
> One thing you can do, but I don't know if it's a good idea, is to add the .o files from libdl.a into your .a file. Then the final linking shouldn't have to mention -ldl.
Thats a nice cheeky idea, but unfortunately it didn't work well at all. I think with a bit more effort I could get something to work but then I am definately limiting usage of the dynamic library (copying the dlopen.o means if/when dlopen is updated, I would still need to update my static libs)... thanks for the suggestion though... I think I'm trying to turn a circle into a square... unix is unix, and rather than trying to change the way that I want it to work, I just need to work with it. It's not a major problem, and like I said before would like to keep it 'semi' unix traditional..

Thanks for your help dwhitney67 and Arndt, its been a nice learning curve ( and will continue to do so ), I think this thread is solved now..

Many thanks for the replies.

---

### Post by dwhitney67 on 2009-11-13
You can always attempt the following, which I believe Arndt was alluding to:
```

g++ main.cpp -L./ -lstaticLib **-static** -ldl -o main

```
This will include the '.o' modules of the libdl.a within your executable, thus making it fully portable.  Bear in mind though, that your executable will grow bigger with this option vs. just loading the library during run-time.

---

