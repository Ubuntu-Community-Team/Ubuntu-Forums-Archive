---
title: "How to use the libiconv with a C program?"
date: 2006-11-07
forum: Programming Talk
---

### Post by mesh2005 on 2006-11-07
I want to write a simple program in C that reads a file line by line and converts each line to UTF-8. The problem is I read the line in char buffer[256] and the iconv functions needs input and output buffers of the type char ** . I tried to cast but I always get segmentation fault. Could you please help?
Thank you

---

### Post by marekdef on 2006-11-07
There is long example here.
[http://www.gnu.org/software/libc/manual/html_node/iconv-Examples.html](http://www.gnu.org/software/libc/manual/html_node/iconv-Examples.html)

You simply need to pass pointer to input buffer (which is also a pointer that's why **)

&input should be ok

---

