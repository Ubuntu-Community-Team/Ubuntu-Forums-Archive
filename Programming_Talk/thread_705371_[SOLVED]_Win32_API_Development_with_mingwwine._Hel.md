---
title: "[SOLVED] Win32 API Development with mingw/wine. Help Please."
date: 2008-02-23
forum: Programming Talk
---

### Post by volanin on 2008-02-23
I am having a hard time with this:
How to I enable XP Button Style in Win32 API code developed using mingw?


Here is a sample code, **mbox.c**:
```
#define _WIN32_IE    0x0500
#define _WIN32_WINNT 0x0501

#include <windows.h>
#include <commctrl.h>



INT WINAPI WinMain( HINSTANCE inst, HINSTANCE prev, LPSTR cmdline, INT show )
{
    InitCommonControls( );
    MessageBox( NULL, "WinXP button style.", "Message Box", MB_OK );
    return 0;
}
```


But when I compile and run it with:
```
i586-mingw32msvc-gcc -o mbox.exe mbox.c -lcomctl32
wine ./mbox.exe
```


I only get the old ugly Win95 Button Styles.
The windows version in **winecfg** is set to Windows XP already.

Help Please!
:mad:

---

### Post by volanin on 2008-02-23
Ok, I read on the internet that you must add a manifest file in order to enable the comctl32.dll functions that allow Windows XP Theming.

The manifest file is as follows:
```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?> 
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0"> 
 <assemblyIdentity 
  version="1.0.0.0" 
  processorArchitecture="X86" 
  name="CompanyName.ProductName.mbox.exe" 
  type="win32"
 /> 
 <description>Your application description here.</description> 
 <dependency> 
  <dependentAssembly> 
   <assemblyIdentity 
    type="win32" 
    name="Microsoft.Windows.Common-Controls" 
    version="6.0.0.0" 
    processorArchitecture="X86" 
    publicKeyToken="6595b64144ccf1df" 
    language="*" 
   />
  </dependentAssembly> 
 </dependency> 
</assembly>
```


I put it in a file named **mbox.exe.manifest** that wine is supposed to read and enable the Window XP Style.
No good.

So I tried adding it as a resource:
```
#ifndef RT_MANIFEST
#define RT_MANIFEST 24
#endif

#ifndef CREATEPROCESS_MANIFEST_RESOURCE_ID
#define CREATEPROCESS_MANIFEST_RESOURCE_ID 1
#endif

CREATEPROCESS_MANIFEST_RESOURCE_ID RT_MANIFEST "mbox.exe.manifest"
```


And add it with:
```
i586-mingw32msvc-windres -o resource.o resource.rc
i586-mingw32msvc-gcc -c -o mbox.o mbox.c
i586-mingw32msvc-gcc -o mbox.exe mbox.o resource.o -lcomctl32

```


But it is still NO GOOD.
I am getting really desperate now. Anyone?
:(

---

### Post by volanin on 2008-02-23
GOT IT.

I tested the sample code in Windows, and it worked perfectly.
The problem seems to be that wine has no support for builtin WindowsXP Styles.
(And installing a WindowsXP theme does not change the buttons...)

---

