---
title: "Undefined reference to dlopen, dlsym, dlerror, dlclose"
date: 2011-11-02
forum: Packaging and Compiling Programs
---

### Post by kr0n1x on 2011-11-02
I'm trying to compile mjpg-streamer from sources, but I'm getting these errors:
```
pasqoo@5742zg:~/mjpg-streamer/mjpg-streamer$ make USE_LIBV4L2=true clean all
make -C plugins/input_uvc clean
make[1]: ingresso nella directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/input_uvc"
rm -f *.a *.o core *~ *.so *.lo
make[1]: uscita dalla directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/input_uvc"
make -C plugins/input_testpicture clean
make[1]: ingresso nella directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/input_testpicture"
rm -f *.a *.o core *~ *.so *.lo
make[1]: uscita dalla directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/input_testpicture"
make -C plugins/output_file clean
make[1]: ingresso nella directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/output_file"
rm -f *.a *.o core *~ *.so *.lo
make[1]: uscita dalla directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/output_file"
make -C plugins/output_http clean
make[1]: ingresso nella directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/output_http"
rm -f *.a *.o core *~ *.so *.lo
make[1]: uscita dalla directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/output_http"
make -C plugins/output_udp clean
make[1]: ingresso nella directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/output_udp"
rm -f *.a *.o core *~ *.so *.lo
make[1]: uscita dalla directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/output_udp"
make -C plugins/output_autofocus clean
make[1]: ingresso nella directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/output_autofocus"
rm -f *.a *.o core *~ *.so *.lo
make[1]: uscita dalla directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/output_autofocus"
make -C plugins/input_gspcav1 clean
make[1]: ingresso nella directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/input_gspcav1"
rm -f *.a *.o core *~ *.so *.lo
make[1]: uscita dalla directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/input_gspcav1"
make -C plugins/output_viewer clean
make[1]: ingresso nella directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/output_viewer"
rm -f *.a *.o core *~ *.so *.lo
make[1]: uscita dalla directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/output_viewer"
make -C plugins/input_control clean
make[1]: ingresso nella directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/input_control"
rm -f *.a *.o core *~ *.so *.lo
make[1]: uscita dalla directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/input_control"
make -C plugins/output_rtsp clean
make[1]: ingresso nella directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/output_rtsp"
rm -f *.a *.o core *~ *.so *.lo
make[1]: uscita dalla directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/output_rtsp"
rm -f *.a *.o mjpg_streamer core *~ *.so *.lo
gcc -D'SVN_REV="3:148"' -O2 -DLINUX -D_GNU_SOURCE -Wall    -c -o mjpg_streamer.o mjpg_streamer.c
gcc -D'SVN_REV="3:148"' -O2 -DLINUX -D_GNU_SOURCE -Wall    -c -o utils.o utils.c
gcc -D'SVN_REV="3:148"' -O2 -DLINUX -D_GNU_SOURCE -Wall  -lpthread -ldl mjpg_streamer.o utils.o -o mjpg_streamer
mjpg_streamer.o: In function `signal_handler':
mjpg_streamer.c:(.text+0x17f): undefined reference to `dlclose'
mjpg_streamer.c:(.text+0x1af): undefined reference to `dlclose'
mjpg_streamer.o: In function `main':
mjpg_streamer.c:(.text.startup+0x260): undefined reference to `dlopen'
mjpg_streamer.c:(.text.startup+0x27c): undefined reference to `dlsym'
mjpg_streamer.c:(.text.startup+0x299): undefined reference to `dlsym'
mjpg_streamer.c:(.text.startup+0x2b6): undefined reference to `dlsym'
mjpg_streamer.c:(.text.startup+0x2d3): undefined reference to `dlsym'
mjpg_streamer.c:(.text.startup+0x418): undefined reference to `dlopen'
mjpg_streamer.c:(.text.startup+0x435): undefined reference to `dlsym'
mjpg_streamer.c:(.text.startup+0x453): undefined reference to `dlsym'
mjpg_streamer.c:(.text.startup+0x471): undefined reference to `dlsym'
mjpg_streamer.c:(.text.startup+0x48f): undefined reference to `dlsym'
mjpg_streamer.c:(.text.startup+0x6ab): undefined reference to `dlerror'
mjpg_streamer.c:(.text.startup+0x805): undefined reference to `dlerror'
mjpg_streamer.c:(.text.startup+0x9e1): undefined reference to `dlerror'
collect2: ld returned 1 exit status
make: *** [mjpg_streamer] Errore 1
pasqoo@5742zg:~/mjpg-streamer/mjpg-streamer$
```

libc6 and libc6-dev are installed, I'm on Xubuntu 11.10 64 bit.

Any help? :)

Thanks!

---

### Post by SevenMachines on 2011-11-02
You need the libs to be linked after the objects. In the Makefile change,
```
$(APP_BINARY): mjpg_streamer.c mjpg_streamer.h mjpg_streamer.o utils.c utils.h utils.o
  $(CC) $(CFLAGS) $(LFLAGS) $(OBJECTS) -o $(APP_BINARY)
  chmod 755 $(APP_BINARY)

