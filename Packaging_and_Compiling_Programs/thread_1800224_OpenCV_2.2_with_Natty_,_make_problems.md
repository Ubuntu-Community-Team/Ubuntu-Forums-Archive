---
title: "OpenCV 2.2 with Natty , make problems"
date: 2011-07-08
forum: Packaging and Compiling Programs
---

### Post by OKComputerQ on 2011-07-08
Hi All,

I'm new with Linux and Ubuntu .I don't if this is the correct section for this thread. I need some help with making OpenCV 2.2 , I'm using this guide to install it :[ http://www.samontab.com/web/2011/06/installing-opencv-2-2-in-ubuntu-11-04/]("http://www.samontab.com/web/2011/06/installing-opencv-2-2-in-ubuntu-11-04/")

I have successfully installed x264 and ffmpeg but I'm stuck with OpenCV making step . This is the error I get :
```

dow.o
[ 47%] Building CXX object modules/highgui/CMakeFiles/opencv_highgui.dir/src/window_gtk.o
[ 47%] Building CXX object modules/highgui/CMakeFiles/opencv_highgui.dir/src/cap_dc1394_v2.o
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_dc1394_v2.cpp: In member function ‘virtual bool CvCaptureCAM_DC1394_v2_CPP::startCapture()’:
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_dc1394_v2.cpp:331:35: warning: comparison between signed and unsigned integer expressions
[ 47%] Building CXX object modules/highgui/CMakeFiles/opencv_highgui.dir/src/cap_ffmpeg.o
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_ffmpeg.cpp: In member function ‘bool CvCapture_FFMPEG::reopen()’:
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_ffmpeg.cpp:419:5: warning: ‘int av_open_input_file(AVFormatContext**, const char*, AVInputFormat*, int, AVFormatParameters*)’ is deprecated (declared at /usr/local/include/libavformat/avformat.h:1094)
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_ffmpeg.cpp:419:52: warning: ‘int av_open_input_file(AVFormatContext**, const char*, AVInputFormat*, int, AVFormatParameters*)’ is deprecated (declared at /usr/local/include/libavformat/avformat.h:1094)
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_ffmpeg.cpp: In member function ‘virtual bool CvCapture_FFMPEG::open(const char*)’:
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_ffmpeg.cpp:452:15: warning: ‘int av_open_input_file(AVFormatContext**, const char*, AVInputFormat*, int, AVFormatParameters*)’ is deprecated (declared at /usr/local/include/libavformat/avformat.h:1094)
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_ffmpeg.cpp:452:63: warning: ‘int av_open_input_file(AVFormatContext**, const char*, AVInputFormat*, int, AVFormatParameters*)’ is deprecated (declared at /usr/local/include/libavformat/avformat.h:1094)
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_ffmpeg.cpp:469:13: error: ‘CODEC_TYPE_VIDEO’ was not declared in this scope
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_ffmpeg.cpp: In member function ‘virtual bool CvCapture_FFMPEG::grabFrame()’:
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_ffmpeg.cpp:556:54: error: ‘avcodec_decode_video’ was not declared in this scope
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_ffmpeg.cpp: In function ‘const char* icvFFMPEGErrStr(int)’:
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_ffmpeg.cpp:809:10: error: ‘AVERROR_NUMEXPECTED’ was not declared in this scope
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_ffmpeg.cpp:813:10: error: ‘AVERROR_NOFMT’ was not declared in this scope
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_ffmpeg.cpp:815:10: error: ‘AVERROR_IO’ was not declared in this scope
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_ffmpeg.cpp:817:10: error: ‘AVERROR_NOMEM’ was not declared in this scope
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_ffmpeg.cpp: In function ‘AVStream* icv_add_video_stream_FFMPEG(AVFormatContext*, CodecID, int, int, int, double, int)’:
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_ffmpeg.cpp:902:70: error: ‘CODEC_TYPE_VIDEO’ was not declared in this scope
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_ffmpeg.cpp: In function ‘int icv_av_write_frame_FFMPEG(AVFormatContext*, AVStream*, uint8_t*, uint32_t, AVFrame*)’:
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_ffmpeg.cpp:1001:22: error: ‘PKT_FLAG_KEY’ was not declared in this scope
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_ffmpeg.cpp:1021:30: error: ‘PKT_FLAG_KEY’ was not declared in this scope
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_ffmpeg.cpp: In member function ‘virtual void CvVideoWriter_FFMPEG::close()’:
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_ffmpeg.cpp:1185:3: warning: ‘int url_fclose(AVIOContext*)’ is deprecated (declared at /usr/local/include/libavformat/avio.h:280)
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_ffmpeg.cpp:1185:20: warning: ‘int url_fclose(AVIOContext*)’ is deprecated (declared at /usr/local/include/libavformat/avio.h:280)
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_ffmpeg.cpp: In member function ‘virtual bool CvVideoWriter_FFMPEG::open(const char*, int, double, CvSize, bool)’:
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_ffmpeg.cpp:1218:41: error: ‘guess_format’ was not declared in this scope
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_ffmpeg.cpp:1241:31: error: ‘av_alloc_format_context’ was not declared in this scope
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_ffmpeg.cpp:1282:9: warning: ‘int av_set_parameters(AVFormatContext*, AVFormatParameters*)’ is deprecated (declared at /usr/local/include/libavformat/avformat.h:1411)
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_ffmpeg.cpp:1282:35: warning: ‘int av_set_parameters(AVFormatContext*, AVFormatParameters*)’ is deprecated (declared at /usr/local/include/libavformat/avformat.h:1411)
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_ffmpeg.cpp:1286:5: warning: ‘void dump_format(AVFormatContext*, int, const char*, int)’ is deprecated (declared at /usr/local/include/libavformat/avformat.h:1554)
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_ffmpeg.cpp:1286:35: warning: ‘void dump_format(AVFormatContext*, int, const char*, int)’ is deprecated (declared at /usr/local/include/libavformat/avformat.h:1554)
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_ffmpeg.cpp:1348:13: warning: ‘int url_fopen(AVIOContext**, const char*, int)’ is deprecated (declared at /usr/local/include/libavformat/avio.h:279)
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_ffmpeg.cpp:1348:52: warning: ‘int url_fopen(AVIOContext**, const char*, int)’ is deprecated (declared at /usr/local/include/libavformat/avio.h:279)
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_ffmpeg.cpp:1354:5: warning: ‘int av_write_header(AVFormatContext*)’ is deprecated (declared at /usr/local/include/libavformat/avformat.h:1469)
/home/munis/OpenCV-2.2.0/modules/highgui/src/cap_ffmpeg.cpp:1354:25: warning: ‘int av_write_header(AVFormatContext*)’ is deprecated (declared at /usr/local/include/libavformat/avformat.h:1469)
make[2]: *** [modules/highgui/CMakeFiles/opencv_highgui.dir/src/cap_ffmpeg.o] Error 1
make[1]: *** [modules/highgui/CMakeFiles/opencv_highgui.dir/all] Error 2
make: *** [all] Error 2


```I don't know maybe this can be coming to due to my previous attempt to install OpenCV , its been several days trying to solve this problem . Can anybody help me around it ?

