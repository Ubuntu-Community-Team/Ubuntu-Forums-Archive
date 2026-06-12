---
title: "Trouble Compling ZoneMinder 1.25.X from Source/Ubuntu 12.04"
date: 2012-10-17
forum: Packaging and Compiling Programs
---

### Post by metallica1973 on 2012-10-17
I orginally installed Zoneminder 1.25.X on Ubuntu 12.04 using there repositories and ran into a roadblock using the Bluecherry BC-08240A - 8 port video, 8 port audio realtime hardware compression card. The card requires the solo6010-dkm driver which uses ('extended' layouts)

[http://community.bluecherrydvr.com/responses/using_the_display_port_on_bluecherry_hardware_compression_cards](http://community.bluecherrydvr.com/responses/using_the_display_port_on_bluecherry_hardware_compression_cards)

I am able to see the video inputs(8,9 respectively) and the capture palette(UYVY [UYUV 4:2:2 Packed, UYVY]) on the card

```

[0xb5000960] v4l2 demux debug: trying kernel V4L2
[0xb5000960] v4l2 demux debug: device Softlogic 6010 using driver solo6x10 (version 2.4.3) on PCI 0000:0a:09.0
[0xb5000960] v4l2 demux debug: the device has the capabilities: 0x05000001
[0xb5000960] v4l2 demux debug: (X) Video Capture, ( ) Audio, ( ) Tuner, ( ) Radio
[0xb5000960] v4l2 demux debug: (X) Read/Write, (X) Streaming, ( ) Asynchronous
[0xb5000960] v4l2 demux debug: video input 0 (Camera 1) has type: External analog input *
[0xb5000960] v4l2 demux debug: video input 1 (Camera 2) has type: External analog input
[0xb5000960] v4l2 demux debug: video input 2 (Camera 3) has type: External analog input
[0xb5000960] v4l2 demux debug: video input 3 (Camera 4) has type: External analog input
[0xb5000960] v4l2 demux debug: video input 4 (Camera 5) has type: External analog input
[0xb5000960] v4l2 demux debug: video input 5 (Camera 6) has type: External analog input
[0xb5000960] v4l2 demux debug: video input 6 (Camera 7) has type: External analog input
[0xb5000960] v4l2 demux debug: video input 7 (Camera 8) has type: External analog input
[0xb5000960] v4l2 demux debug: video input 8 (Multi 4UP-1) has type: External analog input
[0xb5000960] v4l2 demux debug: video input 9 (Multi 4UP-2) has type: External analog input
[0xb5000960] v4l2 demux debug: input set to 0
[0xb5000960] v4l2 demux debug: device supports chroma UYVY [UYUV 4:2:2 Packed, UYVY]
[0xb5000960] v4l2 demux debug: boolean Motion Detection Trace (08000002)
[0xb5000960] v4l2 demux debug: current: false, default: false
[0xb5000960] v4l2 demux debug: found default width and height of 704x480

```

this being said and finding a solution to my issue:

[http://www.zoneminder.com/forums/viewtopic.php?f=29&t=19539&p=76736&hilit=1.25.x+patch#p76736](http://www.zoneminder.com/forums/viewtopic.php?f=29&t=19539&p=76736&hilit=1.25.x+patch#p76736)

I decided to recompile my version of Zoneminder with the adjustment made in the post above. I made most of the changes and have wrestled around with my compile errors and am stuck here:

```

export CPPFLAGS="-D__STDC_CONSTANT_MACROS ${CPPFLAGS}";/opt/zm# ./configure --prefix=/usr --with-webdir=/var/www/zm --with-cgidir=/opt/zm/cgi-bin

```
```

/opt/zm#make
zm_jpeg.o -MD -MP -MF .deps/zm_jpeg.Tpo -c -o zm_jpeg.o zm_jpeg.cpp
mv -f .deps/zm_jpeg.Tpo .deps/zm_jpeg.Po
g++ -DHAVE_CONFIG_H -I. -I..  -I/usr/include -I/usr/include -Wall -Wno-sign-compare -fno-inline -I/usr/include -D__STDC_CONSTANT_MACROS   -g -O2 -MT zm_local_camera.o -MD -MP -MF .deps/zm_local_camera.Tpo -c -o zm_local_camera.o zm_local_camera.cpp
mv -f .deps/zm_local_camera.Tpo .deps/zm_local_camera.Po
g++ -DHAVE_CONFIG_H -I. -I..  -I/usr/include -I/usr/include -Wall -Wno-sign-compare -fno-inline -I/usr/include -D__STDC_CONSTANT_MACROS   -g -O2 -MT zm_monitor.o -MD -MP -MF .deps/zm_monitor.Tpo -c -o zm_monitor.o zm_monitor.cpp
zm_monitor.cpp: In member function ‘virtual void MonitorStream::runStream()’:
zm_monitor.cpp:3479:14: warning: variable ‘frame_sent’ set but not used [-Wunused-but-set-variable]
mv -f .deps/zm_monitor.Tpo .deps/zm_monitor.Po
g++ -DHAVE_CONFIG_H -I. -I..  -I/usr/include -I/usr/include -Wall -Wno-sign-compare -fno-inline -I/usr/include -D__STDC_CONSTANT_MACROS   -g -O2 -MT zm_ffmpeg.o -MD -MP -MF .deps/zm_ffmpeg.Tpo -c -o zm_ffmpeg.o zm_ffmpeg.cpp
mv -f .deps/zm_ffmpeg.Tpo .deps/zm_ffmpeg.Po
g++ -DHAVE_CONFIG_H -I. -I..  -I/usr/include -I/usr/include -Wall -Wno-sign-compare -fno-inline -I/usr/include -D__STDC_CONSTANT_MACROS   -g -O2 -MT zm_mpeg.o -MD -MP -MF .deps/zm_mpeg.Tpo -c -o zm_mpeg.o zm_mpeg.cpp
zm_mpeg.cpp: In member function ‘void VideoStream::OpenStream()’:
zm_mpeg.cpp:179:30: error: too few arguments to function ‘int avcodec_open2(AVCodecContext*, AVCodec*, AVDictionary**)’
/usr/include/libavcodec/avcodec.h:4074:5: note: declared here
zm_mpeg.cpp:244:27: error: too few arguments to function ‘int avformat_write_header(AVFormatContext*, AVDictionary**)’
/usr/include/libavformat/avformat.h:1662:5: note: declared here
zm_mpeg.cpp: In member function ‘double VideoStream::EncodeFrame(uint8_t*, int, bool, unsigned int)’:
zm_mpeg.cpp:386:77: error: ‘av_rescale_q’ was not declared in this scope
make[2]: *** [zm_mpeg.o] Error 1
make[2]: Leaving directory `/opt/zm/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/zm'
make: *** [all] Error 2

```

I made most of the changes to the depriecated functions to what was replaced and now I get the above error messages in reference to:

```

too few arguments to function ‘int avcodec_open2(AVCodecContext*, AVCodec*, AVDictionary**)’
/usr/include/libavcodec/avcodec.h:4074:5: note: declared here
zm_mpeg.cpp:244:27: error: too few arguments to function ‘int avformat_write_header(AVFormatContext*, AVDictionary**)’
/usr/include/libavformat/avformat.h:1662:5: note: declared here
zm_mpeg.cpp: In member function ‘double VideoStream::EncodeFrame(uint8_t*, int, bool, unsigned int)’:
zm_mpeg.cpp:386:77: error: ‘av_rescale_q’ was not declared in this scope

```

What do I need to do to get this to successfully compile? Should I downgrade "FFMPEG" to an older version that used the previous funtions that I had changed? What version of FFMPEG does Zoneminder 1.25.X use?

---

### Post by chrisjunkie on 2012-10-26
Hi all,

I'm having similar problems too trying to compile from source. Is it due to the ffmpeg/libav split?
I've even tried compiling ffmpeg from source with libx264 and am still having issues. Any help would be great.

Thanks

---

