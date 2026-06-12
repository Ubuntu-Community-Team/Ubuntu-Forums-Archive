---
title: "[SOLVED] gettimeofday on Windows?"
date: 2008-01-11
forum: Programming Talk
---

### Post by Vadi on 2008-01-11
Hi all, 

I'm doing some experimentation with time on a simple C program. I got the Linux version to work okay with the help of gettimeofday, localtime. But on windows, I found that the timeval structure exists in winsock2.h, which doesn't have a gettimeofday..

I searched around some, but I'm not familiar with programming resources for Windows. Can anyone help me out / point me in the right direction?

I essentially want to be able to tell the current system time in hours, minutes, seconds, and miliseconds.

---

### Post by #Reistlehr- on 2008-01-11
Only thing i can suggest is create an fsock to udp://localhost:13 to connect to the time server on your machine.

---

### Post by Vadi on 2008-01-11
How efficient would that me? I'd need to check the time many times per second at times.

---

### Post by Wybiral on 2008-01-11
I'm fairly certain windows has it's own way of doing this, unfortunately I'm not a Window programmer so I can't help. You might try a Windows-specific forum for people who can probably help more.

---

### Post by aks44 on 2008-01-11
The daytime service is NOT enabled on Windows by default. So I seriously doubt about the usefulness of that approach.

A good resource for the Win32 API is [http://msdn.microsoft.com](http://msdn.microsoft.com)

And FWIW Google yields very relevant results when it comes to Windows equivalents of gettimeofday()...

---

### Post by Vadi on 2008-01-14
Here's how I did it in the end:

#include <windows.h>

SYSTEMTIME st;
GetSystemTime(&st);

Then you can use st.wHour, st.wMinute, st.wSecond, and st.wMilliseconds to retrieve the values (it has days, months in it too but I don't need them).

---

### Post by onetechguy on 2009-10-29
Even though this thread was marked as solved, the solution provide was not proper (i mean not complete), so for benefit of other I would like to point to complete solution [http://www.cpp-programming.net/c-tidbits/gettimeofday-function-for-windows/](http://www.cpp-programming.net/c-tidbits/gettimeofday-function-for-windows/)

---

