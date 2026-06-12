---
title: "Keep getting error when installing ARToolkit"
date: 2013-04-13
forum: New to Ubuntu
---

### Post by kapi on 2013-04-13
I keep getting the same output and wondered if anyone could help. I'm installing ARToolkit and when I run the 'make' command I get the following output.

collect2: ld returned 1 exit status
make[2]: *** [../../bin/videoTest] Error 1
make[2]: Leaving directory `/home/craig/ARToolKit/util/videoTest'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/craig/ARToolKit/util'
make: *** [all] Error 2

---

### Post by ved2254 on 2013-08-25
I got a similar error. I know this is a linker problem but I can't find any reports of this.
I followed installation instructions here : [Installing ARToolKit on Ubuntu]("http://www.brunosilva.info/2011/07/installing-artoolkit-on-ubuntu.html") 
I use Ubuntu 13.04 64bit.

My error output :

```
cc -o ../../bin/videoTest videoTest.o  -pthread -lgstreamer-0.10 -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lxml2 -lglib-2.0 -L/usr/X11R6/lib -L/usr/local/lib -L../../lib -lARgsub -lARvideo -lAR -lpthread -lglut -lGLU -lGL -lXi -lX11 -lm
../../lib/libARvideo.a(video.o): In function `cb_have_data':
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:66: undefined reference to `gst_pad_get_negotiated_caps'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:67: undefined reference to `gst_caps_get_structure'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:70: undefined reference to `gst_structure_get_int'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:71: undefined reference to `gst_structure_get_int'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:72: undefined reference to `gst_structure_get_double'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:74: undefined reference to `g_print'
../../lib/libARvideo.a(video.o): In function `testing_pad':
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:103: undefined reference to `gst_pad_get_negotiated_caps'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:106: undefined reference to `gst_caps_get_structure'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:109: undefined reference to `gst_structure_get_int'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:110: undefined reference to `gst_structure_get_int'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:111: undefined reference to `gst_structure_get_double'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:113: undefined reference to `g_print'
../../lib/libARvideo.a(video.o): In function `ar2VideoOpen':
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:199: undefined reference to `g_printf'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:202: undefined reference to `g_printf'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:206: undefined reference to `g_printf'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:210: undefined reference to `gst_init'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:219: undefined reference to `gst_version_string'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:219: undefined reference to `g_print'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:236: undefined reference to `gst_parse_launch'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:239: undefined reference to `g_print'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:244: undefined reference to `gst_bin_get_type'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:244: undefined reference to `g_type_check_instance_cast'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:244: undefined reference to `gst_bin_get_by_name'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:247: undefined reference to `g_print'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:252: undefined reference to `gst_element_get_pad'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:256: undefined reference to `gst_pad_add_buffer_probe'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:273: undefined reference to `gst_element_set_state'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:275: undefined reference to `gst_pad_get_peer'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:280: undefined reference to `gst_object_unref'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:283: undefined reference to `gst_element_get_state'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:284: undefined reference to `g_log'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:286: undefined reference to `g_print'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:294: undefined reference to `gst_element_set_state'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:297: undefined reference to `gst_element_get_state'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:298: undefined reference to `g_log'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:300: undefined reference to `g_print'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:304: undefined reference to `gst_element_set_state'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:307: undefined reference to `gst_element_get_state'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:308: undefined reference to `g_log'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:310: undefined reference to `g_print'
../../lib/libARvideo.a(video.o): In function `ar2VideoClose':
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:328: undefined reference to `gst_element_set_state'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:331: undefined reference to `gst_object_get_type'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:331: undefined reference to `g_type_check_instance_cast'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:331: undefined reference to `gst_object_unref'
../../lib/libARvideo.a(video.o): In function `ar2VideoCapStart':
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:349: undefined reference to `gst_element_set_state'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:355: undefined reference to `gst_element_get_state'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:358: undefined reference to `g_log'
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:362: undefined reference to `g_print'
../../lib/libARvideo.a(video.o): In function `ar2VideoCapStop':
/home/ved/Downloads/ARToolKit/lib/SRC/VideoGStreamer/video.c:371: undefined reference to `gst_element_set_state'
collect2: error: ld returned 1 exit status
make[2]: *** [../../bin/videoTest] Error 1
make[2]: Leaving directory `/home/ved/Downloads/ARToolKit/util/videoTest'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/ved/Downloads/ARToolKit/util'
make: *** [all] Error 2
```

---

