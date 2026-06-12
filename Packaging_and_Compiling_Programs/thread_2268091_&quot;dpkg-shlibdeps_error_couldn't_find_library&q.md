---
title: "&quot;dpkg-shlibdeps: error: couldn't find library&quot;"
date: 2015-03-06
forum: Packaging and Compiling Programs
---

### Post by Y_Ernst on 2015-03-06
I got following feedback from the Ubuntu-App Review Team and would like to reproduce/understand the problem: 

```
I've checked your package, seems it still has some issues with dependencies. I got the following error:
dpkg-shlibdeps: error: couldn't find library libpthread.so.0 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libIlmThread-2_1.so.11 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libm.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libIlmThread-2_1.so.11 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libc.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libIlmThread-2_1.so.11 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libgcc_s.so.1 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libIlmThread-2_1.so.11 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libm.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libalut.so.0 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libopenal.so.1 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libalut.so.0 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libc.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libalut.so.0 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libc.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/memoryTheMinorPlanets (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libz.so.1 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libgnutls.so.28 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libp11-kit.so.0 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libgnutls.so.28 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libtasn1.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libgnutls.so.28 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libnettle.so.4 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libgnutls.so.28 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libhogweed.so.2 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libgnutls.so.28 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libgmp.so.10 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libgnutls.so.28 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libc.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libgnutls.so.28 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libm.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/memoryop (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libbsd.so.0 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/memoryop (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libGL.so.1 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/memoryop (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libopenal.so.1 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/memoryop (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libvorbisfile.so.3 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/memoryop (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libz.so.1 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/memoryop (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libfreetype.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/memoryop (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libcrypto.so.1.0.0 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/memoryop (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libgcc_s.so.1 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/memoryop (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libpthread.so.0 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/memoryop (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libc.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/memoryop (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libssl.so.1.0.0 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libssh2.so.1 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libcrypto.so.1.0.0 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libssh2.so.1 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libz.so.1 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libssh2.so.1 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libc.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libssh2.so.1 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libc.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libBlocksRuntime.so.0 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libm.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libImath-2_1.so.11 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libc.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libImath-2_1.so.11 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libgcc_s.so.1 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libImath-2_1.so.11 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libc.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libmsgpack.so.4 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libm.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libicui18n.so.53 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libgcc_s.so.1 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libicui18n.so.53 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libc.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libicui18n.so.53 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libpthread.so.0 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libpthread_workqueue.so.0 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library librt.so.1 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libpthread_workqueue.so.0 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libc.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libpthread_workqueue.so.0 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libpthread.so.0 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libdispatch.so.0 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libc.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libdispatch.so.0 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libpthread.so.0 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libdispatch.so.1.2 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libc.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libdispatch.so.1.2 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libGL.so.1 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libGLEW.so.1.11 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libc.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libGLEW.so.1.11 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libpthread.so.0 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libkqueue.so.0 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library librt.so.1 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libkqueue.so.0 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libc.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libkqueue.so.0 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library ld-linux-x86-64.so.2 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libkqueue.so.0 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libm.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libHalf.so.11 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libc.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libHalf.so.11 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libgcc_s.so.1 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libHalf.so.11 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libpthread.so.0 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libobjc.so.4.6 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libm.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libobjc.so.4.6 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libgcc_s.so.1 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libobjc.so.4.6 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libc.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libobjc.so.4.6 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libm.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libIexMath-2_1.so.11 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libc.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libIexMath-2_1.so.11 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libgcc_s.so.1 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libIexMath-2_1.so.11 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libssl.so.1.0.0 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libcurl.so.4 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libcrypto.so.1.0.0 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libcurl.so.4 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libgssapi_krb5.so.2 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libcurl.so.4 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libkrb5.so.3 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libcurl.so.4 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libk5crypto.so.3 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libcurl.so.4 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libcom_err.so.2 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libcurl.so.4 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libz.so.1 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libcurl.so.4 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libpthread.so.0 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libcurl.so.4 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libc.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libcurl.so.4 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libm.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libobjcxx.so.4.6 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libgcc_s.so.1 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libobjcxx.so.4.6 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libc.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libobjcxx.so.4.6 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libpthread.so.0 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libicuuc.so.53 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libdl.so.2 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libicuuc.so.53 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libm.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libicuuc.so.53 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libgcc_s.so.1 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libicuuc.so.53 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libc.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libicuuc.so.53 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libX11.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libglfw.so.3 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libpthread.so.0 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libglfw.so.3 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library librt.so.1 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libglfw.so.3 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libXrandr.so.2 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libglfw.so.3 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libXi.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libglfw.so.3 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libXxf86vm.so.1 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libglfw.so.3 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libm.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libglfw.so.3 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libXcursor.so.1 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libglfw.so.3 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libGL.so.1 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libglfw.so.3 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libc.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libglfw.so.3 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libgmp.so.10 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libgnustep-base.so.1.24 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libavahi-common.so.3 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libgnustep-base.so.1.24 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libavahi-client.so.3 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libgnustep-base.so.1.24 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libxslt.so.1 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libgnustep-base.so.1.24 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libxml2.so.2 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libgnustep-base.so.1.24 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libz.so.1 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libgnustep-base.so.1.24 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libm.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libgnustep-base.so.1.24 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libdl.so.2 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libgnustep-base.so.1.24 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libffi.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libgnustep-base.so.1.24 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library librt.so.1 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libgnustep-base.so.1.24 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libpthread.so.0 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libgnustep-base.so.1.24 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libgcc_s.so.1 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libgnustep-base.so.1.24 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libc.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libgnustep-base.so.1.24 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libm.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libstdc++.so.6 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libc.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libstdc++.so.6 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library ld-linux-x86-64.so.2 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libstdc++.so.6 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libgcc_s.so.1 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libstdc++.so.6 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libm.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libIex-2_1.so.11 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libc.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libIex-2_1.so.11 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libgcc_s.so.1 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libIex-2_1.so.11 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libz.so.1 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libIlmImf-Imf_2_1.so.21 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libpthread.so.0 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libIlmImf-Imf_2_1.so.21 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libm.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libIlmImf-Imf_2_1.so.21 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libc.so.6 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libIlmImf-Imf_2_1.so.21 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: error: couldn't find library libgcc_s.so.1 needed by debian/memorytheminorplanets/opt/memorytheminorplanets/libIlmImf-Imf_2_1.so.21 (ELF format: 'elf64-x86-64'; RPATH: '')
dpkg-shlibdeps: warning: package could avoid a useless dependency if debian/memorytheminorplanets/opt/memorytheminorplanets/memoryop was not linked against libmsgpack.so.4 (it uses none of the library's symbols)
dpkg-shlibdeps: warning: package could avoid a useless dependency if debian/memorytheminorplanets/opt/memorytheminorplanets/memoryop was not linked against libIexMath-2_1.so.11 (it uses none of the library's symbols)
dpkg-shlibdeps: warning: package could avoid a useless dependency if debian/memorytheminorplanets/opt/memorytheminorplanets/memoryop debian/memorytheminorplanets/opt/memorytheminorplanets/libIlmImf-Imf_2_1.so.21 were not linked against libImath-2_1.so.11 (they use none of the library's symbols)
dpkg-shlibdeps: error: cannot continue due to the errors listed above
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
```

