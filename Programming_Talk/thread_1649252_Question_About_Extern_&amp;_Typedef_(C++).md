---
title: "Question About Extern &amp; Typedef (C++)"
date: 2010-12-19
forum: Programming Talk
---

### Post by nova47 on 2010-12-19
I was perusing another forum and I came across some interesting code and I was wondering exactly what it means.

[PHP]

extern "C" BOOL WINAPI EnableEUDC(BOOL fEnableEUDC);

typedef BOOL (WINAPI *LPFN_ISWOW64PROCESS) (HANDLE, PBOOL);
LPFN_ISWOW64PROCESS fnIsWow64Process;

[/PHP]

I'm giving myself a crash course in Visual C++ as I go but I was wondering exactly what these two lines do? I understand that extern says that a variable is defined somewhere else in a program. However, I'm used to it being in the format "extern [data type] [variable name]". Typedef I'm similarly used to it being in the format "typedef [data type] [name]". Are all of these unusal names such as fnIsWow64Process defined in Windows.h?

---

### Post by worksofcraft on 2010-12-20
> **nova47 said:**
> I was perusing another forum and I came across some interesting code and I was wondering exactly what it means.

[PHP]

extern "C" BOOL WINAPI EnableEUDC(BOOL fEnableEUDC);

typedef BOOL (WINAPI *LPFN_ISWOW64PROCESS) (HANDLE, PBOOL);
LPFN_ISWOW64PROCESS fnIsWow64Process;

[/PHP]

I'm giving myself a crash course in Visual C++ as I go but I was wondering exactly what these two lines do? I understand that extern says that a variable is defined somewhere else in a program. However, I'm used to it being in the format "extern [data type] [variable name]". Typedef I'm similarly used to it being in the format "typedef [data type] [name]". Are all of these unusal names such as fnIsWow64Process defined in Windows.h?

Not to put too fine a point on it, Microsoft Visual C code is infested with macros. Luckily they do stick to the convention of writing macro names in all upper case.

You see for many years companies like Watcom and Borland and Symantec all produced fully fledged C++ compilers for the Windows platform while Microsoft labored under the misconception that poly morphism would be best served with macros a load of macros.

So today there is still a lot of the legacy malarkey about because the VC and the MFC library was what the industry wanted... apparently. :P

---

### Post by Lord DEA on 2010-12-20
The "extern C" part means that the function is defined somewhere else, and is to be called following the C calling convention, and thus, this "C" tells the C++ compiler to use this function as a pure C one.

---

### Post by MadCow108 on 2010-12-20
and the typedef is a shortcut name for a function pointer, similar to normal typedefs (e.g. typedef int myint_t)

the function takes a handle and a pbool (probably pointer to bool) and returns a bool
and it uses stdcall calling convention (the WINAPI macro)
LPFN_ISWOW64PROCESS is the name of the typedef

this saves you writting the whole signature when you need a specific function pointer, instead you just need the typedef name see e.g. the line below

---

### Post by matt_symes on 2010-12-20
Hi

```
extern "C" BOOL WINAPI EnableEUDC(BOOL fEnableEUDC); 
```

This is declaring a function that is defined outside the current unit.

```
typedef BOOL (WINAPI *LPFN_ISWOW64PROCESS) (HANDLE, PBOOL); 
```

This is type defining a pointer to a function. 

```
LPFN_ISWOW64PROCESS fnIsWow64Process;
``` 

This is declaring an instance of that function pointer.

Kind regards

---

### Post by nvteighen on 2010-12-20
What is worse than C++ code?
Legacy C++ code... :P

**extern "C" {}** is a device to shut C++ name mangling off when using a C interface. Otherwise, the compiler will happily mangle the names defined by the C header... and when the linker steps in, it won't be able to correlate the mangled names with the unmangled ones in the C library.

---

