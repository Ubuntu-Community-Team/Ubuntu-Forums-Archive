---
title: "Anyone's got experience with C (stdio) I/O?"
date: 2011-02-19
forum: Programming Talk
---

### Post by t1497f35 on 2011-02-19
Hi,
I'm doing a C++ app but I'd need to use <stdio.h> (for all file I/O operations). From what I read around it looks like to achieve better throughput with the <stdio.h> I need to use an intermediate buffer, something that afaik the C++ iostream takes care automatically of. Is it all true? If so, any tips on how I'd use/create a buffer for using it with <stdio.h> for raw file operations (like copying)?
I can't call external apps to do the job cause I need fine grained control from my app, like being able to pause the copying at any time.

---

### Post by worksofcraft on 2011-02-19
> **t1497f35 said:**
> Hi,
I'm doing a C++ app but I'd need to use <stdio.h> (for all file I/O operations). From what I read around it looks like to achieve better throughput with the <stdio.h> I need to use an intermediate buffer, something that afaik the C++ iostream takes care automatically of. Is it all true? If so, any tips on how I'd use/create a buffer for using it with <stdio.h> for raw file operations (like copying)?
I can't call external apps to do the job cause I need fine grained control from my app, like being able to pause the copying at any time.

IMO all the buffering is already done for us at the C stdio level and all that C++ streams add to this is loads of I/O text formating capabilities.

When accessing files I got the impression that doing low level block I/O with open, read and write directly is more efficient than going through the buffers but I never tested it.

Meanwhile  [here is an article about buffering on stdio]("http://www.pixelbeat.org/programming/stdio_buffering/") that may help.

---

### Post by MadCow108 on 2011-02-19
all C/C++ streams are buffered unless you tell them not to.
You can also change between line buffered and block buffered.

C
[http://www.cs.utah.edu/dept/old/texinfo/glibc-manual-0.02/library_11.html#SEC163](http://www.cs.utah.edu/dept/old/texinfo/glibc-manual-0.02/library_11.html#SEC163)

C++
[http://www.cplusplus.com/reference/iostream/streambuf/](http://www.cplusplus.com/reference/iostream/streambuf/)

---

### Post by t1497f35 on 2011-02-19
Thanks a lot both of you! Now going to read those articles!

---

### Post by rnerwein on 2011-02-19
> **t1497f35 said:**
> Hi,
I'm doing a C++ app but I'd need to use <stdio.h> (for all file I/O operations). From what I read around it looks like to achieve better throughput with the <stdio.h> I need to use an intermediate buffer, something that afaik the C++ iostream takes care automatically of. Is it all true? If so, any tips on how I'd use/create a buffer for using it with <stdio.h> for raw file operations (like copying)?
I can't call external apps to do the job cause I need fine grained control from my app, like being able to pause the copying at any time.

hello
first i'm only programing in C. but i think the following way is possible in C++.
have a look at " man -k async "
you will find there calls like "aio_read, aio_write .......". 
but it's no so easy to handle.

ciao

---

