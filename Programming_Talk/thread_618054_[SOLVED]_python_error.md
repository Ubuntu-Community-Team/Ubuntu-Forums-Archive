---
title: "[SOLVED] python error"
date: 2007-11-20
forum: Programming Talk
---

### Post by finer recliner on 2007-11-20
Could someone PLEASE help me solve this problem. occasionally i start getting errors regarding glibc (see below error message and backtrace) and my program wont run. eventually it goes away on its own. unfortunately, i dont have time to just wait around for my computer to fix itself. i've tried restarting the computer and commenting out lines of code. but nothing seems to manually make it go away. is there a cache or something i need to clear? does this error have to do with a video driver (currently using ati's flgrx). or maybe a python library i have installed?:confused:

if you care to look, my code is posted here:
[http://www.acsu.buffalo.edu/~dhfine/final.py](http://www.acsu.buffalo.edu/~dhfine/final.py)


any help is appreciated. thanks.

```
$ python final.py 
*** glibc detected *** python: munmap_chunk(): invalid pointer: 0x08585980 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7e1292b]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb7982d81]
/usr/lib/libapt-pkg-libc6.6-6.so.4.5(_Z13ReadConfigDirR13ConfigurationRKSsbj+0x317)[0xb6a913b7]
/usr/lib/libapt-pkg-libc6.6-6.so.4.5(_Z13pkgInitConfigR13Configuration+0x82b)[0xb6ac69db]
/usr/lib/python2.5/site-packages/apt_pkg.so[0xb6b50ac2]
python(PyEval_EvalFrameEx+0x5d0c)[0x80c8eec]
python(PyEval_EvalCodeEx+0x775)[0x80ca115]
python(PyEval_EvalCode+0x57)[0x80ca187]
python(PyImport_ExecCodeModuleEx+0xac)[0x80de9ac]
python[0x80df306]
python[0x80e09ce]
python[0x80df98b]
python[0x80dfebc]
python[0x80e0068]
python(PyImport_ImportModuleLevel+0x27)[0x80e04f7]
python[0x80c1db4]
python(PyObject_Call+0x27)[0x805c9e7]
python(PyEval_CallObjectWithKeywords+0x6c)[0x80c232c]
python(PyEval_EvalFrameEx+0x18bd)[0x80c4a9d]
python(PyEval_EvalCodeEx+0x775)[0x80ca115]
python(PyEval_EvalCode+0x57)[0x80ca187]
python(PyImport_ExecCodeModuleEx+0xac)[0x80de9ac]
python[0x80df306]
python[0x80df98b]
python[0x80dfe3e]
python[0x80e0068]
python(PyImport_ImportModuleLevel+0x27)[0x80e04f7]
python[0x80c1db4]
python(PyObject_Call+0x27)[0x805c9e7]
python(PyEval_CallObjectWithKeywords+0x6c)[0x80c232c]
python(PyEval_EvalFrameEx+0x18bd)[0x80c4a9d]
python(PyEval_EvalCodeEx+0x775)[0x80ca115]
python(PyEval_EvalCode+0x57)[0x80ca187]
python(PyImport_ExecCodeModuleEx+0xac)[0x80de9ac]
python[0x80df306]
python[0x80df98b]
python[0x80dfe3e]
python[0x80e0068]
python(PyImport_ImportModuleLevel+0x27)[0x80e04f7]
python[0x80c1db4]
python(PyObject_Call+0x27)[0x805c9e7]
python(PyEval_CallObjectWithKeywords+0x6c)[0x80c232c]
python(PyEval_EvalFrameEx+0x18bd)[0x80c4a9d]
python(PyEval_EvalCodeEx+0x775)[0x80ca115]
python(PyEval_EvalCode+0x57)[0x80ca187]
python(PyImport_ExecCodeModuleEx+0xac)[0x80de9ac]
python[0x80df306]
python[0x80df98b]
python[0x80dfe3e]
python[0x80e00b0]
python(PyImport_ImportModuleLevel+0x27)[0x80e04f7]
python[0x80c1db4]
python(PyObject_Call+0x27)[0x805c9e7]
python(PyEval_CallObjectWithKeywords+0x6c)[0x80c232c]
python(PyEval_EvalFrameEx+0x18bd)[0x80c4a9d]
python(PyEval_EvalCodeEx+0x775)[0x80ca115]
python(PyEval_EvalCode+0x57)[0x80ca187]
python(PyImport_ExecCodeModuleEx+0xac)[0x80de9ac]
python[0x80df306]
python[0x80e09ce]
python[0x80df98b]
python[0x80dfe3e]
python[0x80e0068]
======= Memory map: ========
08048000-0813f000 r-xp 00000000 08:06 867536     /usr/bin/python2.5
0813f000-08164000 rw-p 000f6000 08:06 867536     /usr/bin/python2.5
08164000-0877a000 rw-p 08164000 00:00 0          [heap]
b6a6a000-b6b36000 r-xp 00000000 08:06 868328     /usr/lib/libapt-pkg-libc6.6-6.so.4.5.0
b6b36000-b6b39000 rw-p 000cb000 08:06 868328     /usr/lib/libapt-pkg-libc6.6-6.so.4.5.0
b6b48000-b6b69000 r-xp 00000000 08:06 1000905    /usr/lib/python2.5/site-packages/apt_pkg.so
b6b69000-b6b6c000 rw-p 00020000 08:06 1000905    /usr/lib/python2.5/site-packages/apt_pkg.so
b6b6c000-b6b8f000 r-xp 00000000 08:06 1001481    /usr/lib/python2.5/site-packages/_xmlplus/parsers/pyexpat.so
b6b8f000-b6b92000 rw-p 00023000 08:06 1001481    /usr/lib/python2.5/site-packages/_xmlplus/parsers/pyexpat.so
b6b92000-b6cbd000 r-xp 00000000 08:06 932439     /usr/lib/i686/cmov/libcrypto.so.0.9.8
b6cbd000-b6cd2000 rw-p 0012a000 08:06 932439     /usr/lib/i686/cmov/libcrypto.so.0.9.8
b6cd2000-b6cd5000 rw-p b6cd2000 00:00 0 
b6cd5000-b6d12000 r-xp 00000000 08:06 932440     /usr/lib/i686/cmov/libssl.so.0.9.8
b6d12000-b6d16000 rw-p 0003c000 08:06 932440     /usr/lib/i686/cmov/libssl.so.0.9.8
b6d19000-b6d1d000 r-xp 00000000 08:06 1000817    /usr/lib/python2.5/lib-dynload/zlib.so
b6d1d000-b6d1e000 rw-p 00004000 08:06 1000817    /usr/lib/python2.5/lib-dynload/zlib.so
b6d1e000-b6d21000 r-xp 00000000 08:06 1000771    /usr/lib/python2.5/lib-dynload/_locale.so
b6d21000-b6d22000 rw-p 00003000 08:06 1000771    /usr/lib/python2.5/lib-dynload/_locale.so
b6d22000-b6d24000 r-xp 00000000 08:06 1000796    /usr/lib/python2.5/lib-dynload/grp.so
b6d24000-b6d25000 rw-p 00001000 08:06 1000796    /usr/lib/python2.5/lib-dynload/grp.so
b6d25000-b6dd5000 r-xp 00000000 08:06 2125888    /usr/lib/libstdc++.so.5.0.7
b6dd5000-b6dda000 rw-p 000af000 08:06 2125888    /usr/lib/libstdc++.so.5.0.7
b6dda000-b6ddf000 rw-p b6dda000 00:00 0 
b6ddf000-b766d000 r-xp 00000000 08:06 212578     /usr/lib/dri/fglrx_dri.so
b766d000-b76b8000 rw-p 0088e000 08:06 212578     /usr/lib/dri/fglrx_dri.so
b76b8000-b7742000 rw-p b76b8000 00:00 0 
b7742000-b7743000 r-xp 00000000 08:06 1000780    /usr/lib/python2.5/lib-dynload/_weakref.so
b7743000-b7744000 rw-p 00000000 08:06 1000780    /usr/lib/python2.5/lib-dynload/_weakref.so
b7744000-b77e6000 rw-p b7744000 00:00 0 
b77e6000-b77f0000 r-xp 00000000 08:06 1000775    /usr/lib/python2.5/lib-dynload/_socket.so
b77f0000-b77f3000 rw-p 0000a000 08:06 1000775    /usr/lib/python2.5/lib-dynload/_socket.so
b77f3000-b77fa000 r-xp 00000000 08:06 1291928    /lib/tls/i686/cmov/librt-2.6.1.so
b77fa000-b77fc000 rw-p 00006000 08:06 1291928    /lib/tls/i686/cmov/librt-2.6.1.so
b77fc000-b77ff000 r-xp 00000000 08:06 1000777    /usr/lib/python2.5/lib-dynload/_ssl.so
b77ff000-b7800000 rw-p 00003000 08:06 1000777    /usr/lib/python2.5/lib-dynload/_ssl.so
b7800000-b7803000 r-xp 00000000 08:06 1000810    /usr/lib/python2.5/lib-dynload/select.so
b7803000-b7804000 rw-p 00002000 08:06 1000810    /usr/lib/python2.5/lib-dynload/select.so
b7804000-b780b000 rwxp b7804000 00:00 0 
b780b000-b788d000 rw-p b780b000 00:00 0 
b788d000-b78bb000 r-xp 00000000 08:06 868565     /usr/lib/libglut.so.3.8.0
b78bb000-b78c0000 rw-p 0002d000 08:06 868565     /usr/lib/libglut.so.3.8.0
b78c0000-b78ca000 r-xp 00000000 08:06 1291875    /lib/libgcc_s.so.1
b78ca000-b78cb000 rw-p 0000a000 08:06 1291875    /lib/libgcc_s.so.1
b78cb000-b79b3000 r-xp 00000000 08:06 868973     /usr/lib/libstdc++.so.6.0.9
b79b3000-b79b6000 r--p 000e8000 08:06 868973     /usr/lib/libstdc++.so.6.0.9
b79b6000-b79b8000 rw-p 000eb000 08:06 868973     /usr/lib/libstdc++.so.6.0.9
b79b8000-b79be000 rw-p b79b8000 00:00 0 
b79be000-b7a40000 r-xp 00000000 08:06 868232     /usr/lib/libGLU.so.1.3.070001
b7a40000-b7a41000 rw-p 00081000 08:06 868232     /usr/lib/libGLU.so.1.3.070001
b7a41000-b7a45000 r-xp 00000000 08:06 868276     /usr/lib/libXdmcp.so.6.0.0
b7a45000-b7a46000 rw-p 00003000 08:06 868276     /usr/lib/libXdmcp.so.6.0.0
b7a46000-b7a48000 r-xp 00000000 08:06 868265     /usr/lib/libXau.so.6.0.0
b7a48000-b7a49000 rw-p 00001000 08:06 868265     /usr/lib/libXau.so.6.0.0
b7a49000-b7b36000 r-xp 00000000 08:06 868259     /usr/lib/libX11.so.6.2.0
b7b36000-b7b3a000 rw-p 000ed000 08:06 868259     /usr/lib/libX11.so.6.2.0
b7b3a000-b7b47000 r-xp 00000000 08:06 868280     /usr/lib/libXext.so.6.4.0
b7b47000-b7b48000 rw-p 0000d000 08:06 868280     /usr/lib/libXext.so.6.4.0
b7b48000-b7be0000 r-xp 00000000 08:06 2125989    /usr/lib/libGL.so.1.2
b7be0000-b7be5000 rw-p 00098000 08:06 2125989    /usr/lib/libGL.so.1.2
b7be5000-b7be8000 rw-p b7be5000 00:00 0 
b7be9000-b7bed000 r-xp 00000000 08:06 1000788    /usr/lib/python2.5/lib-dynload/collections.so
b7bed000-b7bee000 rw-p 00004000 08:06 1000788    /usr/lib/python2.5/lib-dynload/collections.so
b7bee000-b7bf1000 r-xp 00000000 08:06 1000786    /usr/lib/python2.5/lib-dynload/cStringIO.so
b7bf1000-b7bf2000 rw-p 00003000 08:06 1000786    /usr/lib/python2.5/lib-dynload/cStringIO.so
b7bf2000-b7bf5000 r-xp 00000000 08:06 1000815    /usr/lib/python2.5/lib-dynload/time.so
b7bf5000-b7bf7000 rw-p 00002000 08:06 1000815    /usr/lib/python2.5/lib-dynload/time.so
b7bf7000-b7bfc000 r-xp 00000000 08:06 1000778    /usr/lib/python2.5/lib-dynload/_struct.so
b7bfc000-b7bfd000 rw-p 00005000 08:06 1000778    /usr/lib/python2.5/lib-dynload/_struct.so
b7bfd000-b7c11000 r-xp 00000000 08:06 1000762    /usr/lib/python2.5/lib-dynload/_ctypes.so
b7c11000-b7c13000 rw-p 00014000 08:06 1000762    /usr/lib/python2.5/lib-dynload/_ctypes.so
b7c13000-b7c18000 r-xp 00000000 08:06 1000803    /usr/lib/python2.5/lib-dynload/operator.so
b7c18000-b7c19000 rw-p 00005000 08:06 1000803    /usr/lib/python2.5/lib-dynload/operator.so
b7c19000-b7c2d000 r-xp 00000000 08:06 869043     /usr/lib/libz.so.1.2.3.3
b7c2d000-b7c2e000 rw-p 00013000 08:06 869043     /usr/lib/libz.so.1.2.3.3
b7c2e000-b7c4d000 r-xp 00000000 08:06 868753     /usr/lib/libjpeg.so.62.0.0
b7c4d000-b7c4e000 rw-p 0001e000 08:06 868753     /usr/lib/libjpeg.so.62.0.0
b7c4f000-b7c53000 r-xp 00000000 08:06 1000812    /usr/lib/python2.5/lib-dynload/strop.so
b7c53000-b7c55000 rw-p 00003000 08:06 1000812    /usr/lib/python2.5/lib-dynload/strop.so
b7c55000-b7c5b000 r-xp 00000000 08:06 1000781    /usr/lib/python2.5/lib-dynload/array.so
b7c5b000-b7c5d000 rw-p 00006000 08:06 1000781    /usr/lib/python2.5/lib-dynload/array.so
b7c5d000-b7c8f000 r-xp 00000000 08:06 1013927    /usr/lib/python2.5/site-packages/PIL/_imaging.so
b7c8f000-b7c92000 rw-p 00032000 08:06 1013927    /usr/lib/python2.5/site-packages/PIL/_imaging.so
b7c92000-b7cdb000 rw-p b7c92000 00:00 0 
b7cdc000-b7ce3000 r--s 00000000 08:06 866792     /usr/lib/gconv/gconv-modules.cache
b7ce3000-b7d22000 r--p 00000000 08:06 932982     /usr/lib/locale/en_US.utf8/LC_CTYPE
b7d22000-b7da5000 rw-p b7d22000 00:00 0 
b7da5000-b7ee9000 r-xp 00000000 08:06 1291835    /lib/tls/i686/cmov/libc-2.6.1.so
b7ee9000-b7eea000 r--p 00143000 08:06 1291835    /lib/tls/i686/cmov/libc-2.6.1.so
b7eea000-b7eec000 rw-p 00144000 08:06 1291835    /lib/tls/i686/cmov/libc-2.6.1.so
b7eec000-b7eef000 rw-p b7eec000 00:00 0 
b7eef000-b7f12000 r-xp 00000000 08:06 1291867    /lib/tls/i686/cmov/libm-2.6.1.so
b7f12000-b7f14000 rw-p 00023000 08:06 1291867    /lib/tls/i686/cmov/libm-2.6.1.so
b7f14000-b7f16000 r-xp 00000000 08:06 1291947    /lib/tls/i686/cmov/libutil-2.6.1.so
b7f16000-b7f18000 rw-p 00001000 08:06 1291947    /lib/tls/i686/cmov/libutil-2.6.1.so
b7f18000-b7f19000 rw-p b7f18000 00:00 0 
b7f19000-b7f1b000 r-xp 00000000 08:06 1291860    /lib/tls/i686/cmov/libdl-2.6.1.so
b7f1b000-b7f1d000 rw-p 00001000 08:06 1291860    /lib/tls/i686/cmov/libdl-2.6.1.so
b7f1d000-b7f31000 r-xp 00000000 08:06 1291920    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7f31000-b7f33000 rw-p 00013000 08:06 1291920    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7f33000-b7f35000 rw-p b7f33000 00:00 0 
b7f35000-b7f37000 r-xp 00000000 08:06 1000793    /usr/lib/python2.5/lib-dynload/fcntl.so
b7f37000-b7f38000 rw-p 00002000 08:06 1000793    /usr/lib/python2.5/lib-dynload/fcntl.so
b7f38000-b7f3a000 r-xp 00000000 08:06 1000774    /usr/lib/python2.5/lib-dynload/_random.so
b7f3a000-b7f3b000 rw-p 00002000 08:06 1000774    /usr/lib/python2.5/lib-dynload/_random.so
b7f3b000-b7f3f000 r-xp 00000000 08:06 1000783    /usr/lib/python2.5/lib-dynload/binascii.so
b7f3f000-b7f40000 rw-p 00003000 08:06 1000783    /usr/lib/python2.5/lib-dynload/binascii.so
b7f40000-b7f43000 r-xp 00000000 08:06 1000800    /usr/lib/python2.5/lib-dynload/math.so
b7f43000-b7f44000 rw-p 00002000 08:06 1000800    /usr/lib/python2.5/lib-dynload/math.so
b7f44000-b7f46000 rw-p b7f44000 00:00 0 
b7f46000-b7f60000 r-xp 00000000 08:06 1291821    /lib/ld-2.6.1.so
b7f60000-b7f62000 rw-p 00019000 08:06 1291821    /lib/ld-2.6.1.so
bfc9d000-bfcc7000 rwxp bfc9d000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

```

---

### Post by finer recliner on 2007-11-20
it turns out if i comment out the following line (line 23):
```

tex = Texture2D("particle.png")

```
the problem goes away...

any workaround ideas?

---

### Post by finer recliner on 2007-11-20
nevermind. it turns out i was missing a custom library my instructor created. very bad runtime error when all i needed to know what i was trying to instantiate a class that wasnt defined.... :-/

---

