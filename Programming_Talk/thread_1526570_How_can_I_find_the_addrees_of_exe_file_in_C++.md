---
title: "How can I find the addrees of exe file in C++?"
date: 2010-07-08
forum: Programming Talk
---

### Post by bahador.saket on 2010-07-08
Dear all

I am going the get the address of my .exe files in windows , but unfortunately I can not.
Also I am using Code::Block. 
I want a part of code that return the address of my exe file.


Regards,
Bahador Saket

---

### Post by dwhitney67 on 2010-07-08
Can you please elaborate a little further what you mean by "address"?  Do you mean the directory (folder) location?

---

### Post by johnl on 2010-07-08
Check out [GetModuleFileName](http://msdn.microsoft.com/en-us/library/ms683197%28VS.85%29.aspx):


```

#include <windows.h>

// ...
TCHAR szExe[512];
DWORD dwLen;

dwLen = GetModuleFileName(NULL, szExe, sizeof(szExe));

if (dwLen == 0) {
   // error: check GetLastError()
} else if (dwLen == sizeof(szExe)) {
   // check GetLastError() for ERROR_INSUFFICIENT_BUFFER
   // result might have been truncated
} else {
   // success, exe now contains the path and name of your
   // executable
}

```

---

