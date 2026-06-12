---
title: "Problem installing webcam-server"
date: 2012-02-11
forum: Packaging and Compiling Programs
---

### Post by loganbell45 on 2012-02-11
Hi, I'm trying to install webcam-server, and after configuring it, when trying t use 'make' I get this:
$ make
Making all in src
make[1]: Entering directory `/home/logan/Downloads/webcam_server-0.50/src'
gcc  -g -O2  -o webcam_server -ljpeg -lpthread camera.o client.o filters.o grabber.o imgqueue.o jdatabuf.o image.o unpalette.o version.o watchdog.o webcam_server.o  -lpthread 
filters.o: In function `image2jpeg':
/home/logan/Downloads/webcam_server-0.50/src/filters.c:51: undefined reference to `jpeg_std_error'
/home/logan/Downloads/webcam_server-0.50/src/filters.c:52: undefined reference to `jpeg_CreateCompress'
/home/logan/Downloads/webcam_server-0.50/src/filters.c:58: undefined reference to `jpeg_set_defaults'
/home/logan/Downloads/webcam_server-0.50/src/filters.c:59: undefined reference to `jpeg_set_quality'
/home/logan/Downloads/webcam_server-0.50/src/filters.c:60: undefined reference to `jpeg_start_compress'
/home/logan/Downloads/webcam_server-0.50/src/filters.c:62: undefined reference to `jpeg_write_scanlines'
/home/logan/Downloads/webcam_server-0.50/src/filters.c:63: undefined reference to `jpeg_finish_compress'
/home/logan/Downloads/webcam_server-0.50/src/filters.c:77: undefined reference to `jpeg_destroy_compress'
/home/logan/Downloads/webcam_server-0.50/src/filters.c:71: undefined reference to `jpeg_destroy_compress'
collect2: ld returned 1 exit status
make[1]: *** [webcam_server] Error 1
make[1]: Leaving directory `/home/logan/Downloads/webcam_server-0.50/src'
make: *** [all-recursive] Error 1

apparently the collect2: ld returned 1 exit status is some kind of problem with a linker, but I'm not yet adept enough at ubuntu to work out what's going wrong. 
Thanks if yo can help.

---

### Post by luismontes on 2012-09-03
Old thread, but just in case anybody still cares, the order of the libraries matter. Put -ljpeg bit after all the .o files and it will compile

---

### Post by luismontes on 2012-09-03
And, in order to run it on a Ubuntu 12.04 system, you have to use something like:
```

LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so ./webcam_server -l my_log_file -d /dev/video0

```

---

