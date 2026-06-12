---
title: "Java and BlueJ Installation; Warning!: Noob; use small words!"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by lupinesoul on 2008-07-17
I think I got java set up, but I'm not sure...  Here's what was in the terminal.  I also need help installing bluej. ^_^'  Thanks.


nate@nateComp:~/Desktop$ java -jar bluej-221.jar
*** glibc detected *** /usr/bin/sablevm: munmap_chunk(): invalid pointer: 0x0824d678 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7dfe61b]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb49658b1]
/usr/lib/sablevm-classpath/libgtkpeer-1.13.so(Java_gnu_java_awt_peer_gtk_GdkFontPeer_getGlyphVector+0x395)[0xb4f9011c]
/usr/lib/libffi.so.4(ffi_call_SYSV+0x17)[0xb7d2b4e3]
/usr/lib/libffi.so.4(ffi_call+0x6a)[0xb7d2b31a]
/usr/lib/libsablevm-1.13.so[0xb7ef8b85]
/usr/lib/libsablevm-1.13.so[0xb7f2a5b8]
/lib/tls/i686/cmov/libpthread.so.0[0xb7d324fb]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0xb7e65e5e]
======= Memory map: ========
08048000-0804b000 r-xp 00000000 08:01 4352617    /usr/bin/sablevm
0804b000-0804c000 rw-p 00002000 08:01 4352617    /usr/bin/sablevm
0804c000-08336000 rw-p 0804c000 00:00 0          [heap]
ad7c8000-ad7da000 r--p 00000000 08:01 4481069    /usr/share/fonts/type1/gsfonts/n019004l.pfb
ad7da000-ad7db000 ---p ad7da000 00:00 0 
ad7db000-adfdb000 rw-p ad7db000 00:00 0 
adfdb000-adfdc000 ---p adfdb000 00:00 0 
adfdc000-ae7dc000 rw-p adfdc000 00:00 0 
ae7dc000-ae7f0000 r--p 00000000 08:01 4481066    /usr/share/fonts/type1/gsfonts/n019003l.pfb
ae7f0000-ae7f1000 ---p ae7f0000 00:00 0 
ae7f1000-aeff1000 rw-p ae7f1000 00:00 0 
aeff1000-aeff2000 ---p aeff1000 00:00 0 
aeff2000-af7f2000 rw-p aeff2000 00:00 0 
af7f2000-af7f7000 r-xp 00000000 08:01 4374953    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-gif.so
af7f7000-af7f8000 rw-p 00005000 08:01 4374953    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-gif.so
af7f8000-af8f9000 rw-p af7f8000 00:00 0 
af8f9000-af8fa000 ---p af8f9000 00:00 0 
af8fa000-b00fa000 rw-p af8fa000 00:00 0 
b00fa000-b00fb000 ---p b00fa000 00:00 0 
b00fb000-b08fb000 rw-p b00fb000 00:00 0 
b08fb000-b08fc000 ---p b08fb000 00:00 0 
b08fc000-b10fc000 rw-p b08fc000 00:00 0 
b10fc000-b10fd000 ---p b10fc000 00:00 0 
b10fd000-b18fd000 rw-p b10fd000 00:00 0 
b18fd000-b18fe000 ---p b18fd000 00:00 0 
b18fe000-b20fe000 rw-p b18fe000 00:00 0 
b20fe000-b20ff000 ---p b20fe000 00:00 0 
b20ff000-b2a6e000 rw-p b20ff000 00:00 0 
b2a6e000-b2b00000 ---p b2a6e000 00:00 0 
b2b04000-b2b06000 r-xp 00000000 08:01 4407984    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b2b06000-b2b07000 rw-p 00001000 08:01 4407984    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b2b07000-b2b08000 ---p b2b07000 00:00 0 
b2b08000-b3409000 rw-p b2b08000 00:00 0 
b3409000-b340f000 r--s 00000000 08:01 8791       /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b340f000-b3412000 r--s 00000000 08:01 8801       /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b3412000-b3413000 r--s 00000000 08:01 8793       /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b3413000-b3414000 r--s 00000000 08:01 8786       /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b3414000-b3417000 r--s 00000000 08:01 8792       /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b3417000-b341a000 r--s 00000000 08:01 8788       /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b341a000-b341d000 r--s 00000000 08:01 8798       /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b341d000-b3425000 r--s 00000000 08:01 8802       /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b3425000-b342d000 r--s 00000000 08:01 8781       /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b342d000-b344f000 r--s 00000000 08:01 8858       /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b344f000-b3456000 r--s 00000000 08:01 8796       /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b3456000-b3457000 ---p b3456000 00:00 0 
b3457000-b3c57000 rw-p b3457000 00:00 0 
b3c57000-b3c65000 r-xp 00000000 08:01 4374915    /usr/lib/gtk-2.0/2.10.0/engines/libcrux-engine.so
b3c65000-b3c66000 rw-p 0000d000 08:01 4374915    /usr/lib/gtk-2.0/2.10.0/engines/libcrux-engine.so
b3c66000-b3c67000 ---p b3c66000 00:00 0 
b3c67000-b4467000 rw-p b3c67000 00:00 0 
b4467000-b4470000 r-xp 00000000 08:01 2106723    /lib/tls/i686/cmov/libnss_files-2.7.so
b4470000-b4472000 rw-p 00008000 08:01 2106723    /lib/tls/i686/cmov/libnss_files-2.7.so
b4472000-b447a000 r-xp 00000000 08:01 2106727    /lib/tls/i686/cmov/libnss_nis-2.7.so
b447a000-b447c000 rw-p 00007000 08:01 2106727    /lib/tls/i686/cmov/libnss_nis-2.7.so
b447c000-b4490000 r-xp 00000000 08:01 2106717    /lib/tls/i686/cmov/libnsl-2.7.so
b4490000-b4492000 rw-p 00013000 08:01 2106717    /lib/tls/i686/cmov/libnsl-2.7.so
b4492000-b4494000 rw-p b4492000 00:00 0 
b4494000-b449b000 r-xp 00000000 08:01 2106719    /lib/tls/i686/cmov/libnss_compat-2.7.so
b449b000-b449d000 rw-p 00006000 08:01 2106719    /lib/tls/i686/cmov/libnss_compat-2.7.so
b449f000-b44a0000 r--s 00000000 08:01 8784       /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b44a0000-b44a3000 r--s 00000000 08:01 8799       /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b44a3000-b44a9000 r--s 00000000 08:01 8780       /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b44a9000-b44ab000 r--s 00000000 08:01 8841       /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b44ab000-b44ea000 r--p 00000000 08:01 4375420    /usr/lib/locale/en_US.utf8/LC_CTYPE
b44ea000-b44eb000 r--p 00000000 08:01 4375425    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b44eb000-b44ec000 r--p 00000000 08:01 4375428    /usr/lib/locale/en_US.utf8/LC_TIME
b44ec000-b45cd000 r--p 00000000 08:01 4375419    /usr/lib/locale/en_US.utf8/LC_COLLATE
b45cd000-b45ce000 r--p 00000000 08:01 4375423    /usr/lib/locale/en_US.utf8/LC_MONETARY
b45ce000-b45d2000 r-xp 00000000 08:01 4351292    /usr/lib/libXdmcp.so.6.0.0
b45d2000-b45d3000 rw-p 00003000 08:01 4351292    /usr/lib/libXdmcp.so.6.0.0
b45d3000-b45ea000 r-xp 00000000 08:01 4352122    /usr/lib/libxcb.so.1.0.0
b45ea000-b45eb000 rw-p 00016000 08:01 4352122    /usr/lib/libxcb.so.1.0.0
b45eb000-b45ec000 r-xp 00000000 08:01 4352120    /usr/lib/libxcb-xlib.so.0.0.0
b45ec000-b45ed000 rw-p 00000000 08:01 4352120    /usr/lib/libxcb-xlib.so.0.0.0
b45ed000-b4613000 r-xp 00000000 08:01 4351940    /usr/lib/libpcre.so.3.12.1
b4613000-b4614000 rw-p 00026000 08:01 4351940    /usr/lib/libpcre.so.3.12.1
b4614000-b462b000 r-xp 00000000 08:01 2089085    /lib/libselinux.so.1
b462b000-b462d000 rw-p 00016000 08:01 2089085    /lib/libselinux.so.1
b462d000-b4634000 r-xp 00000000 08:01 2106736    /lib/tls/i686/cmov/librt-2.7.so
b4634000-b4636000 rw-p 00006000 08:01 2106736    /lib/tls/i686/cmov/librt-2.7.so
b4636000-b4640000 r-xp 00000000 08:01 2089024    /lib/libgcc_s.so.1
b4640000-b4641000 rw-p 0000a000 08:01 2089024    /lib/libgcc_s.so.1
b4641000-b4729000 r-xp 00000000 08:01 4352059    /usr/lib/libstdc++.so.6.0.9
b4729000-b472c000 r--p 000e8000 08:01 4352059    /usr/lib/libstdc++.so.6.0.9
b472c000-b472e000 rw-p 000eb000 08:01 4352059    /usr/lib/libstdc++.so.6.0.9
b472e000-b4734000 rw-p b472e000 00:00 0 
b4734000-b475c000 r-xp 00000000 08:01 4351950    /usr/lib/libpixman-1.so.0.10.0
b475c000-b475d000 rw-p 00027000 08:01 4351950    /usr/lib/libpixman-1.so.0.10.0
b475d000-b477f000 r-xp 00000000 08:01 4351954    /usr/lib/libpng12.so.0.15.0
b477f000-b4780000 rw-p 00022000 08:01 4351954    /usr/lib/libpng12.so.0.15.0
b4780000-b4782000 r-xp 00000000 08:01 4351281    /usr/lib/libXau.so.6.0.0
b4782000-b4783000 rw-p 00001000 08:01 4351281    /usr/lib/libXau.so.6.0.0
b4783000-b47a2000 r-xp 00000000 08:01 4351518    /usr/lib/libexpat.so.1.5.2
b47a2000-b47a4000 rw-p 0001e000 08:01 4351518    /usr/lib/libexpat.so.1.5.2
b47a4000-b47a6000 r-xp 00000000 08:01 4351290    /usr/lib/libXdamage.so.1.1.0
b47a6000-b47a7000 rw-p 00001000 08:01 4351290    /usr/lib/libXdamage.so.1.1.0
b47a7000-b47a9000 r-xp 00000000 08:01 4351286    /usr/lib/libXcomposite.so.1.0.0
b47a9000-b47aa000 rw-p 00001000 08:01 4351286    /usr/lib/libXcomposite.so.1.0.0
b47aa000-b47ae000 r-xp 00000000 08:01 4351324    /usr/lib/libXtst.so.6.1.0
b47ae000-b47af000 rw-p 00003000 08:01 4351324    /usr/lib/libXtst.so.6.1.0
b47af000-b4893000 r-xp 00000000 08:01 4351275    /usr/lib/libX11.so.6.2.0
b4893000-b4896000 rw-p 000e4000 08:01 4351275    /usr/lib/libX11.so.6.2.0
b4896000-b48ab000 r-xp 00000000 08:01 4351245    /usr/lib/libICE.so.6.3.0
b48ab000-b48ac000 rw-p 00014000 08:01 4351245    /usr/lib/libICE.so.6.3.0
b48ac000-b48ae000 rw-p b48ac000 00:00 0 
b48ae000-b48b5000 r-xp 00000000 08:01 4351269    /usr/lib/libSM.so.6.0.0
b48b5000-b48b6000 rw-p 00006000 08:01 4351269    /usr/lib/libSM.so.6.0.0
b48b6000-b4922000 r-xp 00000000 08:01 4351534    /usr/lib/libfreetype.so.6.3.16
b4922000-b4926000 rw-p 0006b000 08:01 4351534    /usr/lib/libfreetype.so.6.3.16
b4926000-b49d6000 r-xp 00000000 08:01 4351604    /usr/lib/libglib-2.0.so.Aborted
nate@nateComp:~/Desktop$

