---
title: "Changing a binarys linked libraries"
date: 2007-09-11
forum: Programming Talk
---

### Post by jimdaddy on 2007-09-11
Hi everyone,

I have a binary file that I compiled (I have the source of it), and I wish to copy this file to another machine (which is a stripped down embedded distro) and run it there, however it obviously has a number of linked libraries which aren't in the same location on that machine or don't exist at all.

Basically, if I run ldd on the library (on the machine it was compiled on) this is the output:

```

ldd ddccontrol
       libddccontrol.so.0 => /usr/local/lib/libddccontrol.so.0
(0x005f3000)
       libxml2.so.2 => /usr/lib/libxml2.so.2 (0x02ba5000)
       libz.so.1 => /usr/lib/libz.so.1 (0x00d0c000)
       libpthread.so.0 => /lib/tls/libpthread.so.0 (0x00dd9000)
       libm.so.6 => /lib/tls/libm.so.6 (0x00bf0000)
       libc.so.6 => /lib/tls/libc.so.6 (0x00ac4000)
       /lib/ld-linux.so.2 (0x00aab000)

```

Now some of those libraries/paths dont exist on the other machine, so I'm looking for a way to just package the binary with the libs, like:

myapp/binary
myapp/lib/libxml2.so.2 etc.

I have tried opening the binary file in a hex editor to change the path but I end up with a seg fault so I assume I'm doing it wrong. Can anyone give me any pointers on how to do this better, perhaps a specific tool i could use or maybe even recommend a hex editor.

Any help is appreciated,

Thanks.

---

### Post by Wybiral on 2007-09-11
I don't know of any way after it's already compiled, maybe someone else does.

The reason the hex editor didn't work is likely because you changed the offsets of everything (changing the length of the path will change the executable offsets).

Can't you simply create the directories on the target file system?

---

### Post by jimdaddy on 2007-09-11
Well I could, but that's something I'd really like to avoid. The OS is a mere 8mb, completely stripped, so I'd rather just run this from a /tmp directory or nfs (at least now while im testing it). 

I do have the source for this program, so if there is even a way at compile time to directly link it? Although I'm sure that would require some heavy editing of the configure script. 

One thing I do remember is a variable, something like LD_PRELOAD that allows you to replace libraries which are linked in a binary during runtime. Unfortunately I dont think thats the actual variable name since i cant seem to find anything on it. 

At least I have hex editing crossed off my list so far heh :) Thanks.

---

### Post by Wybiral on 2007-09-11
If you can compile it, then you can move the libraries (or shared object files) into a relative directory.

If it's not too big of a project (doesn't have too complex of a build system) then it shouldn't be too hard to do.

---

### Post by gnusci on 2007-09-11
It sound to me that you need statical linking. In this case why don't you just try to compile with static linking so all the libraries will be inside the binary. It can be just something like:

**> ./configure --enable-static-link**
**> make**

more information:

