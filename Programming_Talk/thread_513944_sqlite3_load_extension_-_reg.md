---
title: "sqlite3_load_extension - reg"
date: 2007-07-31
forum: Programming Talk
---

### Post by zoobave on 2007-07-31
Hi,
                    I got the follwoing error while doing make. Is there any library to be loaded other than sqlite3?

```
/bin/sh ../libtool --tag=CC   --mode=link gcc  -g -O2   -o foo main.o callbacks.o -L/usr/local/lib -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -L/usr/local/lib -lmtp -lusb  -lsqlite3
gcc -g -O2 -o foo main.o callbacks.o  -L/usr/local/lib /usr/local/lib/libgtk-x11-2.0.so /usr/local/lib/libgdk-x11-2.0.so /usr/local/lib/libatk- 1.0.so /usr/local/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libpangocairo-1.0.so /usr/lib/libpango-1.0.so /usr/lib/libcairo.so /usr/lib/libgobject- 2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so /usr/local/lib/libmtp.so /usr/lib/libusb.so /usr/local/lib/libsqlite3.so -Wl,--rpath -Wl,/usr/local/lib -Wl,--rpath -Wl,/usr/local/lib
callbacks.o: In function `load_db':
/home/user/dvm/whatever-0.0.1/src/callbacks.c:1617: undefined reference to `sqlite3_load_extension'
/home/user/dvm/whatever-0.0.1/src/callbacks.c:1618: undefined reference to `sqlite3_enable_load_extension'
collect2: ld returned 1 exit status
make: *** [foo] Error 1

```



-- 

Regards,

Zoobave A
[http://zoobave.blogspot.com]("http://zoobave.blogspot.com")

---