```to
```
$(APP_BINARY): mjpg_streamer.c mjpg_streamer.h mjpg_streamer.o utils.c utils.h utils.o
  $(CC) $(CFLAGS) $(OBJECTS) $(LFLAGS) -o $(APP_BINARY)
  chmod 755 $(APP_BINARY)

```

[EDIT] This is due to to --as-needed being passed by default to gcc nowadays, theres many unresolved symbol threads in the forum for further explanation
[http://wiki.debian.org/ToolChain/DSOLinking#Onlylinkwithneededlibraries](http://wiki.debian.org/ToolChain/DSOLinking#Onlylinkwithneededlibraries)

---

### Post by kr0n1x on 2011-11-02
That resolved the problem, thanks.

But the make still doesn't finish, maybe I should ask to their own forum but I try here:

```
pasqoo@5742zg:~/mjpg-streamer/mjpg-streamer$ make USE_LIBV4L2=true clean all
make -C plugins/input_uvc clean
make[1]: ingresso nella directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/input_uvc"
rm -f *.a *.o core *~ *.so *.lo
make[1]: uscita dalla directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/input_uvc"
make -C plugins/input_testpicture clean
make[1]: ingresso nella directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/input_testpicture"
rm -f *.a *.o core *~ *.so *.lo
make[1]: uscita dalla directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/input_testpicture"
make -C plugins/output_file clean
make[1]: ingresso nella directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/output_file"
rm -f *.a *.o core *~ *.so *.lo
make[1]: uscita dalla directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/output_file"
make -C plugins/output_http clean
make[1]: ingresso nella directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/output_http"
rm -f *.a *.o core *~ *.so *.lo
make[1]: uscita dalla directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/output_http"
make -C plugins/output_udp clean
make[1]: ingresso nella directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/output_udp"
rm -f *.a *.o core *~ *.so *.lo
make[1]: uscita dalla directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/output_udp"
make -C plugins/output_autofocus clean
make[1]: ingresso nella directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/output_autofocus"
rm -f *.a *.o core *~ *.so *.lo
make[1]: uscita dalla directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/output_autofocus"
make -C plugins/input_gspcav1 clean
make[1]: ingresso nella directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/input_gspcav1"
rm -f *.a *.o core *~ *.so *.lo
make[1]: uscita dalla directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/input_gspcav1"
make -C plugins/output_viewer clean
make[1]: ingresso nella directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/output_viewer"
rm -f *.a *.o core *~ *.so *.lo
make[1]: uscita dalla directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/output_viewer"
make -C plugins/input_control clean
make[1]: ingresso nella directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/input_control"
rm -f *.a *.o core *~ *.so *.lo
make[1]: uscita dalla directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/input_control"
make -C plugins/output_rtsp clean
make[1]: ingresso nella directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/output_rtsp"
rm -f *.a *.o core *~ *.so *.lo
make[1]: uscita dalla directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/output_rtsp"
rm -f *.a *.o mjpg_streamer core *~ *.so *.lo
gcc -D'SVN_REV="3:148M"' -O2 -DLINUX -D_GNU_SOURCE -Wall    -c -o mjpg_streamer.o mjpg_streamer.c
gcc -D'SVN_REV="3:148M"' -O2 -DLINUX -D_GNU_SOURCE -Wall    -c -o utils.o utils.c
gcc -D'SVN_REV="3:148M"' -O2 -DLINUX -D_GNU_SOURCE -Wall  mjpg_streamer.o utils.o -lpthread -ldl -o mjpg_streamer
chmod 755 mjpg_streamer
make -C plugins/input_uvc USE_LIBV4L2=true all
make[1]: ingresso nella directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/input_uvc"
gcc -c -O1 -DLINUX -D_GNU_SOURCE -Wall -shared -fPIC -DUSE_LIBV4L2 -o v4l2uvc.lo v4l2uvc.c
v4l2uvc.c: In function &#8216;init_videoIn&#8217;:
v4l2uvc.c:88:23: warning: variable &#8216;currentHeight&#8217; set but not used [-Wunused-but-set-variable]
v4l2uvc.c:88:9: warning: variable &#8216;currentWidth&#8217; set but not used [-Wunused-but-set-variable]
gcc -c -O1 -DLINUX -D_GNU_SOURCE -Wall -shared -fPIC -DUSE_LIBV4L2 -o jpeg_utils.lo jpeg_utils.c
gcc -c -O1 -DLINUX -D_GNU_SOURCE -Wall -shared -fPIC -DUSE_LIBV4L2 -o dynctrl.lo dynctrl.c
gcc -O1 -DLINUX -D_GNU_SOURCE -Wall -shared -fPIC -DUSE_LIBV4L2 -lv4l2 -ljpeg -o input_uvc.so input_uvc.c v4l2uvc.lo jpeg_utils.lo dynctrl.lo
make[1]: uscita dalla directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/input_uvc"
cp plugins/input_uvc/input_uvc.so .
make -C plugins/output_file all
make[1]: ingresso nella directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/output_file"
gcc -O2 -DLINUX -D_GNU_SOURCE -Wall -shared -fPIC -o output_file.so output_file.c
make[1]: uscita dalla directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/output_file"
cp plugins/output_file/output_file.so .
make -C plugins/output_udp all
make[1]: ingresso nella directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/output_udp"
gcc -O2 -DLINUX -D_GNU_SOURCE -Wall -shared -fPIC -o output_udp.so output_udp.c
make[1]: uscita dalla directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/output_udp"
cp plugins/output_udp/output_udp.so .
make -C plugins/output_http all
make[1]: ingresso nella directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/output_http"
gcc -c -O1 -DLINUX -D_GNU_SOURCE -Wall -shared -fPIC -o httpd.lo httpd.c
gcc -O1 -DLINUX -D_GNU_SOURCE -Wall -shared -fPIC -o output_http.so output_http.c httpd.lo
make[1]: uscita dalla directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/output_http"
cp plugins/output_http/output_http.so .
make -C plugins/input_testpicture all
make[1]: ingresso nella directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/input_testpicture"
convert pictures/960x720_1.jpg -resize 640x480! pictures/640x480_1.jpg
/bin/sh: convert: not found
make[1]: *** [pictures/640x480_1.jpg] Errore 127
make[1]: uscita dalla directory "/home/pasqoo/mjpg-streamer/mjpg-streamer/plugins/input_testpicture"
make: *** [input_testpicture.so] Errore 2
pasqoo@5742zg:~/mjpg-streamer/mjpg-streamer$
```

It doesn't find /bin/sh? Or what?

---

### Post by SevenMachines on 2011-11-02
Compiles fine here, try 
```
 $ sudo apt-get install imagemagick