---

### Post by FakeOutdoorsman on 2011-07-09
Maybe you should try [OpenCV 2.3.0](http://sourceforge.net/projects/opencvlibrary/files/opencv-unix/2.3/) instead.

---

### Post by mrybczyn on 2011-07-18
Same problem with 2.3 and trunk...  It is some problem with the custom build of ffmpeg as described in the ubuntu forums that causes openCV grief.  I think it may be the --enable-static and --enable-dynamic config options of x264 and ffmpeg, but I haven't got it figured out yet.

---

### Post by bambam88 on 2011-07-19
> **FakeOutdoorsman said:**
> Maybe you should try [OpenCV 2.3.0]("http://sourceforge.net/projects/opencvlibrary/files/opencv-unix/2.3/") instead.
I tried it...and I got the same result. Has anybody gotten this to work?

---

### Post by Don_Shifty on 2011-08-30
still getting the error with the latest opencv on 11.04...
help would be much appreciated!

---

### Post by nightstraveler on 2011-11-11
Same problem, any solutions?

---

### Post by Bachstelze on 2011-11-11
Where did you install ffmpeg from? ffmpeg is a project that moves VERY quickly; it is perfectly possible that the versions of ffmpeg and opencv you have are not compatible because your ffmpeg is either too recent or too old.

---

### Post by nightstraveler on 2011-11-11
ffmpeg reports version 0.7.2
opencv trying to install is 2.3.1

---

### Post by nightstraveler on 2011-11-13
Sorry for the quick bump on this, but I'm a bit time crunched. The help is greatly appreciated.

---

### Post by Bachstelze on 2011-11-14
Then this is probably not the best place to ask. Ask the OpenCV people for which ffmpeg version is appropriate to compile your OpenCV version against.

---

