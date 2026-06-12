---
title: "V4L2 - example won't compile"
date: 2007-05-15
forum: Programming Talk
---

### Post by jonface on 2007-05-15
I've been trying to compile the example code for V4L2 capturing but it just won't seem to work.

This is the url: [http://v4l2spec.bytesex.org/v4l2spec/capture.c](http://v4l2spec.bytesex.org/v4l2spec/capture.c)

I've got everything needed as far as I know to compile. The error is:

```

jonface@x64:~/Desktop$ gcc -o cap capture.c
In file included from capture.c:25:
/usr/include/linux/videodev2.h:552: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘v4l2_std_id’
/usr/include/linux/videodev2.h:635: error: expected specifier-qualifier-list before ‘v4l2_std_id’
/usr/include/linux/videodev2.h:653: error: expected specifier-qualifier-list before ‘v4l2_std_id’
/usr/include/linux/videodev2.h:690: error: expected specifier-qualifier-list before ‘v4l2_std_id’

```

If I try this:

```

jonface@x64:~/Desktop$ gcc -I /usr/src/linux-headers-2.6.17-11/include/asm-i386/ -o cap capture.c
In file included from /usr/src/linux-headers-2.6.17-11/include/asm-i386/fcntl.h:1,
                 from capture.c:14:
/usr/include/asm-generic/fcntl.h:117: error: expected specifier-qualifier-list before ‘off_t’
/usr/include/asm-generic/fcntl.h:140: error: expected specifier-qualifier-list before ‘loff_t’
In file included from capture.c:25:
/usr/include/linux/videodev2.h:552: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘v4l2_std_id’
/usr/include/linux/videodev2.h:635: error: expected specifier-qualifier-list before ‘v4l2_std_id’
/usr/include/linux/videodev2.h:653: error: expected specifier-qualifier-list before ‘v4l2_std_id’
/usr/include/linux/videodev2.h:690: error: expected specifier-qualifier-list before ‘v4l2_std_id’
capture.c: In function ‘errno_exit’:
capture.c:50: error: ‘errno’ undeclared (first use in this function)
capture.c:50: error: (Each undeclared identifier is reported only once
capture.c:50: error: for each function it appears in.)
capture.c:50: warning: implicit declaration of function ‘strerror’
capture.c:50: warning: format ‘%s’ expects type ‘char *’, but argument 5 has type ‘int’
capture.c: In function ‘xioctl’:
capture.c:63: error: ‘errno’ undeclared (first use in this function)
capture.c: In function ‘read_frame’:
capture.c:83: warning: implicit declaration of function ‘read’
capture.c:84: error: ‘errno’ undeclared (first use in this function)
capture.c:103: warning: implicit declaration of function ‘memset’
capture.c:103: warning: incompatible implicit declaration of built-in function ‘memset’
capture.c: In function ‘mainloop’:
capture.c:194: error: ‘errno’ undeclared (first use in this function)
capture.c: In function ‘start_capturing’:
capture.c:249: warning: incompatible implicit declaration of built-in function ‘memset’
capture.c:270: warning: incompatible implicit declaration of built-in function ‘memset’
capture.c: In function ‘init_mmap’:
capture.c:340: warning: incompatible implicit declaration of built-in function ‘memset’
capture.c:347: error: ‘errno’ undeclared (first use in this function)
capture.c: In function ‘init_userp’:
capture.c:399: warning: incompatible implicit declaration of built-in function ‘memset’
capture.c:406: error: ‘errno’ undeclared (first use in this function)
capture.c: In function ‘init_device’:
capture.c:443: error: ‘errno’ undeclared (first use in this function)
capture.c:483: warning: incompatible implicit declaration of built-in function ‘memset’
capture.c: In function ‘close_device’:
capture.c:545: warning: implicit declaration of function ‘close’
capture.c: In function ‘open_device’:
capture.c:558: error: ‘errno’ undeclared (first use in this function)
capture.c:558: warning: format ‘%s’ expects type ‘char *’, but argument 5 has type ‘int’
capture.c:567: warning: implicit declaration of function ‘open’
capture.c:571: warning: format ‘%s’ expects type ‘char *’, but argument 5 has type ‘int’

```

I'm really not sure what is going on but I would be interested to hear if anyone else can get it to compile. V4L is working as far as I know (webcam is working).

Thanks.

---

### Post by mjbeam on 2007-05-15
It compiled for me.

---

### Post by jonface on 2007-05-16
Is there anything you can suggest I try?

---

### Post by jonface on 2007-05-19
Solved.

had pedantic-errors and others in a gcc alias. Doh. Works fine without.

---

### Post by taryneast on 2008-08-15
Hi, I'm re-dredging up this thread as I've just hit the same problem.

I'm currently trying to install ffmpeg for a system we're developing, and it seems to use v4l2

When I try to make on ffmpeg, it comes up with errors quite similar to what is reported in the thread above.

Unfortunately I can't find "-pedantic-errors" anywhere where I might be passing in a gcc-flag (and I grepped for it on my home directory just in case).

Anyone have any clues as to where I might start looking for a solution?

Thanks in advance,
Taryn

[Edit: looks like the following ilnk fixes it: 
[http://osdir.com/ml/kde.devel.kstars/2006-04/msg00033.html](http://osdir.com/ml/kde.devel.kstars/2006-04/msg00033.html) ]

---

