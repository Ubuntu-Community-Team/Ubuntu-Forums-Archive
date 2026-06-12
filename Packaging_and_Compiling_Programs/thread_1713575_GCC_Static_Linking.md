---
title: "GCC Static Linking"
date: 2011-03-24
forum: Packaging and Compiling Programs
---

### Post by rau on 2011-03-24
I'm still acquainting myself with Mingw-w64, and I've hit a snag trying to compile with a static library I made.

test code header:
```

#ifndef OBJECT_H_
#define OBJECT_H_

#ifdef BUILD_DLL
    #define EXPORT __declspec(dllexport)
#else
    #define EXPORT __declspec(dllimport)
#endif

class Object
{
public:
    virtual void SetString(const char* str) = 0;
    virtual void PrintString() = 0;
    virtual void Release() = 0;
};

extern "C" __stdcall EXPORT Object* CreateObject(const char* str);

#endif //OBJECT_H_

```

I can compile it fine with a shared library as follows:

```

g++ -shared -DBUILD_DLL -o libobject.dll object.cpp
g++ -o test.exe test.cpp -L. -lobject

```

but if I try to use a static library as follows:

```

g++ -DBUILD_DLL -c object.cpp
ar rcs libobject.a object.o
g++ -static -o test.exe test.cpp -L. -lobject  //note: with or without -static

```

I get a linker error: undefined refrence to '__imp_CreateObject'

What am I doing wrong here?

---

### Post by MadCow108 on 2011-03-24
I think you need to remove the __declspec(dllexport) in the static case as that will mangle the symbol names in a different way

---

### Post by JupiterV2 on 2011-03-25
To my knowledge, using declspec(dllimport/export) is only used for shared libraries. If I'm not mistaken, your error can be avoided by checking in your configure script (assuming you're using autoconf) whether you're building a shared library. If you are, then pass something like -DBUILDING_DLL_IMPORT to generate an import library.

```
#ifdef DLL_EXPORT 
#    define EXPORT __declspec(dllexport)
#else
#    ifdef BUILDING_DLL_IMPORT
#        define EXPORT __declspec(dllimport)
#    endif /* DLL_IMPORT */
# endif /* DLL_EXPORT */
```

If this this is being built as a cross-platform program, you should check if _WIN32 is defined too, because the above is not used in native linux shared/static libraries.

Again, though, if you are building a static library none of the above is needed. DLL_EXPORT is usually only passed when libtool (I'm assuming you're using that too) is trying to make a shared library.

That said, I'm a notice when porting to windows.

---

### Post by rau on 2011-04-01
My goals are to be able to write one header file that can be used on both Windows and Linux, and for that header to be suitable for use with both static and shared versions of the library, whether it be for building the library or building code dependent on the library. I also want it to be as simple and straight forward as possible. Also, the goal is to export only those functions that are a part of the public api when compiling as a shared library.

How is something like this?

```

#if defined(OBJECT_SHARED_LIBRARY)
  #if defined(_WIN32) || defined(__CYGWIN__)
    #if defined(OBJECT_BUILDING_LIBRARY)
      #define OBJECT_API __declspec(dllexport)
    #else
      #define OBJECT_API __declspec(dllimport)
    #endif
  #else
    #define OBJECT_API __attribute__ ((visibility("default")))
  #endif
#else
  #define OBJECT_API
#endif

```

---

### Post by rau on 2011-04-02
Or perhaps it it is better to create two separate header files? One for building the library and one for users of the library?

---