```since then, 
```
$ dpkg -S /usr/bin/convert
imagemagick: /usr/bin/convert
```

---

### Post by kr0n1x on 2011-11-03
Yay now it worked :)
How did you find that solution?? :D

Thanks!

---

### Post by MadCow108 on 2011-11-03
bin/sh is a red herring, its the thing after the colon it does not find, bin/sh is just the program that tries to find it.
```
/bin/sh: convert: not found
```

the general solution to finding files not installed on your system is apt-file, dpkg -S only checks installed packages:
```
apt-file search -x  "bin/convert$"
graphicsmagick-imagemagick-compat: /usr/bin/convert
imagemagick: /usr/bin/convert
imagemagick-dbg: /usr/lib/debug/usr/bin/convert

```

---

### Post by kr0n1x on 2011-11-03
> **MadCow108 said:**
> bin/sh is a red herring, its the thing after the colon it does not find, bin/sh is just the program that tries to find it.
```
/bin/sh: convert: not found
```

the general solution to finding files not installed on your system is apt-file, dpkg -S only checks installed packages:
```
apt-file search -x  "bin/convert$"
graphicsmagick-imagemagick-compat: /usr/bin/convert
imagemagick: /usr/bin/convert
imagemagick-dbg: /usr/lib/debug/usr/bin/convert

```

Oh, I see... thanks :)

---