How was dpkg called and how can I prevent this bug? I'm using pbuilder (with build essentials) and the DEB package is created (with some warnings) on my ubuntu system.
   

My control file looks like this:
```

Source: memorytheminorplanets
Section: devel
Priority: optional
Maintainer: yousry <[REMOVED]>
Build-Depends: libc6, libavahi-client3, libavahi-common3, libbsd0, libcomerr2, libssl1.0.0, libffi6, libfreetype6, libgcc1, libgl1-mesa-glx, libgmp10, libgssapi-krb5-2, libhogweed2, libk5crypto3, libkrb5-3, libnettle4, libopenal1, libp11-kit0, libssl1.0.0, libtasn1-6, libvorbisfile3, libx11-6, libxcursor1, libxi6, libxml2, libxrandr2, libxslt1.1, libxxf86vm1, zlib1g, libalut0, debhelper
Standards-Version: 3.9.4
Homepage: [REMOVED]

Package: memorytheminorplanets
Architecture: any
Depends: ${shlibs:Depends}, ${misc:Depends}
Description:  Memory – The Minor Planets
 In 2005 a Norwegian mathematician presented this device to the public. He invented it to clearly distinguish between humans and descendants of an "alien invasion" that took allegedly place thousands of years ago. Interestingly, almost nobody from the audience was able to finish all 15 rounds of this mechanical game.
```


And my rules file like this:

```
#!/usr/bin/make -f
# -*- makefile -*-

# Uncomment this to turn on verbose mode.
#export DH_VERBOSE=1

%:
	dh $@ 

override_dh_shlibdeps:
	LD_LIBRARY_PATH=$(LD_LIBRARY_PATH):debian/memorytheminorplanets/opt/memorytheminorplanets dh_shlibdeps --dpkg-shlibdeps-params="--ignore-missing-info"

```

At first I used dh_shlibdeps with the -l (library path) option but it seems that this isn't available on the reference system. As alternative I added the environment path to the build-rules but it seems that this is also ignored. 

For an alternative source-code upload it would be necessary to use clang 3.6+ with the llvm runtime. (The  application needs a modern libobjc). With PKGBUILD this isn't a problem but I have no idea how this could be done with deb.  

Any help would be appreciated.

The package can also be found here: [URL="http://virtualhorde.com/BIN/memorytheminorplanets-1.1ubuntu4-debsrc.tar.gz"]http://virtualhorde.com/BIN/memorytheminorplanets-1.1ubuntu4-debsrc.tar.gz
[/URL]

---

### Post by Y_Ernst on 2015-03-26
I removed several virtual packages from the control file.
I recorded and uploaded my build-steps in a video here: [https://youtu.be/v0EQidzk-V4](https://youtu.be/v0EQidzk-V4) 
Any improvement suggestions are welcome.

---

### Post by Y_Ernst on 2015-03-30
Here comes the weekly progress report.

The last response from the build team was:

> Hi!
There are still missing build-dependencies, please try to build it on a clean pbuilder.
Thanks!


My Response:

I uploaded a video where I demonstrate the build with a cleaned pbuilder cache:
[https://youtu.be/dvmJFahh8i0]("https://youtu.be/dvmJFahh8i0")

---

### Post by Y_Ernst on 2015-03-30
If you want to try it by yourself. The package can be found here:

[http://virtualhorde.com/BIN/memorytheminorplanets-1.1ubuntu5-debsrc.tar.gz](http://virtualhorde.com/BIN/memorytheminorplanets-1.1ubuntu5-debsrc.tar.gz)

```
sha256sum memorytheminorplanets-1.1ubuntu5-debsrc.tar.gz
88c54cb335096235137b8ff9359f8c40b52abf41fe4dac19d2d5107539e673ce  memorytheminorplanets-1.1ubuntu5-debsrc.tar.gz
```

If you don't want to watch the boring video.

*To clear the pbuilder cache and base container I removed the /var/cache/pbuilder folder.*

---

