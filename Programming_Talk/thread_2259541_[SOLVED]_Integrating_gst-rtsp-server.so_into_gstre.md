---
title: "[SOLVED] Integrating gst-rtsp-server.so into gstreamer_android.so"
date: 2015-01-05
forum: Programming Talk
---

### Post by kometonja on 2015-01-05
Hello.
I was compiling gstreamer 1.4.4 from source, by using configure --host=arm-linux-androideabi flag to get the ARM .so and .a binaries.
Then I used gst-android 0.10 build tools to link libraries into gstreamer_android.so.
That works fine.
The problem is that I don't know how to deploy the gst-rtsp-server.so on Android. All the libraries are embedded into .so files  but this one doesn't  depend on gstreamer_andorid.so  but:

 0x00000001 (NEEDED)                     Shared library: [libgstreamer-1.0.so.0]
 0x00000001 (NEEDED)                     Shared library: [libgio-2.0.so.0]
 0x00000001 (NEEDED)                     Shared library: [libgobject-2.0.so.0]
 0x00000001 (NEEDED)                     Shared library: [libglib-2.0.so.0]
 0x00000001 (NEEDED)                     Shared library: [libintl.so.8]
 0x00000001 (NEEDED)                     Shared library: [libm.so]
 0x00000001 (NEEDED)                     Shared library: [libc.so]
 0x00000001 (NEEDED)                     Shared library: [libdl.so]
 0x0000000e (SONAME)                     Library soname: [libgstrtsp-1.0.so.0]
(even if I create custom Android.mk and point LOCAL_SHARED_LIBRARIES  to gstreamer_android.so)
 
So I don't know how to either "register" those libgstreamer-1.0.so.0 from gstreamer_android.so or append gstrtspserver.so into gstreamer_android.so. I tried later by adding into gst-android's Android.mk but then I get this error:
gst-build-armeabi/gstreamer_android.o:gstreamer_android.c:function gst_android_register_static_plugins: error: undefined reference to 'gst_plugin_rtspserver_register'

So I am cleary doing something wrong, can anyone point me to the right direction?
Thanks.

---

### Post by kometonja on 2015-01-07
Ok found a solution,
It was enought to add something like this to gst-android/ndk-build/gstreamer-1.0.mk

GSTREAMER_RTSP_SERVER_LIBS := -Wl,--whole-archive /path/to/gst-rtsp-server-1.4.4/gst/rtsp-server/.libs/libgstrtspserver-1.0.a

and then append this flags to GSTREAMER_ANDROID_LIBS like this:

GSTREAMER_ANDROID_LIBS := $(GSTREAMER_RTSP_SERVER_LIBS) $(call fix-deps,-lgiognutls, -lhogweed)

If you need a custom Android.mk to build RTSP server here's one to start with

[http://pastebin.com/05Z3ni0s](http://pastebin.com/05Z3ni0s)

---

