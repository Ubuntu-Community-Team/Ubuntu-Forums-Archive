---
title: "gprof does not work with libc_p libraries in ubuntu?"
date: 2006-11-12
forum: Programming Talk
---

### Post by achillez on 2006-11-12
Hi all, 

I've tried some experiments with the latest Ubuntu and I can't seem to properly link in the gprof'd standard libraries. The standard gprof'd libraries aren't linked in when I do: 

gcc -g -pg -o testme testme.c  

Then when I try to link them in I get: 

gcc -g -pg -o testme testme.c -lc_p 
> testme
> Floating point exception (core dumped) 

Then when I try to remove standard libs, I get a link error (can't find _Unwind_resume): 

gcc -g -pg -o testme testme.c -nodefaultlibs -lc_p -lgcc

Any help here would be appreciated

---

### Post by cmacdonell on 2007-03-27
Hi,

I have this same error, we're you ever able to resolve it?

Thanks,
Cam

---

### Post by hod139 on 2007-03-27
You should check our callgrind.  It is in my opinion superior to g_prof.

---

