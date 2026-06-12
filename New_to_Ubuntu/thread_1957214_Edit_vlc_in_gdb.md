---
title: "Edit vlc in gdb"
date: 2012-04-12
forum: New to Ubuntu
---

### Post by greendragons on 2012-04-12
Hello,
I want to modify few lines in vlc source... but for that i exactly need to know which function is invoked for that feature(i want to edit default subtitles path)... when i load vlc in gdb i get this
```

<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /usr/bin/vlc...Reading symbols from /usr/lib/debug/usr/bin/vlc...done.
done.
(gdb) l
55    vlc.c: No such file or directory.
    in vlc.c
(gdb) 

```

And also if i run it.. then
```
(gdb) r
Starting program: /usr/bin/vlc 
[Thread debugging using libthread_db enabled]
VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[New Thread 0xb7ddfb70 (LWP 4648)]
[New Thread 0xb7d5eb70 (LWP 4649)]
[0x804c914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[New Thread 0xb7cddb70 (LWP 4650)]
Blocked: call to setlocale(6, "")
[New Thread 0xb7c0ab70 (LWP 4651)]

```

I just get the spawned threads and addresses not C code so that i can probe into functions based on the action i take on vlc gui...

Thnx!!

---

### Post by MG&amp;TL on 2012-04-12
Compile vlc from source, then debug the executable. That way it may be able to find the source. Some build systems have a "make debug" option for more debug symbols.

Also, I'm sure you can probably either find it in the source code, or ask another developer.

Well done for contributing. :)

---

### Post by greendragons on 2012-04-12
I tried installing from source code.. it's giving me lots of errors for missing deps.. even i followed one tutorial still no cigars! If ya know some link(good one) to installation vlc from source then plz it will be big favor... 
I use ubuntu Natty...
Thnx!!!
**The Idea of Open Source is DIVINE**

---

### Post by MG&amp;TL on 2012-04-12
To install missing build dependencies:

```
sudo apt-get build-dep vlc
```

After that, if you've still got compiler errors, paste them here. :)

Amen to that.

---

### Post by greendragons on 2012-04-12
Thnx for command tht helped me... im able to configure now...
I have set custom path using --prefix.. in configure
But while make install im getting error...
```

make install prefix=/home/kodedozer/vlc_build/vlc

```

Error is 
```
libtool: install: /usr/bin/install -c .libs/libvlccore.lai /home/kodedozer/vlc_build/vlc/lib/libvlccore.la
libtool: install: error: cannot install `libvlc.la' to a directory not ending in /home/kodeodzer/vlc_build/vlc/lib
make[5]: *** [install-libLTLIBRARIES] Error 1
make[5]: Leaving directory `/home/kodedozer/vlc_build/src'
make[4]: *** [install-am] Error 2
make[4]: Leaving directory `/home/kodedozer/vlc_build/src'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `/home/kodedozer/vlc_build/src'
make[2]: *** [install] Error 2
make[2]: Leaving directory `/home/kodedozer/vlc_build/src'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/kodedozer/vlc_build'
make: *** [install] Error 2

```
Thnx!!

---

### Post by MG&amp;TL on 2012-04-12
> **greendragons said:**
> 
Error is 
```
libtool: install: /usr/bin/install -c .libs/libvlccore.lai /home/kodedozer/vlc_build/vlc/lib/libvlccore.la
libtool: install: error: cannot install `libvlc.la' to a directory not ending in /home/kodeodzer/vlc_build/vlc/lib
make[5]: *** [install-libLTLIBRARIES] Error 1
make[5]: Leaving directory `/home/kodedozer/vlc_build/src'
make[4]: *** [install-am] Error 2
make[4]: Leaving directory `/home/kodedozer/vlc_build/src'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `/home/kodedozer/vlc_build/src'
make[2]: *** [install] Error 2
make[2]: Leaving directory `/home/kodedozer/vlc_build/src'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/kodedozer/vlc_build'
make: *** [install] Error 2

```

Thnx!!

I'm sorry, but I have absolutely no idea. I think that's vlc's bad, not yours. Try re-updating your source tree after a day or so, and they might have fixed it. Or else, you could try (gulp!) installing without a prefix.

---

### Post by greendragons on 2012-04-12
I did everything from scratch, now it's working fine and im able to view source code in gdb, :guitar:
Hope could be able to edit what i want
Thnx for help!

---

### Post by greendragons on 2012-04-12
I thought it was done.. But im not getting exact function while selecting vlc options, what im getting is
```
[Thread 0xae521b70 (LWP 11423) exited]
[New Thread 0xae521b70 (LWP 11426)]
[Thread 0xb69bbb70 (LWP 11425) exited]
[Thread 0xae521b70 (LWP 11426) exited]

```
It's all thread information rather than those particular thread code..

---

### Post by greendragons on 2012-04-12
Ohh! i missed lol.. This are the threads spawned by libraries which are installed already like cario for graphics.. i can't view their code from vlc lol..

---

### Post by MG&amp;TL on 2012-04-12
> **greendragons said:**
> I thought it was done.. But im not getting exact function while selecting vlc options, what im getting is
```
[Thread 0xae521b70 (LWP 11423) exited]
[New Thread 0xae521b70 (LWP 11426)]
[Thread 0xb69bbb70 (LWP 11425) exited]
[Thread 0xae521b70 (LWP 11426) exited]

```
It's all thread information rather than those particular thread code..

Huh. Try:

```
make clean
make debug

```

EDIT: never mind. :)

You might be a lot better just understanding the interface code. If, for instance, you can see a particular bit of text, search for that bit of text in the source code.

---

### Post by greendragons on 2012-04-12
> **MG&TL said:**
> Huh. Try:

```
make clean
make debug

```EDIT: never mind. :)

No it was my bad.. i asked stupid question..
Those spawned threads are from libraries which are not from vlc package so their code wasn't revealed.
Thnx for help...

---

### Post by MG&amp;TL on 2012-04-12
> **greendragons said:**
> No it was my bad.. i asked stupid question..
Those spawned threads are from libraries which are not from vlc package so their code wasn't revealed.
Thnx for help...

No problem, let me know how your code gets on. :)

---

