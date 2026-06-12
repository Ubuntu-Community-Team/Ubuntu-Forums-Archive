---
title: "getaddrinfo_a windows equivalence"
date: 2017-12-25
forum: Programming Talk
---

### Post by chuchi on 2017-12-25
Hi everyone!


I have to implement a client socket connection application. This application receives only one parameter : the maximum timeout for connect/read operations. I was using gethostbyname, but this function is not reentrant in Linux and the application is expected to be run in a multi thread environment. 


Then I read gethostbyname is obsolete and I have to use getaddrinfo, but this call might block for an unspecified amount of time, and I can't tell getaddrinfo to stay blocked for a specific timeout. Then  I found getaddrinfo_a, which can accept a timeout...


But is there a getaddrinfo_a equivalence in Windows? 


If there is not, I can stick with gethostbyname only in Windows... But the documentation about gethostbyname does not say anything about reentrancy..


[https://msdn.microsoft.com/en-us/library/windows/desktop/ms738524(v=vs.85).aspx](https://msdn.microsoft.com/en-us/library/windows/desktop/ms738524(v=vs.85).aspx)


Any suggestions?? 


Thanks a lot!!

---

