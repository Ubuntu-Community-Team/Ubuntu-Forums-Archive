---
title: "Sigsegv"
date: 2010-12-07
forum: Programming Talk
---

### Post by deoxy on 2010-12-07
hello guys.

I am new in this forum. i trying compile a programm in ubuntu, but I have a problem, this compile OK, but when I trying run this, send me the following message:

deoxy@deoxy-laptop:~/AIS/libtissue-1.0$ sudo make clean all
rm -f *.o *~ libtissue.so.* libtissue.a
gcc -Wall -O2 -fPIC -g -I/home/deoxy/opt -c tissue.c
gcc -Wall -O2 -fPIC -g -I/home/deoxy/opt -c client.c
gcc -Wall -O2 -fPIC -g -I/home/deoxy/opt -c ds.c
gcc -Wall -O2 -fPIC -g -I/home/deoxy/opt -c signal.c
gcc -Wall -O2 -fPIC -g -I/home/deoxy/opt -c antigen.c
gcc -Wall -O2 -fPIC -g -I/home/deoxy/opt -c cytokine.c
gcc -Wall -O2 -fPIC -g -I/home/deoxy/opt -c cell.c
gcc -Wall -O2 -fPIC -g -I/home/deoxy/opt -c receptor.c
gcc -Wall -O2 -fPIC -g -I/home/deoxy/opt -c producer.c
gcc -Wall -O2 -fPIC -g -I/home/deoxy/opt -c misc.c
gcc -Wall -O2 -fPIC -g -I/home/deoxy/opt -c response.c
response.c: In function ‘old_send_response’:
response.c:73: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc -Wall -O2 -fPIC -g -I/home/deoxy/opt -c syscall.c
gcc -Wall -O2 -fPIC -g -I/home/deoxy/opt -c log.c
gcc -Wall -O2 -fPIC -g -I/home/deoxy/opt  -shared -Wl,-soname,libtissue.so.1 \
        -o libtissue.so.1.1.0.0 tissue.o client.o ds.o signal.o antigen.o cytokine.o cell.o receptor.o producer.o misc.o response.o syscall.o log.o
ar rcs libtissue.a tissue.o client.o ds.o signal.o antigen.o cytokine.o cell.o receptor.o producer.o misc.o response.o syscall.o log.o

deoxy@deoxy-laptop:~/AIS/libtissue-1.0$ sudo make install
rm -f /usr/local/lib/libtissue.so* /usr/local/lib/libtissue.a
ldconfig
rm -rf /usr/local/include/tissue
install libtissue.so.1.1.0.0 /usr/local/lib
install libtissue.a /usr/local/lib
ldconfig
rm -f /usr/local/lib/libtissue.so
ln -s /usr/local/lib/libtissue.so.1 /usr/local/lib/libtissue.so
rm -rf /usr/local/include/tissue
mkdir /usr/local/include/tissue
install tissue.h client.h ds.h signal.h antigen.h cytokine.h cell.h \
            receptor.h producer.h misc.h response.h syscall.h \
            log.h syscallent.h \
            /usr/local/include/tissue

deoxy@deoxy-laptop:~/AIS/libtissue-1.0$ sudo ./libtissue.so.1.1.0.0 
Fallo de segmentación

(segmentation fault)

I debug this whit ddd and I find this:
(gdb) run
Starting program: /home/deoxy/AIS/libtissue-1.0/libtissue.so.1.1.0.0 

Program received signal SIGSEGV, Segmentation fault.
0x00000001 in ?? ()
(gdb) 

I read many manual, reference, wiki etc. but I understand what is the problem. 

Can anyone help me with this, please?.

regards.

deoxy.-

---

### Post by Zugzwang on 2010-12-07
You have compiled a library, which are typically not executable. You will need to create a program that uses that library in order to have something executable. 

I'm however a little bit puzzled about the fact that you were able to treat your library like a program in the first place, i.e., execute it.

---

### Post by dwhitney67 on 2010-12-07
> **Zugzwang said:**
> You have compiled a library, which are typically not executable. You will need to create a program that uses that library in order to have something executable. 

I'm however a little bit puzzled about the fact that you were able to treat your library like a program in the first place, i.e., execute it.

Beware that some developers like to do weird things; for example, they implement a main() function in their library.

I believe Douglas Young did something retarded like this in his book "Object Oriented Programming with C++ and OSF/Motif".

Of course, as you stated, one must still develop a program and link with the library before it can be executed.

Consider the mini-project that I have attached.  After downloading it:
```

tar xf mini.tar
cd mini
make         # builds library and app
make run     # runs the app

```

---

