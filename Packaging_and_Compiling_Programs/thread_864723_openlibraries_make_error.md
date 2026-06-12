---
title: "openlibraries make error"
date: 2008-07-19
forum: Packaging and Compiling Programs
---

### Post by Partyboi2 on 2008-07-19
I have been trying to compile openlibraries on hardy, but seem to have ran into a problem and so far have not been able to find the solution. Maybe someone might be able to help.
```
In file included from /usr/include/ffmpeg/avformat.h:36,
                 from avformat_plugin.cpp:31:
/usr/include/ffmpeg/avcodec.h:2437: warning: 'ImgReSampleContext' is deprecated (declared at /usr/include/ffmpeg/avcodec.h:2434)
/usr/include/ffmpeg/avcodec.h:2444: warning: 'ImgReSampleContext' is deprecated (declared at /usr/include/ffmpeg/avcodec.h:2434)
In file included from avformat_plugin.cpp:31:
/usr/include/ffmpeg/avformat.h:282: warning: 'AVFrac' is deprecated (declared at /usr/include/ffmpeg/avformat.h:118)
avformat_plugin.cpp: In member function 'AVStream* olib::openmedialib::ml::avformat_store::add_video_stream(CodecID)':
avformat_plugin.cpp:605: warning: deprecated conversion from string constant to 'char*'
avformat_plugin.cpp: In member function 'void olib::openmedialib::ml::avformat_input::store_image(double, int64_t)':
avformat_plugin.cpp:1483: warning: 'img_convert' is deprecated (declared at /usr/include/ffmpeg/avcodec.h:2575)
avformat_plugin.cpp:1483: warning: 'img_convert' is deprecated (declared at /usr/include/ffmpeg/avcodec.h:2575)
avformat_plugin.cpp:1490: warning: 'img_convert' is deprecated (declared at /usr/include/ffmpeg/avcodec.h:2575)
avformat_plugin.cpp:1490: warning: 'img_convert' is deprecated (declared at /usr/include/ffmpeg/avcodec.h:2575)
avformat_plugin.cpp: In member function 'int olib::openmedialib::ml::avformat_input::decode_audio(bool&)':
avformat_plugin.cpp:1563: warning: 'avcodec_decode_audio' is deprecated (declared at /usr/include/ffmpeg/avcodec.h:2730)
avformat_plugin.cpp:1563: warning: 'avcodec_decode_audio' is deprecated (declared at /usr/include/ffmpeg/avcodec.h:2730)
avformat_plugin.cpp: At global scope:
avformat_plugin.cpp:1920: error: extra qualification 'olib::openmedialib::ml::avformat_resampler_filter::' on member 'avformat_resampler_filter'
avformat_plugin.cpp:2015: error: extra qualification 'olib::openmedialib::ml::avformat_resampler_filter::' on member 'fetch'
make[5]: *** [libopenmedialib_avformat_la-avformat_plugin.lo] Error 1
make[5]: Leaving directory `/home/karl/Desktop/openlibraries-0.4.0/src/openmedialib/plugins/avformat'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/karl/Desktop/openlibraries-0.4.0/src/openmedialib/plugins'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/karl/Desktop/openlibraries-0.4.0/src/openmedialib'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/karl/Desktop/openlibraries-0.4.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/karl/Desktop/openlibraries-0.4.0'
make: *** [all] Error 2

```

---

