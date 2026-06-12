---
title: "[SOLVED] 64 bit 7.10 compiled code segfaults in: &amp;quot;strlen () from /lib/libc.so.6&amp;quot;"
date: 2008-03-20
forum: Packaging and Compiling Programs
---

### Post by firebush on 2008-03-20
I'm getting a segfault when I compile and run the following code (it should simply print the ip address related to that unsigned long, which is 192.0.0.131):

------------------------snip----------------------------
#include <stdio.h>

int
main(void) 
{
    printf("addr: %s\n", inet_ntoa((unsigned long)2197815488 ));

    return 0;
}
------------------------pins----------------------------

I compiled this with the following (with the above content in a file named temp.c):
$ cc -o temp temp.c
$ ./temp 
Segmentation fault (core dumped)

When I compile it with the gdb flag and run "bt" after the seg fault I get the following back trace:


------------------------snip----------------------------
$ gcc -g -o temp_gdb temp.c 
$ gdb temp_gdb 
(gdb) run
Starting program: /tmp/temp_gdb 

Program received signal SIGSEGV, Segmentation fault.
0x00002b63d4dc8b50 in strlen () from /lib/libc.so.6
(gdb) bt
#0  0x00002b63d4dc8b50 in strlen () from /lib/libc.so.6
#1  0x00002b63d4d9725a in vfprintf () from /lib/libc.so.6
#2  0x00002b63d4d9d31a in printf () from /lib/libc.so.6
#3  0x000000000040050c in main () at temp.c:6
------------------------pins----------------------------

As the subject of this thread suggests, I'm doing this on a 64 bit version of 7.10.  My friend has a 32 bit version and does not see this issue.  That may not be my issue.  Perhaps I have something misconfigured.  Any suggestions what might be causing this?

My version of libc6 is 2.6.1-1ubuntu10, which is the latest version currently available.  

If anyone has the above described specifications (64 bit 7.10, with the above latest libc6), and does not get that segfault, I would appreciate that information as well.

Thanks in advance for any help offered!

---

### Post by geraldm on 2008-03-22
Well, the 32-bit compiler returns:
ntoa.c:6: warning: format '%s' expects type 'char *', but argument 2 has type 'int'
It does return the value you suggested, but it is sloppy lucky, as the warning indicates, as it returns a char pointer to a uint32_t.

You may chase the information in the headers, eventually altering your code to eliminate the accurate WARNING.  In 32-bit, this goes through arpa/inet.h netinet/in.h
so find equivalent headers for 64-bit.

Gerald

---

### Post by firebush on 2008-03-24
Thanks, geraldm!  I needed to include:
#include <arpa/inet.h>

With that included, the above code worked fine printing:
addr: 192.0.0.131

---

### Post by sandeepy on 2009-05-28
thanks geraldm !

---

