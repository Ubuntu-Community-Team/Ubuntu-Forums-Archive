---
title: "compiling issue with Intrepid"
date: 2009-03-24
forum: Programming Talk
---

### Post by shahin on 2009-03-24
Greetings-
   I get he following error:
/usr/include/bits/fcntl2.h:51: error: call to ‘__open_missing_mode’ declared with attribute error: open with O_CREAT in second argument needs 3 arguments
Please let me know if I should post more of the output.  I see others have had similar issue when I do an online search, but the fix is unclear.  Someone suggested to do "apt-get intall root", and I did. But that did not fix the issue.

---

### Post by dwhitney67 on 2009-03-25
It would be helpful if you posted some code; it is not typical (nor is it possible) for one to include fcntl2.h directly in their code.  Usually fcntl.h is included, and with the appropriate preprocessor flags enabled, the fcntl2.h file is included.

From fcntl.h:
```

...
/* Define some inlines helping to catch common problems.  */
#if __USE_FORTIFY_LEVEL > 0 && defined __extern_always_inline \
    && defined __va_arg_pack_len
# include <bits/fcntl2.h>
#endif
...

```

If you do not have the C library header files on your system, then you would need to obtain them using:
```

sudo apt-get install build-essential

```

-----------

EDIT

I re-read the OP again, and looking over the code in fcntl2.h, I see the issue.  When calling open() with the O_CREAT option, the file mode needs to be provided.  It's been a while since I have used open(), but I believe the usage is something like:
```

int fd = open("somePath", O_CREAT, 0644);   // create file "somePath" w/ rw-r--r-- permissions

```

---

### Post by shahin on 2009-03-25
Thanks for the message.  What I am trying to do is to compile a copy of snort.  I did the apt-get install build-essential, seems I do have everything I should.  I have snort-2.8.3.2 and pcre-7.8.  pcre compilation goes well.  snort is never done completely.  I noticed the error when I do "make" and only posted that section.  I'll be glad to provide any other evidence required.

---

### Post by shahin on 2009-03-27
Can you see if you can compile Snort on your machine?  Are you running Intrepid?

---

