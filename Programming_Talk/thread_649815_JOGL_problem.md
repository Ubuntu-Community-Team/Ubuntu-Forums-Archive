---
title: "JOGL problem"
date: 2007-12-25
forum: Programming Talk
---

### Post by LlamaCyrus on 2007-12-25
Hello everybody!

I have installed Java 1.4.2 and JOGL (atleast i thought i had installed JOGL)

I copied files to the Java folders, jogl.jar to the ext folder and jogl.so to the i386 folder.

Now i try to compile JOGL code, it compiles correctly (i don't get any errors)

But if i try to open the code with the java command line, i get an huge error!

Sorry for posting this huge error here, but i'm pretty desperate!


An unexpected exception has been detected in native code outside the VM.
Unexpected Signal : 11 occurred at PC=0xAAE38157
Function=XVisualIDFromVisual+0x7
Library=/usr/lib/libX11.so.6

Current Java thread:
	at net.java.games.jogl.impl.JAWT_DrawingSurface.GetDrawingSurfaceInfo0(Native Method)
	at net.java.games.jogl.impl.JAWT_DrawingSurface.GetDrawingSurfaceInfo(JAWT_DrawingSurface.java:42)
	at net.java.games.jogl.impl.x11.X11OnscreenGLContext.lockSurface(X11OnscreenGLContext.java:167)
	at net.java.games.jogl.impl.x11.X11OnscreenGLContext.makeCurrent(X11OnscreenGLContext.java:108)
	- locked <0xab9501a8> (a net.java.games.jogl.impl.x11.X11OnscreenGLContext)
	at net.java.games.jogl.impl.GLContext.invokeGL(GLContext.java:162)
	- locked <0xab9501a8> (a net.java.games.jogl.impl.x11.X11OnscreenGLContext)
	at net.java.games.jogl.GLCanvas.reshape(GLCanvas.java:105)
	at java.awt.Component.setBounds(Component.java:1664)
	at java.awt.BorderLayout.layoutContainer(BorderLayout.java:691)
	- locked <0xabdd0d98> (a java.awt.Component$AWTTreeLock)
	at java.awt.Container.layout(Container.java:1020)
	at java.awt.Container.doLayout(Container.java:1010)
	at java.awt.Container.validateTree(Container.java:1092)
	at java.awt.Container.validateTree(Container.java:1099)
	at java.awt.Container.validateTree(Container.java:1099)
	at java.awt.Container.validateTree(Container.java:1099)
	at java.awt.Container.validate(Container.java:1067)
	- locked <0xabdd0d98> (a java.awt.Component$AWTTreeLock)
	at java.awt.Window.show(Window.java:461)
	at java.awt.Component.show(Component.java:1133)
	at java.awt.Component.setVisible(Component.java:1088)
	at VertexArrayTest.<init>(VertexArrayTest.java:60)
	at VertexArrayTest.main(VertexArrayTest.java:84)

Dynamic libraries:
08048000-08057000 r-xp 00000000 08:02 1048875    /usr/lib/j2se/1.4/jre/bin/java
08057000-08059000 rwxp 0000e000 08:02 1048875    /usr/lib/j2se/1.4/jre/bin/java
08059000-082a4000 rwxp 08059000 00:00 0          [heap]
aa901000-aa9e9000 r-xp 00000000 08:02 526316     /usr/lib/libstdc++.so.6.0.9
aa9e9000-aa9ec000 r-xp 000e8000 08:02 526316     /usr/lib/libstdc++.so.6.0.9
aa9ec000-aa9ee000 rwxp 000eb000 08:02 526316     /usr/lib/libstdc++.so.6.0.9
aa9f4000-aaa76000 r-xp 00000000 08:02 525575     /usr/lib/libGLU.so.1.3.070001
aaa76000-aaa77000 rwxp 00081000 08:02 525575     /usr/lib/libGLU.so.1.3.070001
aaa77000-aaad5000 r-xp 00000000 08:02 525571     /usr/lib/libGL.so.1.2
aaad5000-aaad7000 rwxp 0005d000 08:02 525571     /usr/lib/libGL.so.1.2
aaad8000-aab99000 r-xp 00000000 08:02 822330     /usr/lib/j2se/1.4/jre/lib/i386/libjogl.so
aab99000-aab9b000 rwxp 000c1000 08:02 822330     /usr/lib/j2se/1.4/jre/lib/i386/libjogl.so
aac1c000-aac22000 r-xs 00000000 08:02 1294421    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
aac22000-aac25000 r-xs 00000000 08:02 1294974    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
aac25000-aac29000 r-xs 00000000 08:02 1294973    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
aac29000-aac2a000 r-xs 00000000 08:02 1294972    /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
aac2a000-aac2b000 r-xs 00000000 08:02 1294971    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
aac2b000-aac2e000 r-xs 00000000 08:02 1294970    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
aac2e000-aac2f000 r-xs 00000000 08:02 1294967    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
aac2f000-aac35000 r-xs 00000000 08:02 1294878    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
aac35000-aac37000 r-xs 00000000 08:02 1294965    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
aac37000-aac3f000 r-xs 00000000 08:02 1294964    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
aac3f000-aac45000 r-xs 00000000 08:02 1294963    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
aac45000-aac46000 r-xs 00000000 08:02 1294961    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
aac46000-aac48000 r-xs 00000000 08:02 1294959    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
aac48000-aac4e000 r-xs 00000000 08:02 1294958    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
aac4e000-aac52000 r-xs 00000000 08:02 1294406    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
aac52000-aac54000 r-xs 00000000 08:02 1294954    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
aac54000-aac55000 r-xs 00000000 08:02 1295008    /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
aac55000-aac56000 r-xs 00000000 08:02 1295007    /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
aac56000-aac57000 r-xs 00000000 08:02 1295003    /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
aac57000-aac5a000 r-xs 00000000 08:02 1295002    /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
aac5a000-aac5d000 r-xs 00000000 08:02 1295000    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
aac5d000-aac5f000 r-xs 00000000 08:02 1294999    /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
aac5f000-aac60000 r-xs 00000000 08:02 1294998    /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
aac60000-aac61000 r-xs 00000000 08:02 1294996    /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
aac61000-aac62000 r-xs 00000000 08:02 1294995    /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
aac62000-aac67000 r-xs 00000000 08:02 1294994    /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
aac67000-aac6c000 r-xs 00000000 08:02 1294992    /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
aac6c000-aac6e000 r-xs 00000000 08:02 1294991    /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
aac6e000-aac71000 r-xs 00000000 08:02 1294989    /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
aac71000-aac72000 r-xs 00000000 08:02 1294988    /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
aac72000-aac73000 r-xs 00000000 08:02 1294987    /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
aac73000-aac76000 r-xs 00000000 08:02 1294986    /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
aac76000-aac7c000 r-xs 00000000 08:02 1294984    /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
aac7c000-aac7d000 r-xs 00000000 08:02 1294982    /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
aac7d000-aac85000 r-xs 00000000 08:02 1296838    /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
aac94000-aac9e000 r-xp 00000000 08:02 1114179    /lib/libgcc_s.so.1
aac9e000-aac9f000 rwxp 0000a000 08:02 1114179    /lib/libgcc_s.so.1
aac9f000-aaca8000 r-xp 00000000 08:02 525774     /usr/lib/libdrm.so.2.3.0
aaca8000-aaca9000 rwxp 00008000 08:02 525774     /usr/lib/libdrm.so.2.3.0
aaca9000-aacab000 r-xp 00000000 08:02 525617     /usr/lib/libXdamage.so.1.1.0
aacab000-aacac000 rwxp 00001000 08:02 525617     /usr/lib/libXdamage.so.1.1.0
aacac000-aacb0000 r-xp 00000000 08:02 525659     /usr/lib/libXxf86vm.so.1.0.0
aacb0000-aacb1000 rwxp 00003000 08:02 525659     /usr/lib/libXxf86vm.so.1.0.0
aad32000-aad36000 r-xp 00000000 08:02 525625     /usr/lib/libXfixes.so.3.1.0
aad36000-aad37000 rwxp 00003000 08:02 525625     /usr/lib/libXfixes.so.3.1.0
aad37000-aad3e000 r-xp 00000000 08:02 525645     /usr/lib/libXrender.so.1.3.0
aad3e000-aad3f000 rwxp 00006000 08:02 525645     /usr/lib/libXrender.so.1.3.0
aad3f000-aad47000 r-xp 00000000 08:02 525615     /usr/lib/libXcursor.so.1.0.2
aad47000-aad48000 rwxp 00007000 08:02 525615     /usr/lib/libXcursor.so.1.0.2
aad55000-aadf2000 r-xp 00000000 08:02 822325     /usr/lib/j2se/1.4/jre/lib/i386/libfontmanager.so
aadf2000-aae04000 rwxp 0009d000 08:02 822325     /usr/lib/j2se/1.4/jre/lib/i386/libfontmanager.so
aae08000-aae0c000 r-xp 00000000 08:02 525619     /usr/lib/libXdmcp.so.6.0.0
aae0c000-aae0d000 rwxp 00003000 08:02 525619     /usr/lib/libXdmcp.so.6.0.0
aae0d000-aaefa000 r-xp 00000000 08:02 525602     /usr/lib/libX11.so.6.2.0
aaefa000-aaefe000 rwxp 000ed000 08:02 525602     /usr/lib/libX11.so.6.2.0
aaefe000-aaf02000 r-xp 00000000 08:02 525651     /usr/lib/libXtst.so.6.1.0
aaf02000-aaf03000 rwxp 00004000 08:02 525651     /usr/lib/libXtst.so.6.1.0
aaf03000-aaf10000 r-xp 00000000 08:02 525623     /usr/lib/libXext.so.6.4.0
aaf10000-aaf11000 rwxp 0000d000 08:02 525623     /usr/lib/libXext.so.6.4.0
aaf11000-aaf26000 r-xp 00000000 08:02 525580     /usr/lib/libICE.so.6.3.0
aaf26000-aaf28000 rwxp 00014000 08:02 525580     /usr/lib/libICE.so.6.3.0
aaf29000-aaf30000 r-xp 00000000 08:02 525598     /usr/lib/libSM.so.6.0.0
aaf30000-aaf31000 rwxp 00006000 08:02 525598     /usr/lib/libSM.so.6.0.0
aaf31000-aaf7e000 r-xp 00000000 08:02 525649     /usr/lib/libXt.so.6.0.0
aaf7e000-aaf82000 rwxp 0004c000 08:02 525649     /usr/lib/libXt.so.6.0.0
aaf82000-aaf89000 r-xp 00000000 08:02 525639     /usr/lib/libXp.so.6.2.0
aaf89000-aaf8a000 rwxp 00006000 08:02 525639     /usr/lib/libXp.so.6.2.0
aaf8c000-aaf8d000 r-xp 00000000 08:02 822314     /usr/lib/j2se/1.4/jre/lib/i386/libjawt.so
aaf8d000-aaf8e000 rwxp 00000000 08:02 822314     /usr/lib/j2se/1.4/jre/lib/i386/libjawt.so
aaf8e000-aaf90000 r-xs 00000000 08:02 1294980    /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
aaf90000-aaf94000 r-xs 00000000 08:02 1294979    /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
aaf94000-aaf97000 r-xs 00000000 08:02 1294429    /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
aaf97000-ab189000 r-xp 00000000 08:02 822309     /usr/lib/j2se/1.4/jre/lib/i386/libXm.so.3
ab189000-ab1a3000 rwxp 001f1000 08:02 822309     /usr/lib/j2se/1.4/jre/lib/i386/libXm.so.3
ab1a4000-ab20a000 r-xp 00000000 08:02 822306     /usr/lib/j2se/1.4/jre/lib/i386/libmlib_image.so
ab20a000-ab20b000 rwxp 00066000 08:02 822306     /usr/lib/j2se/1.4/jre/lib/i386/libmlib_image.so
ab20b000-ab2ec000 r-xp 00000000 08:02 822317     /usr/lib/j2se/1.4/jre/lib/i386/libawt.so
ab2ec000-ab2f5000 rwxp 000e0000 08:02 822317     /usr/lib/j2se/1.4/jre/lib/i386/libawt.so
ab319000-ab3a4000 r-xs 00000000 08:02 806019     /usr/lib/j2se/1.4/jre/lib/ext/jogl.jar
ab3a4000-ab3b2000 r-xs 00000000 08:02 806000     /usr/lib/j2se/1.4/jre/lib/ext/ldapsec.jar
ab3b2000-ab46e000 r-xs 00000000 08:02 806001     /usr/lib/j2se/1.4/jre/lib/ext/localedata.jar
ab46e000-ab48a000 r-xs 00000000 08:02 805999     /usr/lib/j2se/1.4/jre/lib/ext/sunjce_provider.jar
ab68e000-ab6cd000 r-xp 00000000 08:02 591100     /usr/lib/locale/en_US.utf8/LC_CTYPE
b5978000-b5f18000 r-xs 00000000 08:02 709060     /usr/lib/j2se/1.4/jre/lib/charsets.jar
b5f18000-b5f29000 r-xs 00000000 08:02 709058     /usr/lib/j2se/1.4/jre/lib/jce.jar
b5f29000-b6006000 r-xs 00000000 08:02 709056     /usr/lib/j2se/1.4/jre/lib/jsse.jar
b6006000-b601c000 r-xs 00000000 08:02 709062     /usr/lib/j2se/1.4/jre/lib/sunrsasign.jar
b6066000-b7a12000 r-xs 00000000 08:02 709063     /usr/lib/j2se/1.4/jre/lib/rt.jar
b7a12000-b7a23000 r-xp 00000000 08:02 822313     /usr/lib/j2se/1.4/jre/lib/i386/libzip.so
b7a23000-b7a25000 rwxp 00011000 08:02 822313     /usr/lib/j2se/1.4/jre/lib/i386/libzip.so
b7a25000-b7a44000 r-xp 00000000 08:02 822303     /usr/lib/j2se/1.4/jre/lib/i386/libjava.so
b7a44000-b7a45000 rwxp 0001f000 08:02 822303     /usr/lib/j2se/1.4/jre/lib/i386/libjava.so
b7a45000-b7a56000 r-xp 00000000 08:02 822305     /usr/lib/j2se/1.4/jre/lib/i386/libverify.so
b7a56000-b7a57000 rwxp 00011000 08:02 822305     /usr/lib/j2se/1.4/jre/lib/i386/libverify.so
b7a57000-b7a60000 r-xp 00000000 08:02 1147916    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b7a60000-b7a62000 rwxp 00008000 08:02 1147916    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b7a62000-b7a6a000 r-xp 00000000 08:02 1147918    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b7a6a000-b7a6c000 rwxp 00007000 08:02 1147918    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b7a6c000-b7a73000 r-xp 00000000 08:02 1147914    /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b7a73000-b7a75000 rwxp 00006000 08:02 1147914    /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b7a75000-b7a77000 r-xp 00000000 08:02 525608     /usr/lib/libXau.so.6.0.0
b7a77000-b7a78000 rwxp 00001000 08:02 525608     /usr/lib/libXau.so.6.0.0
b7a78000-b7a7b000 r-xs 00000000 08:02 805998     /usr/lib/j2se/1.4/jre/lib/ext/dnsns.jar
b7a7b000-b7a82000 r-xs 00000000 08:02 557289     /usr/lib/gconv/gconv-modules.cache
b7a82000-b7aa5000 r-xp 00000000 08:02 1147911    /lib/tls/i686/cmov/libm-2.6.1.so
b7aa5000-b7aa7000 rwxp 00023000 08:02 1147911    /lib/tls/i686/cmov/libm-2.6.1.so
b7aa7000-b7abb000 r-xp 00000000 08:02 1147913    /lib/tls/i686/cmov/libnsl-2.6.1.so
b7abb000-b7abd000 rwxp 00013000 08:02 1147913    /lib/tls/i686/cmov/libnsl-2.6.1.so
b7abf000-b7d80000 r-xp 00000000 08:02 1065265    /usr/lib/j2se/1.4/jre/lib/i386/client/libjvm.so
b7d80000-b7d9b000 rwxp 002c0000 08:02 1065265    /usr/lib/j2se/1.4/jre/lib/i386/client/libjvm.so
b7db3000-b7ef7000 r-xp 00000000 08:02 1147907    /lib/tls/i686/cmov/libc-2.6.1.so
b7ef7000-b7ef8000 r-xp 00143000 08:02 1147907    /lib/tls/i686/cmov/libc-2.6.1.so
b7ef8000-b7efa000 rwxp 00144000 08:02 1147907    /lib/tls/i686/cmov/libc-2.6.1.so
b7efe000-b7f00000 r-xp 00000000 08:02 1147910    /lib/tls/i686/cmov/libdl-2.6.1.so
b7f00000-b7f02000 rwxp 00001000 08:02 1147910    /lib/tls/i686/cmov/libdl-2.6.1.so
b7f02000-b7f16000 r-xp 00000000 08:02 1147921    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7f16000-b7f18000 rwxp 00013000 08:02 1147921    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7f1a000-b7f1e000 rwxs 00000000 08:02 1409166    /tmp/hsperfdata_brian/8186
b7f1e000-b7f26000 r-xp 00000000 08:02 1048865    /usr/lib/j2se/1.4/jre/lib/i386/native_threads/libhpi.so
b7f26000-b7f27000 rwxp 00007000 08:02 1048865    /usr/lib/j2se/1.4/jre/lib/i386/native_threads/libhpi.so
b7f29000-b7f43000 r-xp 00000000 08:02 1114125    /lib/ld-2.6.1.so
b7f43000-b7f45000 rwxp 00019000 08:02 1114125    /lib/ld-2.6.1.so
bf898000-bf8af000 rwxp bf898000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]

