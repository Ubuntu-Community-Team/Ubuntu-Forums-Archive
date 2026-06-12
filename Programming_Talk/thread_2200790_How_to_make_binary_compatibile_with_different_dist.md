---
title: "How to make binary compatibile with different distribution"
date: 2014-01-21
forum: Programming Talk
---

### Post by erotavlas on 2014-01-21
Hi,

I need to create an executable that works with as many as possible distribution. I read a lot of information about this and I discovered that there are two ways: static linking and dynamic linking. The first solution avoids to bring with the executable the libraries but it has some problem as the licenses. The second solution appears the more suitable.
With the dynamic linking the linker adds to the executable header ELF all the references of the libraries of which it needs and the operating system loads these libraries before executing the binary.
The command readelf -d binary shows the needed libraries
```

Dynamic section at offset 0x149d80 contains 33 entries:
  Tag        Type                         Name/Value
 0x0000000000000001 (NEEDED)             Shared library: [libopencv_highgui.so.2.4]
 0x0000000000000001 (NEEDED)             Shared library: [libopencv_imgproc.so.2.4]
 0x0000000000000001 (NEEDED)             Shared library: [libopencv_core.so.2.4]
 0x0000000000000001 (NEEDED)             Shared library: [libstdc++.so.6]
 0x0000000000000001 (NEEDED)             Shared library: [libm.so.6]
 0x0000000000000001 (NEEDED)             Shared library: [libgcc_s.so.1]
 0x0000000000000001 (NEEDED)             Shared library: [libpthread.so.0]
 0x0000000000000001 (NEEDED)             Shared library: [libc.so.6]
 0x000000000000000f (RPATH)              Library rpath: [$ORIGIN/lib]

```
while the command ldd binary shows all the libraries called from my executable.
```

linux-vdso.so.1 =>  (0x00007fffbb14c000)
    libopencv_highgui.so.2.4 => /home/user/./lib/libopencv_highgui.so.2.4 (0x00007f19398d0000)
    libopencv_imgproc.so.2.4 => /home/user/./lib/libopencv_imgproc.so.2.4 (0x00007f1939410000)
    libopencv_core.so.2.4 => /home/user/./lib/libopencv_core.so.2.4 (0x00007f1938fb7000)
    libstdc++.so.6 => /home/user/./lib/libstdc++.so.6 (0x00007f1938cb3000)
    libm.so.6 => /home/user/./lib/libm.so.6 (0x00007f19389b7000)
    libgcc_s.so.1 => /home/user/./lib/libgcc_s.so.1 (0x00007f19387a0000)
    libpthread.so.0 => /home/user/./lib/libpthread.so.0 (0x00007f1938583000)
    libc.so.6 => /home/user/./lib/libc.so.6 (0x00007f19381c3000)
    libtiff.so.4 => /usr/lib/x86_64-linux-gnu/libtiff.so.4 (0x00007f1937f49000)
    libgstreamer-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstreamer-0.10.so.0 (0x00007f1937c62000)
    libgobject-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0 (0x00007f1937a13000)
    libglib-2.0.so.0 => /lib/x86_64-linux-gnu/libglib-2.0.so.0 (0x00007f193771d000)
    libgstapp-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstapp-0.10.so.0 (0x00007f1937511000)
    libgstvideo-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstvideo-0.10.so.0 (0x00007f19372f5000)
    libdc1394.so.22 => /usr/lib/x86_64-linux-gnu/libdc1394.so.22 (0x00007f1937081000)
    libv4l1.so.0 => /usr/lib/x86_64-linux-gnu/libv4l1.so.0 (0x00007f1936e7b000)
    libavcodec.so.53 => /usr/lib/x86_64-linux-gnu/libavcodec.so.53 (0x00007f193606b000)
    libavformat.so.53 => /usr/lib/x86_64-linux-gnu/libavformat.so.53 (0x00007f1935d6a000)
    libavutil.so.51 => /usr/lib/x86_64-linux-gnu/libavutil.so.51 (0x00007f1935b4a000)
    libswscale.so.2 => /usr/lib/x86_64-linux-gnu/libswscale.so.2 (0x00007f1935904000)
    librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007f19356fb000)
    libgomp.so.1 => /usr/lib/x86_64-linux-gnu/libgomp.so.1 (0x00007f19354ec000)
    /lib64/ld-linux-x86-64.so.2 (0x00007f1939bca000)
    libjpeg.so.8 => /usr/lib/x86_64-linux-gnu/libjpeg.so.8 (0x00007f193529b000)
    libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007f1935084000)
    libgmodule-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0 (0x00007f1934e80000)
    libxml2.so.2 => /usr/lib/x86_64-linux-gnu/libxml2.so.2 (0x00007f1934b23000)
    libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f193491f000)
    libffi.so.6 => /usr/lib/x86_64-linux-gnu/libffi.so.6 (0x00007f1934717000)
    libpcre.so.3 => /lib/x86_64-linux-gnu/libpcre.so.3 (0x00007f19344d9000)
    libgstbase-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstbase-0.10.so.0 (0x00007f1934286000)
    liborc-0.4.so.0 => /usr/lib/x86_64-linux-gnu/liborc-0.4.so.0 (0x00007f193400b000)
    libraw1394.so.11 => /usr/lib/x86_64-linux-gnu/libraw1394.so.11 (0x00007f1933dfb000)
    libusb-1.0.so.0 => /lib/x86_64-linux-gnu/libusb-1.0.so.0 (0x00007f1933bec000)
    libv4l2.so.0 => /usr/lib/x86_64-linux-gnu/libv4l2.so.0 (0x00007f19339e0000)
    libvpx.so.1 => /usr/lib/libvpx.so.1 (0x00007f193373a000)
    libvorbisenc.so.2 => /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2 (0x00007f193326b000)
    libvorbis.so.0 => /usr/lib/x86_64-linux-gnu/libvorbis.so.0 (0x00007f193303f000)
    libtheoraenc.so.1 => /usr/lib/x86_64-linux-gnu/libtheoraenc.so.1 (0x00007f1932e01000)
    libtheoradec.so.1 => /usr/lib/x86_64-linux-gnu/libtheoradec.so.1 (0x00007f1932be6000)
    libspeex.so.1 => /usr/lib/x86_64-linux-gnu/libspeex.so.1 (0x00007f19329cd000)
    libschroedinger-1.0.so.0 => /usr/lib/libschroedinger-1.0.so.0 (0x00007f1932719000)
    libgsm.so.1 => /usr/lib/libgsm.so.1 (0x00007f193250b000)
    libva.so.1 => /usr/lib/x86_64-linux-gnu/libva.so.1 (0x00007f19322f5000)
    libbz2.so.1.0 => /lib/x86_64-linux-gnu/libbz2.so.1.0 (0x00007f19320e4000)
    libv4lconvert.so.0 => /usr/lib/x86_64-linux-gnu/libv4lconvert.so.0 (0x00007f1931e6f000)
    libogg.so.0 => /usr/lib/x86_64-linux-gnu/libogg.so.0 (0x00007f1931c67000)

```
Now I have used the option of the linker to set RPATH -Wl,-rpath,\$$ORIGIN/lib ([http://en.wikipedia.org/wiki/Rpath](http://en.wikipedia.org/wiki/Rpath)) and so before the execution the linker looks as the first path the RPATH. This is true if the DT_RUNPATH is not set ([https://wiki.debian.org/RpathIssue](https://wiki.debian.org/RpathIssue)). On my Ubuntu 12.04 64 bit, if I check with ldd this is correct all the libraries points to the right path.
On Debian 7 64 bit, where the openCV libraries are not present, ldd returns
```

linux-vdso.so.1 =>  (0x00007fffcf157000)
    linux-vdso.so.1 =>  (0x00007fffcf157000)
    libopencv_highgui.so.2.4 => /home/user/./lib/libopencv_highgui.so.2.4 (0x00007fd15d4a1000)
    libopencv_imgproc.so.2.4 => /home/user/./lib/libopencv_imgproc.so.2.4 (0x00007fd15cfe1000)
    libopencv_core.so.2.4 => /home/user/./lib/libopencv_core.so.2.4 (0x00007fd15cb88000)
    libstdc++.so.6 => /home/user/./lib/libstdc++.so.6 (0x00007fd15c884000)
    libm.so.6 => /home/user/./lib/libm.so.6 (0x00007fd15c588000)
    libgcc_s.so.1 => /home/user/./lib/libgcc_s.so.1 (0x00007fd15c371000)
    libpthread.so.0 => /home/user/./lib/libpthread.so.0 (0x00007fd15c154000)
    libc.so.6 => /home/user/./lib/libc.so.6 (0x00007fd15bd94000)
    libtiff.so.4 => /home/user/./lib/libtiff.so.4 (0x00007fd15bb2f000)
    libgstreamer-0.10.so.0 => /home/user/./lib/libgstreamer-0.10.so.0 (0x00007fd15b848000)
    libgobject-2.0.so.0 => /home/user/./lib/libgobject-2.0.so.0 (0x00007fd15b5f9000)
    libglib-2.0.so.0 => /home/user/./lib/libglib-2.0.so.0 (0x00007fd15b303000)
    libgstapp-0.10.so.0 => /home/user/./lib/libgstapp-0.10.so.0 (0x00007fd15b0f7000)
    libgstvideo-0.10.so.0 => /home/user/./lib/libgstvideo-0.10.so.0 (0x00007fd15aedb000)
    libdc1394.so.22 => /home/user/./lib/libdc1394.so.22 (0x00007fd15ac67000)
    libv4l1.so.0 => /home/user/./lib/libv4l1.so.0 (0x00007fd15aa61000)
    libavcodec.so.53 => /home/user/./lib/libavcodec.so.53 (0x00007fd159c51000)
    libavformat.so.53 => /home/user/./lib/libavformat.so.53 (0x00007fd159950000)
    libavutil.so.51 => /home/user/./lib/libavutil.so.51 (0x00007fd159730000)
    libswscale.so.2 => /home/user/./lib/libswscale.so.2 (0x00007fd1594ea000)
    librt.so.1 => /home/user/./lib/librt.so.1 (0x00007fd1592e1000)
    libgomp.so.1 => /home/user/./lib/libgomp.so.1 (0x00007fd1590d2000)
    /lib64/ld-linux-x86-64.so.2 (0x00007fd15d79b000)
    libjpeg.so.8 => /home/user/./lib/libjpeg.so.8 (0x00007fd158e81000)
    libz.so.1 => /home/user/./lib/libz.so.1 (0x00007fd158c6a000)
    libgmodule-2.0.so.0 => /home/user/./lib/libgmodule-2.0.so.0 (0x00007fd158a66000)
    libxml2.so.2 => /home/user/./lib/libxml2.so.2 (0x00007fd158709000)
    libdl.so.2 => /home/user/./lib/libdl.so.2 (0x00007fd158505000)
    libffi.so.6 => /home/user/./lib/libffi.so.6 (0x00007fd1582fd000)
    libpcre.so.3 => /home/user/./lib/libpcre.so.3 (0x00007fd1580bf000)
    libgstbase-0.10.so.0 => /home/user/./lib/libgstbase-0.10.so.0 (0x00007fd157e6c000)
    liborc-0.4.so.0 => /home/user/./lib/liborc-0.4.so.0 (0x00007fd157bf1000)
    libraw1394.so.11 => /home/user/./lib/libraw1394.so.11 (0x00007fd1579e1000)
    libusb-1.0.so.0 => /home/user/./lib/libusb-1.0.so.0 (0x00007fd1577d2000)
    libv4l2.so.0 => /home/user/./lib/libv4l2.so.0 (0x00007fd1575c6000)
    libvpx.so.1 => /home/user/./lib/libvpx.so.1 (0x00007fd157320000)
    libvorbisenc.so.2 => /home/user/./lib/libvorbisenc.so.2 (0x00007fd156e51000)
    libvorbis.so.0 => /home/user/./lib/libvorbis.so.0 (0x00007fd156c25000)
    libtheoraenc.so.1 => /home/user/./lib/libtheoraenc.so.1 (0x00007fd1569e7000)
    libtheoradec.so.1 => /home/user/./lib/libtheoradec.so.1 (0x00007fd1567cc000)
    libspeex.so.1 => /home/user/./lib/libspeex.so.1 (0x00007fd1565b3000)
    libschroedinger-1.0.so.0 => /home/user/./lib/libschroedinger-1.0.so.0 (0x00007fd1562ff000)
    libgsm.so.1 => /home/user/./lib/libgsm.so.1 (0x00007fd1560f1000)
    libva.so.1 => /home/user/./lib/libva.so.1 (0x00007fd155edb000)
    libbz2.so.1.0 => /home/user/./lib/libbz2.so.1.0 (0x00007fd155cca000)
    libv4lconvert.so.0 => /home/user/./lib/libv4lconvert.so.0 (0x00007fd155a55000)
    libogg.so.0 => /home/user/./lib/libogg.so.0 (0x00007fd15584d000)

```
it seems correct while on openSuse 12.3 64 bit where I installed openCV there are some libraries external to the path $ORIGIN/lib (libogg)
```

linux-vdso.so.1 =>  (0x00007fff25fff000)
    libopencv_highgui.so.2.4 => /home/user/lib/libopencv_highgui.so.2.4 (0x00007feb4a50c000)
    libopencv_imgproc.so.2.4 => /home/user/lib/libopencv_imgproc.so.2.4 (0x00007feb4a04c000)
    libopencv_core.so.2.4 => /home/user/lib/libopencv_core.so.2.4 (0x00007feb49bf4000)
    libstdc++.so.6 => /home/user/lib/libstdc++.so.6 (0x00007feb498f0000)
    libm.so.6 => /home/user/lib/libm.so.6 (0x00007feb495f4000)
    libgcc_s.so.1 => /home/user/lib/libgcc_s.so.1 (0x00007feb493de000)
    libpthread.so.0 => /home/user/lib/libpthread.so.0 (0x00007feb491c1000)
    libc.so.6 => /home/user/lib/libc.so.6 (0x00007feb48e01000)
    libtiff.so.4 => /home/user/lib/libtiff.so.4 (0x00007feb48b9d000)
    libgstreamer-0.10.so.0 => /home/user/lib/libgstreamer-0.10.so.0 (0x00007feb488b6000)
    libgobject-2.0.so.0 => /home/user/lib/libgobject-2.0.so.0 (0x00007feb48667000)
    libglib-2.0.so.0 => /home/user/lib/libglib-2.0.so.0 (0x00007feb48372000)
    libgstapp-0.10.so.0 => /home/user/lib/libgstapp-0.10.so.0 (0x00007feb48166000)
    libgstvideo-0.10.so.0 => /home/user/lib/libgstvideo-0.10.so.0 (0x00007feb47f4a000)
    libdc1394.so.22 => /home/user/lib/libdc1394.so.22 (0x00007feb47cd7000)
    libv4l1.so.0 => /home/user/lib/libv4l1.so.0 (0x00007feb47ad1000)
    libavcodec.so.53 => /usr/local/lib/libavcodec.so.53 (0x00007feb46a00000)
    libavformat.so.53 => /usr/local/lib/libavformat.so.53 (0x00007feb46702000)
    libavutil.so.51 => /usr/local/lib/libavutil.so.51 (0x00007feb464e2000)
    libswscale.so.2 => /usr/local/lib/libswscale.so.2 (0x00007feb462af000)
    librt.so.1 => /home/user/lib/librt.so.1 (0x00007feb460a7000)
    libgomp.so.1 => /home/user/lib/libgomp.so.1 (0x00007feb45e98000)
    /lib64/ld-linux-x86-64.so.2 (0x00007feb4a804000)
    libjpeg.so.8 => /home/user/lib/libjpeg.so.8 (0x00007feb45c48000)
    libz.so.1 => /home/user/lib/libz.so.1 (0x00007feb45a31000)
    libgmodule-2.0.so.0 => /home/user/lib/libgmodule-2.0.so.0 (0x00007feb4582d000)
    libxml2.so.2 => /home/user/lib/libxml2.so.2 (0x00007feb454d1000)
    libdl.so.2 => /home/user/lib/libdl.so.2 (0x00007feb452cd000)
    libffi.so.6 => /home/user/lib/libffi.so.6 (0x00007feb450c5000)
    libpcre.so.3 => /home/user/lib/libpcre.so.3 (0x00007feb44e88000)
    libgstbase-0.10.so.0 => /home/user/lib/libgstbase-0.10.so.0 (0x00007feb44c35000)
    liborc-0.4.so.0 => /home/user/lib/liborc-0.4.so.0 (0x00007feb449ba000)
    libraw1394.so.11 => /home/user/lib/libraw1394.so.11 (0x00007feb447ab000)
    libusb-1.0.so.0 => /home/user/lib/libusb-1.0.so.0 (0x00007feb4459c000)
    libv4l2.so.0 => /home/user/lib/libv4l2.so.0 (0x00007feb44390000)
    libvo-amrwbenc.so.0 => /usr/local/lib/libvo-amrwbenc.so.0 (0x00007feb44176000)
    libvo-aacenc.so.0 => /usr/local/lib/libvo-aacenc.so.0 (0x00007feb43f58000)
    libtheoraenc.so.1 => /usr/local/lib/libtheoraenc.so.1 (0x00007feb43d1d000)
    libtheoradec.so.1 => /usr/local/lib/libtheoradec.so.1 (0x00007feb43b04000)
    libspeex.so.1 => /usr/local/lib/libspeex.so.1 (0x00007feb438ea000)
    libopencore-amrwb.so.0 => /usr/local/lib/libopencore-amrwb.so.0 (0x00007feb436d6000)
    libopencore-amrnb.so.0 => /usr/local/lib/libopencore-amrnb.so.0 (0x00007feb434ac000)
    libmp3lame.so.0 => /usr/local/lib/libmp3lame.so.0 (0x00007feb43224000)
    libfaac.so.0 => /usr/local/lib/libfaac.so.0 (0x00007feb43011000)
    libv4lconvert.so.0 => /home/user/lib/libv4lconvert.so.0 (0x00007feb42d9c000)
    libogg.so.0 => /usr/local/lib/libogg.so.0 (0x00007feb42b95000)

```
Each library inside $ORIGIN/lib can be linked with other libraries and they can be different from those inside the folder. For instance if I type ldd from Debian 7 I get
```

./libavformat.so.53: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.14' not found (required by ./libavformat.so.53)
    linux-vdso.so.1 =>  (0x00007fff31499000)
    libavcodec.so.53 => /usr/lib/x86_64-linux-gnu/libavcodec.so.53 (0x00007f5dfe09b000)
    libavutil.so.51 => /usr/lib/x86_64-linux-gnu/libavutil.so.51 (0x00007f5dfde7a000)
    libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f5dfdbf7000)
    libbz2.so.1.0 => /lib/x86_64-linux-gnu/libbz2.so.1.0 (0x00007f5dfd9e7000)
    libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007f5dfd7d0000)
    libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f5dfd5b3000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f5dfd229000)
    libxvidcore.so.4 => /usr/lib/x86_64-linux-gnu/libxvidcore.so.4 (0x00007f5dfcef2000)
    libx264.so.123 => /usr/lib/x86_64-linux-gnu/libx264.so.123 (0x00007f5dfcb69000)
    libvpx.so.1 => /usr/lib/x86_64-linux-gnu/libvpx.so.1 (0x00007f5dfc8ca000)
    libvorbisenc.so.2 => /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2 (0x00007f5dfc3fb000)
    libvorbis.so.0 => /usr/lib/x86_64-linux-gnu/libvorbis.so.0 (0x00007f5dfc1cd000)
    libtheoraenc.so.1 => /usr/lib/x86_64-linux-gnu/libtheoraenc.so.1 (0x00007f5dfbf8c000)
    libtheoradec.so.1 => /usr/lib/x86_64-linux-gnu/libtheoradec.so.1 (0x00007f5dfbd70000)
    libspeex.so.1 => /usr/lib/x86_64-linux-gnu/libspeex.so.1 (0x00007f5dfbb57000)
    libschroedinger-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libschroedinger-1.0.so.0 (0x00007f5dfb88a000)
    libopenjpeg.so.2 => /usr/lib/x86_64-linux-gnu/libopenjpeg.so.2 (0x00007f5dfb668000)
    libmp3lame.so.0 => /usr/lib/x86_64-linux-gnu/libmp3lame.so.0 (0x00007f5dfb3dd000)
    libgsm.so.1 => /usr/lib/x86_64-linux-gnu/libgsm.so.1 (0x00007f5dfb1d0000)
    libdirac_encoder.so.0 => /usr/lib/x86_64-linux-gnu/libdirac_encoder.so.0 (0x00007f5dfaf40000)
    libva.so.1 => /usr/lib/x86_64-linux-gnu/libva.so.1 (0x00007f5dfad28000)
    /lib64/ld-linux-x86-64.so.2 (0x00007f5dff22e000)
    libogg.so.0 => /usr/lib/x86_64-linux-gnu/libogg.so.0 (0x00007f5dfab22000)
    liborc-0.4.so.0 => /usr/lib/x86_64-linux-gnu/liborc-0.4.so.0 (0x00007f5dfa8a4000)
    libstdc++.so.6 => /usr/lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007f5dfa59d000)
    libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007f5dfa387000)
    libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f5dfa182000)

```
Hence is it possible to get an executable that depends only from the libraries in $ORIGIN/lib? I compiled with Ubuntu 12.04 64 bit, but if I try to execute on Debian 7 64 bit I get segmentation fault of the linker ld-linux-x86-64.so.2 while in openSuse 12.3 64 bit I get
```

./binary: relocation error: /home/user/lib/libopencv_highgui.so.2.4: symbol avformat_network_init, version LIBAVFORMAT_53 not defined in file libavformat.so.53 with link time reference

```
ldd libavformat
```

ldd libavformat.so.53
    linux-vdso.so.1 =>  (0x00007fff8c3c5000)
    libavcodec.so.53 => /usr/local/lib/libavcodec.so.53 (0x00007f3634b37000)
    libavutil.so.51 => /usr/local/lib/libavutil.so.51 (0x00007f3634916000)
    libm.so.6 => /lib64/libm.so.6 (0x00007f36346bf000)
    libbz2.so.1.0 => not found
    libz.so.1 => /lib64/libz.so.1 (0x00007f36344a7000)
    libpthread.so.0 => /lib64/libpthread.so.0 (0x00007f3634289000)
    libc.so.6 => /lib64/libc.so.6 (0x00007f3633ef9000)
    libvo-amrwbenc.so.0 => /usr/local/lib/libvo-amrwbenc.so.0 (0x00007f3633cdf000)
    libvo-aacenc.so.0 => /usr/local/lib/libvo-aacenc.so.0 (0x00007f3633ac0000)
    libtheoraenc.so.1 => /usr/local/lib/libtheoraenc.so.1 (0x00007f3633885000)
    libtheoradec.so.1 => /usr/local/lib/libtheoradec.so.1 (0x00007f363366c000)
    libspeex.so.1 => /usr/local/lib/libspeex.so.1 (0x00007f3633451000)
    libopencore-amrwb.so.0 => /usr/local/lib/libopencore-amrwb.so.0 (0x00007f363323d000)
    libopencore-amrnb.so.0 => /usr/local/lib/libopencore-amrnb.so.0 (0x00007f3633013000)
    libmp3lame.so.0 => /usr/local/lib/libmp3lame.so.0 (0x00007f3632d8a000)
    libfaac.so.0 => /usr/local/lib/libfaac.so.0 (0x00007f3632b77000)
    /lib64/ld-linux-x86-64.so.2 (0x00007f3635f35000)
    libogg.so.0 => /usr/local/lib/libogg.so.0 (0x00007f363296f000)

```
the binary is in /home/user/.
Are there other solutions to distribute a binary without source code?

Thank you very much

---

### Post by Bachstelze on 2014-01-21
the easiest way is to link the libraries statically, but you need to be careful about the license terms of the libraries you use (for example if you use a GPL library, then you *can't* distribute your program without its source code).

---

### Post by erotavlas on 2014-01-21
Yes, I know what you are talking about. So is there no workaround in the case of dynamic link?

---

