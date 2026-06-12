---
title: "IsBadReadPtr Solution"
date: 2009-06-26
forum: Programming Talk
---

### Post by wbest on 2009-06-26
Yeah, so I have some C++ files I need to convert from Windows to Linux, and I ran into IsBadReadPtr
I found this forum that has some solutions, but I'm not sure if I can sue any of them.
[http://fixunix.com/linux/337646-isbadreadptr-linux.html](http://fixunix.com/linux/337646-isbadreadptr-linux.html)
 
The exact call to it is:
if(IsBadReadPtr(fun, sizeof(LPDWORD))==false)
 
where fun is of type CML_HOL_FUNC, which I believe is of type int dur to
typedef int (*CML_HOL_FUNC)(CML_DATE date)
 
And LPDWORD is made by:
#include <stdint.h>
typedef uint_t DWORD
typedef DWORD* LPDWORD
 
Now, I of course need a Linux version of this.  Will I be able to use the write() function like in the above link?  Or is there a better solution for my particular problem?
 
I'll try to answer as many questions as I can, but I did not write the code, it is my job to port it, though.

---