---

### Post by lupinesoul on 2008-07-17
Does the code intimidate most people?  I've seen people ask for code before... :(

---

### Post by Inxsible on 2008-07-17
First things first....lets see what version of java you have. type in ```
java -version
``` and post back the output here.

This time use the code tags to post any output...makes it a lot more readable

---

### Post by TSS on 2008-07-17
It appears that your command to install BlueJ is correct.  See here for more complete instructions: [http://www.bluej.org/download/install.html](http://www.bluej.org/download/install.html)

Let's make sure Java is setup correctly though.  Do what the poster suggested above me, and type 'java -version'.  Post the results here.

---

### Post by tinny on 2008-07-18
> 
First things first....lets see what version of java you have. type in
Code:

java -version




Yeah looks like a java version problem.

I have Sun Java 6 installed and it works great (im running Ubuntu Hardy)

"java -version" gives me...

```

java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)

```

I also use NetBeans and it runs fine. (BlueJ is a cut down version of NetBeans)

If you want to try the same Java environment as me do the following...

```

sudo apt-get clean
sudo apt-get update
sudo apt-get install sun-java6*

```

---

### Post by lupinesoul on 2008-07-18
SableVM version 1.13
- compile date and time: 2006-11-09 00:24:19 UTC
- gcc version: 4.1.2 20061103 (prerelease) (Ubuntu 4.1.1-18ubuntu2)
- 'real life brokenness' features enabled
- signal based exception detection
- copying garbage collection
- bidirectional object layout
- inline-threaded interpreter

---

### Post by lupinesoul on 2008-07-18
^ Apparently, the Java version.

---

### Post by lupinesoul on 2008-07-18
Nevermind... I just found out about the true power of Synaptic.

---

