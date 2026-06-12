---
title: "Problems Compiling ARToolKit in Ubuntu 12.04"
date: 2012-07-08
forum: Packaging and Compiling Programs
---

### Post by Garatuza on 2012-07-08
[I]Hi Everyone!

I am new to Ubuntu and ARToolKit, i am trying to compile ARToolkit, first i downloaded this packages
freeglut3-dev
libgstreamer0.10-dev
libgstreamer-plugins-base0.10-dev 
libxi-dev
libxmu-headers
libxmu-dev
libjpeg62-dev
libglib2.0-dev
libgtk2.0-dev

after that i downloaded ARToolKit-2.72.1.tgz

following this i used tar zxvf ARToolKit-2.72.1.tgz to extract al the files

finally i configured  the Toolkit with ./Configure and choosing Gstreamer Media Framework (option 5)

the problem is when i try to use

$ make

it gets this errors

../../lib/libARvideo.a(video.o): In function `cb_have_data':
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:66: undefined reference to `gst_pad_get_negotiated_caps'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:67: undefined reference to `gst_caps_get_structure'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:70: undefined reference to `gst_structure_get_int'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:71: undefined reference to `gst_structure_get_int'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:72: undefined reference to `gst_structure_get_double'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:74: undefined reference to `g_print'
../../lib/libARvideo.a(video.o): In function `testing_pad':
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:103: undefined reference to `gst_pad_get_negotiated_caps'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:106: undefined reference to `gst_caps_get_structure'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:109: undefined reference to `gst_structure_get_int'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:110: undefined reference to `gst_structure_get_int'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:111: undefined reference to `gst_structure_get_double'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:113: undefined reference to `g_print'
../../lib/libARvideo.a(video.o): In function `ar2VideoOpen':
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:199: undefined reference to `g_printf'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:202: undefined reference to `g_printf'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:206: undefined reference to `g_printf'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:210: undefined reference to `gst_init'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:219: undefined reference to `gst_version_string'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:219: undefined reference to `g_print'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:236: undefined reference to `gst_parse_launch'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:239: undefined reference to `g_print'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:244: undefined reference to `gst_bin_get_type'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:244: undefined reference to `g_type_check_instance_cast'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:244: undefined reference to `gst_bin_get_by_name'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:247: undefined reference to `g_print'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:252: undefined reference to `gst_element_get_pad'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:256: undefined reference to `gst_pad_add_buffer_probe'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:273: undefined reference to `gst_element_set_state'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:275: undefined reference to `gst_pad_get_peer'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:280: undefined reference to `gst_object_unref'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:283: undefined reference to `gst_element_get_state'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:284: undefined reference to `g_log'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:286: undefined reference to `g_print'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:294: undefined reference to `gst_element_set_state'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:297: undefined reference to `gst_element_get_state'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:298: undefined reference to `g_log'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:300: undefined reference to `g_print'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:304: undefined reference to `gst_element_set_state'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:307: undefined reference to `gst_element_get_state'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:308: undefined reference to `g_log'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:310: undefined reference to `g_print'
../../lib/libARvideo.a(video.o): In function `ar2VideoClose':
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:328: undefined reference to `gst_element_set_state'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:331: undefined reference to `gst_object_get_type'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:331: undefined reference to `g_type_check_instance_cast'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:331: undefined reference to `gst_object_unref'
../../lib/libARvideo.a(video.o): In function `ar2VideoCapStart':
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:349: undefined reference to `gst_element_set_state'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:355: undefined reference to `gst_element_get_state'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:358: undefined reference to `g_log'
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:362: undefined reference to `g_print'
../../lib/libARvideo.a(video.o): In function `ar2VideoCapStop':
/home/garatuza/ARToolKit/lib/SRC/VideoGStreamer/video.c:371: undefined reference to `gst_element_set_state'
collect2: ld devolvió el estado de salida 1

I think it has to do with GStreamer but, i dont know what could it be

i would appreciate any help, i have been trying since two days ago and have met a dead end, i dont know what to do, 

Thanks to all!
[/I]

---

### Post by parq on 2012-07-09
Hi!

1. Are you running 'make' as sudo? Try:

```
$ sudo make
```


2. Have you done the correct video configuration? Verify that you have the correct gstreamer options.

You can have more info at [elblogdeparq.blogspot.com.es/2009/07/realidad-aumentada-artoolkit-en-ubuntu]("http://elblogdeparq.blogspot.com.es/2009/07/realidad-aumentada-artoolkit-en-ubuntu.html")

---

### Post by SevenMachines on 2012-07-10
This program has mis-configured library linking orders that would need to be fixed up to compile on a reasonably (post gcc 4.3) new computer. Theres a million and one threads about this issue in the forum, the 'as-needed' linking problem. 
The quickest though not proper way to get it working would be look for every failing linking as seen in your output, look for the corresponding Makefile, and switch the order of 
$(LDFLAG) $(LIBS)
to
$(LIBS) $(LDFLAG)

It's not correct but the outcome would probably allow compilation. 
As you're not used to ubuntu or compilation I'd recommend you ignore this program and move on,  if the codes this out of date there are probably other problems with it too

---

### Post by jalexstark on 2012-09-17
Perhaps edit Configure to do this automatically.  (The first sed search-and-replace is additional.)

```
cat > $SED <<EOF
s/\$(LDFLAG) \$(LIBS)/\$(LIBS) \$(LDFLAG)/
s/@VIDEO_DRIVER@/$VIDEO_DRIVER/
s/@CFLAG@/$CFLAG/
s/@LDFLAG@/$LDFLAG/
s/@ARFLAG@/$ARFLAG/
s/@RANLIB@/$RANLIB/
s/@LIBS@/$LIBS/
s/@CCVT_OBJ@/$CCVT_OBJ/
EOF
```

---