[http://phaseit.net/claird/comp.programming/linking.html](http://phaseit.net/claird/comp.programming/linking.html)
[http://en.wikipedia.org/wiki/Static_Library](http://en.wikipedia.org/wiki/Static_Library)
[http://www.faqs.org/docs/linux_scratch/chapter05/whystatic.html](http://www.faqs.org/docs/linux_scratch/chapter05/whystatic.html)
[http://publib.boulder.ibm.com/infocenter/pseries/v5r3/index.jsp?topic=/com.ibm.aix.prftungd/doc/prftungd/when_dyn_linking_static_linking.htm](http://publib.boulder.ibm.com/infocenter/pseries/v5r3/index.jsp?topic=/com.ibm.aix.prftungd/doc/prftungd/when_dyn_linking_static_linking.htm)

---

### Post by jimdaddy on 2007-09-11
Thanks a lot that made the main binary static and it works great. However in the src folder it also makes a second binary which it calls to probe a monitor; it doesn't seem to be built statically, ie:

```

ldd ddcpci
        libc.so.6 => /lib/tls/libc.so.6 (0x00ac4000)
        /lib/ld-linux.so.2 (0x00aab000)

```

So when i copy that file over to the other machine it says:

> 
/lib/i686/libc.so.6: version `GLIBC_2.3' not found  (required by /usr/local/bin/ddcpci)


That file does exist (in /lib/ anyway), should it not of been built statically too? The Makefile in its directory has the following LINK attribute:

> 
LINK = $(LIBTOOL) --tag=CC --mode=link $(CCLD) $(AM_CFLAGS) $(CFLAGS) \
        $(AM_LDFLAGS) $(LDFLAGS) -o $@


I assume the `--mode=link gcc`  should of done that? Sorry for the newbish question's but I've never done anything like this before :)

Thanks again.

---

### Post by gnusci on 2007-09-11
Try including:

**-static-libgcc**

or also:

**-Wl,-Bstatic -lstdc++**

during the linking process, something like:
[PHP]
LINK = $(LIBTOOL) -static-libgcc --tag=CC --mode=link $(CCLD) $(AM_CFLAGS) $(CFLAGS) \
$(AM_LDFLAGS) $(LDFLAGS) -o $@[/PHP]

---

### Post by jimdaddy on 2007-09-12
Hi thanks for the replies again :)

Unfortunately the option -static-libgcc isnt recognised? I wasn't able to find very much out of it on google. I'm using gcc 3.4.5 if that helps. I tried adding `-Wl,-Bstatic -lstdc++` into the Makefile, but it wouldnt compile then;

> 
gcc -g -O2 -Wall -Wl,-Bstatic -DDATADIR=\"/usr/local/share/ddccontrol-db\" -DBINDIR=\"/usr/local/bin\" -o ddcpci -Wl,-z -Wl,now main.o nvidia.o radeon.o i2c-algo-bit.o intel810.o via.o sis.o  -lstdc++ -lpci
/usr/bin/ld: cannot find -lgcc_s
collect2: ld returned 1 exit status


Thanks again for the help, I really appreciate it :)

---

### Post by gnusci on 2007-09-12
> gcc -g -O2 -Wall -Wl,-Bstatic -DDATADIR=\"/usr/local/share/ddccontrol-db\" -DBINDIR=\"/usr/local/bin\" -o ddcpci -Wl,-z -Wl,now main.o nvidia.o radeon.o i2c-algo-bit.o intel810.o via.o sis.o -lstdc++ -lpci
/usr/bin/ld: cannot find -lgcc_s
collect2: ld returned 1 exit status

As I can see your compiler [COLOR="Red"]can not find -lgcc_s[/COLOR] :) if this the case, it is mean that you must tell to the compiler where it can find it, to know where the library is you can ask to the compiler:

**> gcc -print-libgcc-file-name**

The result is something like:

**/usr/lib/libgcc_s.so**

if not you have to install it, if yes try **ldd** so you can get more information:

**> ldd /usr/lib/libgcc_s.so**

You have to check whether there is something pointing to the wrong place or not. If everything look all right try to add the right path, something like:

**-L /usr/lib/**

could you post the output of:

**> uname -a**
**> gcc -v**

---

### Post by jimdaddy on 2007-09-12
> **gnusci said:**
> As I can see your compiler [COLOR="Red"]can not find -lgcc_s[/COLOR] :) if this the case, it is mean that you must tell to the compiler where it can find it, to know where the library is you can ask to the compiler:

**> gcc -print-libgcc-file-name**


```

# gcc -print-libgcc-file-name
/usr/lib/gcc/i386-redhat-linux/3.4.5/libgcc.a

```

No .so file was returned, so I checked and I do have libgcc installed. Did a little searching and found;

```

/usr/lib/gcc/i386-redhat-linux/3.4.3/libgcc_s.so -> /lib/libgcc_s.so.1
/lib/libgcc_s.so.1 -> libgcc_s-3.4.6-20060404.so.1

```

I tried to make a /lib/libgcc_s.so link to the .so above, but i still get the problem about finding lgcc_s :(

> 
if not you have to install it, if yes try **ldd** so you can get more information:


```

ldd /lib/libgcc_s-3.4.6-20060404.so.1
        libc.so.6 => /lib/tls/libc.so.6 (0x00411000)
        /lib/ld-linux.so.2 (0x00aab000)

```

Seems to be normal enough right? 

> 
**-L /usr/lib/**


I added this to the COMPILE option in the makefile, adding it to the LINK section gives an error about /lib/ being a directory (it sure is!:))

> 
could you post the output of:

**> uname -a**
**> gcc -v**

yup, this machine I'm compiling it on as you can see is a centos 4.x box:

```

# uname -a
Linux quaoar 2.6.9-34.EL #1 Wed Mar 8 00:07:35 CST 2006 i686 i686 i386 GNU/Linux

# gcc -v
Reading specs from /usr/lib/gcc/i386-redhat-linux/3.4.5/specs
Configured with: ../configure --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --enable-shared --enable-threads=posix --disable-checking --with-system-zlib --enable-__cxa_atexit --disable-libunwind-exceptions --enable-java-awt=gtk --host=i386-redhat-linux
Thread model: posix
gcc version 3.4.5 20051201 (Red Hat 3.4.5-2)

```

Maybe I could edit the --enable-shared option from the specs file? Since this is pretty much all I need to compile anyway :)

Thanks again!

---

### Post by gnusci on 2007-09-12
I suspect you compiler does not like the idea the link thi library in static mode, that can be becuase the binary can no run properly, it seem that you have an small mess with it, because you have:

**gcc version 3.4.5**

but also:

```

/usr/lib/gcc/i386-redhat-linux/3.4.3/libgcc_s.so -> /lib/libgcc_s.so.1
/lib/libgcc_s.so.1 -> libgcc_s-3.4.6-20060404.so.1

```

and 

```

ldd /lib/libgcc_s-3.4.6-20060404.so.1
        libc.so.6 => /lib/tls/libc.so.6 (0x00411000)
        /lib/ld-linux.so.2 (0x00aab000)

```

but it seem to me that you have this library compiled for a newer version:

**libgcc_s-3.4.6-20060404.so.1**

which can be the cause why gcc-3.4.5 does reject it...

---

