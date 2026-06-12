---
title: "[C++]  error: ‘0’ cannot be used as a function"
date: 2009-07-27
forum: Programming Talk
---

### Post by wbest on 2009-07-27
So, I'm maintaining some code, and I'm trying to get it to copile.
But I keep getting the same error:
 error: ‘0’ cannot be used as a function

This is about the line:
```
  XDebugOutput("SP (MASTER_SLAVE: via - %s): %s - Exists: %s\n",  
      bMasterSP ? "master" : "slave",SPFullName().data(), Exists() ? "true" : "false");
```

I'll get the error even if I write it like this:
 ```
 XDebugOutput("TEST %d", 1);
```

Or even simply this:
```
  XDebugOutput("TEST");
```

The code for XDebugOutput() looks like this:
```
CORE_API void _SYSNAME_SPACE_::XDebugOutput(const char* format, ...) 
{ 
  char        tmp[8192];     // a big one 
  va_list     args; 
     
  va_start(args, format); 
  int code = _vsnprintf(tmp, sizeof(tmp), format, args); 
  va_end(args); 
   
  if (code   == -1) 
    sprintf(tmp, "Too big to fit in error string!"); 
 
  printf("%s", tmp); 
 
#ifdef WIN32 
  ::OutputDebugString(tmp); 
#endif 
}
```

Do you all have any ideas on what is wrong?

---

### Post by wbest on 2009-07-27
Never mind, found the error.

---