Heap at VM Abort:
Heap
 def new generation   total 576K, used 500K [0xab8d0000, 0xab970000, 0xabdb0000)
  eden space 512K,  89% used [0xab8d0000, 0xab942a50, 0xab950000)
  from space 64K,  65% used [0xab950000, 0xab95a8c0, 0xab960000)
  to   space 64K,   0% used [0xab960000, 0xab960000, 0xab970000)
 tenured generation   total 1408K, used 650K [0xabdb0000, 0xabf10000, 0xaf8d0000)
   the space 1408K,  46% used [0xabdb0000, 0xabe52a00, 0xabe52a00, 0xabf10000)
 compacting perm gen  total 4608K, used 4423K [0xaf8d0000, 0xafd50000, 0xb38d0000)
   the space 4608K,  96% used [0xaf8d0000, 0xafd21f00, 0xafd22000, 0xafd50000)

Local Time = Tue Dec 25 20:48:24 2007
Elapsed Time = 0
#
# The exception above was detected in native code outside the VM
#
# Java VM: Java HotSpot(TM) Client VM (Blackdown-1.4.2-02 mixed mode)
#

Please help me out here xD

Regards,
Brian

---

### Post by moma on 2007-12-26
I do not program or mingle with Java, but 

Have you tested the JOGL demo-programs. 
[https://jogl-demos.dev.java.net/](https://jogl-demos.dev.java.net/)

Clik on the pictures and Java loader vil automatically download and run the demos,

Here are other samples, All examples play well on this machine.
[http://ak.kiet.le.googlepages.com/theredbookinjava.html#CH01](http://ak.kiet.le.googlepages.com/theredbookinjava.html#CH01)
------

Have you installed Java Runtime (JRE) packages. You will need at least these
$ apt-cache search sun-java6  

* Install proper (restricted) driver for you graphic card.
Study step 5) of [this document....]("http://www.futuredesktop.org/")

You must have
$ glxinfo | grep -i direct
direct rendering: Yes

* Install freeglut libraries.
Study **Note 1)** of this [rant...]("http://ubuntuforums.org/showthread.php?p=3627418&posted=1#post3627418")
---------

Tell us how your test did. Then we can move on to offline JOGL.  Interesting stuff btw.
c u later.

---

### Post by jespdj on 2007-12-26
Do you have any reason why you're using an old version of Java (1.4.2)? If not, install Sun Java 6:
```
sudo apt-get install sun-java6-jdk
```
(install the JDK, not just the JRE, if you want to compile Java source code).

---

