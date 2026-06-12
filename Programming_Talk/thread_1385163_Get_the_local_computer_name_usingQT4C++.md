---
title: "Get the local computer name usingQT4C++"
date: 2010-01-19
forum: Programming Talk
---

### Post by DiegoTc on 2010-01-19
Hi
I was wondering if someone knows how to get the user name of the computer using QT4c++
I found something, but it will on work on windows, and it for c++,not using the QT4 functions
```

#include <windows.h>
#include <string>
#include <iostream.h>

string GetLocalComputerName() { 
  TCHAR chrComputerName[MAX_COMPUTERNAME_LENGTH + 1]; 
  string strRetVal; 
  DWORD dwBufferSize = MAX_COMPUTERNAME_LENGTH + 1; 
  
  if(GetComputerName(chrComputerName,&dwBufferSize)) { 
    // We got the name, set the return value. 
    strRetVal = chrComputerName; 
  } else { 
    // Failed to get the name, call GetLastError here to get 
    // the error code. 
    strRetVal = ""; 
  } 

  return(strRetVal); 
}

```

I supposed there is a way in QT4c++ in where you can get the user name that will work for linux and windows

---

### Post by lloyd_b on 2010-01-19
IIRC, the getenv() function works correctly on both Windows and Linux.  In the case of Linux, your login sets the USER and USERNAME environment variables correctly.

You might see if Windows follows this convention, and if it does you have an easy solution.

Lloyd B.

---

### Post by lisati on 2010-01-19
> **lloyd_b said:**
> IIRC, the getenv() function works correctly on both Windows and Linux.  In the case of Linux, your login sets the USER and USERNAME environment variables correctly.

You might see if Windows follows this convention, and if it does you have an easy solution.

Lloyd B.

I have seen an equivalent in Windows, and have actually done something similar, but have lost the source code...... if memory serves correctly it wasn't through the getenv() function. Sorry I couldn't be of more help.

---

### Post by johnl on 2010-01-19
Check **man gethostname**.


```

NAME
       gethostname, sethostname - get/set hostname

SYNOPSIS
       #include <unistd.h>

       int gethostname(char *name, size_t len);
DESCRIPTION
       gethostname() returns the null-terminated  hostname  in  the  character
       array  name,  which  has a length of len bytes.  If the null-terminated
       hostname is too large to fit, then the name is truncated, and no  error
       is  returned  (but  see  NOTES  below).  POSIX.1-2001 says that if such
       truncation occurs, then it is unspecified whether the  returned  buffer
       includes a terminating null byte.

RETURN VALUE
       On  success,  zero is returned.  On error, -1 is returned, and errno is
       set appropriately.


```

---

### Post by paultag on 2010-01-24
getenv() will do fine for what you need it to do.

If you want to hack even more, set up a pipe to "whoami" and read that back.

The only issue with this is that anyone can set their envvar to something other then their username ( if it is a security app ). In the case of a secure app, one might read the user ID, and lookup against the passwd file.

Cheers Diego, you rock!

Paul

---

