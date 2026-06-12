---
title: "undefined reference while compile libgphoto2"
date: 2016-12-14
forum: New to Ubuntu
---

### Post by leonhongkong on 2016-12-14
Hi. My question is about libgphoto2 in gphoto2 from [https://github.com/gphoto/libgphoto2/tree/master/examples](https://github.com/gphoto/libgphoto2/tree/master/examples)


I try to compile "libgphoto2/examples/lunkwill-canon-capture.c" (basically all .c file in libgphoto2/example show same error)

gcc -Wall -o TESTOUTPUT -lgphoto2 lunkwill-canon-capture.c (as libgphoto2 manual suggest)

I got error 

```
/tmp/ccg65O2b.o: In function `wait_event_and_download':
sample-trigger-capture.c:(.text+0xad): undefined reference to `gp_camera_wait_for_event'
sample-trigger-capture.c:(.text+0x371): undefined reference to `gp_camera_file_read'
sample-trigger-capture.c:(.text+0x57b): undefined reference to `gp_camera_file_delete'
/tmp/ccg65O2b.o: In function `main':
sample-trigger-capture.c:(.text+0x607): undefined reference to `sample_create_context'
sample-trigger-capture.c:(.text+0x64c): undefined reference to `gp_log_add_func'
sample-trigger-capture.c:(.text+0x658): undefined reference to `gp_camera_new'
sample-trigger-capture.c:(.text+0x66b): undefined reference to `gp_camera_init'
sample-trigger-capture.c:(.text+0x6db): undefined reference to `gp_camera_trigger_capture'
sample-trigger-capture.c:(.text+0x799): undefined reference to `gp_camera_exit'
collect2: error: ld returned 1 exit status
```

What did I do wrong?
best regards

---

### Post by spjackson on 2016-12-14
Try moving the library to the end of the command, i.e.
```

gcc -Wall -o TESTOUTPUT sample-trigger-capture.c -lgphoto2

```

---

### Post by leonhongkong on 2016-12-14
thanks spjackson. but still got error.

> /usr/bin/ld: /tmp/ccb8QcxX.o: undefined reference to symbol 'gp_log_add_func@@LIBGPHOTO2_5_0'
//usr/lib/x86_64-linux-gnu/libgphoto2_port.so.12: error adding symbols: DSO missing from command line
collect2: error: ld returned 1 exit status

---

### Post by spjackson on 2016-12-14
> **leonhongkong said:**
> thanks spjackson. but still got error.
```

/usr/bin/ld: /tmp/ccb8QcxX.o: undefined reference to symbol 'gp_log_add_func@@LIBGPHOTO2_5_0'
//usr/lib/x86_64-linux-gnu/libgphoto2_port.so.12: error adding symbols: DSO missing from command line
collect2: error: ld returned 1 exit status

```



It's not a library I am familiar with, but that error suggests that you need
```

gcc -Wall -o TESTOUTPUT sample-trigger-capture.c -lgphoto2 -lgphoto2_port


```

---

### Post by leonhongkong on 2016-12-14
thank. i missed -lgphoto2_port. It work now

---

