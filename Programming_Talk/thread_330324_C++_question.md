---
title: "C++ question"
date: 2007-01-03
forum: Programming Talk
---

### Post by Ben Sprinkle on 2007-01-03
I need to know the following.
1. When a program is compiled using gtkmm, does the other user who does not have gtkmm installed, do they need it installed just to run? Or is it only if it is refrencing extra libs?

2. What if I manually copy the .h files I am using into my directory upon compiling. Does the other user still need gtkmm installed? Or can it run stand alone.

---

### Post by Mirrorball on 2007-01-03
They will need to have all the **shared libraries** you are linking to, not the headers. The headers will be included in your program anyway (you #include them).

---

### Post by lnostdal on 2007-01-03
assuming you are developing for and under ubuntu this is not something the user needs to do "manually"; just distribute your application as a .deb and make it download and install libgtkmm for them

you can also link in libgtkmm statically into your application but this is not something i'd do when better options like the one above exists

---

### Post by amo-ej1 on 2007-01-03
Use *ldd* to see on what libraries an application depends e.g.:

```

edb@lapedb:~$ ldd /usr/bin/wireshark 
        linux-gate.so.1 =>  (0xffffe000)
        libwiretap.so.0 => /usr/lib/wireshark/libwiretap.so.0 (0xb7ed6000)
        libwireshark.so.0 => /usr/lib/wireshark/libwireshark.so.0 (0xb6af1000)
        libpcre.so.3 => /usr/lib/libpcre.so.3 (0xb6ab0000)
        libpcap.so.0.8 => /usr/lib/libpcap.so.0.8 (0xb6a88000)
        libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0xb6738000)
        libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0xb66b4000)
        libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0xb669a000)
        libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0xb6684000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb665d000)
        libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0xb6655000)
        libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0xb6626000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb6619000)
        libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb6611000)
        libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0xb660e000)
        libXi.so.6 => /usr/lib/libXi.so.6 (0xb6605000)
        libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0xb6602000)
        libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0xb65f9000)
        libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0xb65f4000)
        libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0xb65ba000)
        libcairo.so.2 => /usr/lib/libcairo.so.2 (0xb6558000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb648e000)
        libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0xb6454000)
        libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0xb6450000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb644c000)
        libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0xb6447000)
        libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0xb63b5000)
        libadns.so.1 => /usr/lib/libadns.so.1 (0xb63a3000)
        libgcrypt.so.11 => /usr/lib/libgcrypt.so.11 (0xb6355000)
        libgpg-error.so.0 => /usr/lib/libgpg-error.so.0 (0xb6351000)
        libgnutls.so.13 => /usr/lib/libgnutls.so.13 (0xb62e2000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb62ce000)
        libcap.so.1 => /lib/libcap.so.1 (0xb62ca000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb62b6000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb6182000)
        librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0xb6179000)
        /lib/ld-linux.so.2 (0xb7f17000)
        libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0xb614e000)
        libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0xb60e4000)
        libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb60c5000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb60c2000)
        libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb609e000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb6099000)
        libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb6083000)
        libtasn1.so.3 => /usr/lib/libtasn1.so.3 (0xb606f000)

```

This shows all the shared libraries wireshark uses and at what offset they will be loaded. When one of the required libraries is not found in the LD_LIBRARY_PATH the application will complain and will not start.

Moving header files around is only something that will make your compiler happy, without the proper link options your code will not even link ...

---

### Post by Ben Sprinkle on 2007-01-03
Thanks, but including headers, the user does not need libgtkmm if it is compiled already to run?

---

### Post by Mirrorball on 2007-01-03
He will need it.

---

### Post by Ben Sprinkle on 2007-01-03
Alrighty, thanks evil looking nurse. ;)

---

### Post by Wybiral on 2007-01-03
> Alrighty, thanks evil looking nurse. 
lol

---

### Post by amo-ej1 on 2007-01-04
can't stand the urge to start whistling 'twisted nerve' when seeing that avatar ;)

---

