---
title: "install opencv"
date: 2009-07-26
forum: Programming Talk
---

### Post by my.self on 2009-07-26
Hi!

Does anybody know a good install manual for  "opencv" on Ubuntu 9.04?

I checked out the this version:
[https://opencvlibrary.svn.sourceforge.net/svnroot/opencvlibrary/trunk](https://opencvlibrary.svn.sourceforge.net/svnroot/opencvlibrary/trunk)

and tried to install it based on the following article:

[http://opencv.willowgarage.com/wiki/InstallGuide_Linux](http://opencv.willowgarage.com/wiki/InstallGuide_Linux)
but there seems to be a problem with "ffmpeg".


I also tried several configurations of "ffmpeg" based on the following articles:
[http://www.comp.leeds.ac.uk/vision/opencv/install-lin-ffmpeg.html](http://www.comp.leeds.ac.uk/vision/opencv/install-lin-ffmpeg.html)
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

but i still not succeeded to make it run :-(

Cheers Stefan

---

### Post by stair314 on 2009-07-26
Can you post the exact error you're seeing? I've installed OpenCV on many platforms and there are many different kinds of "problems with 'ffmpeg'" that one can encounter.

---

### Post by my.self on 2009-07-26
Thx for your quick reply!
I just copied the "make" output ...

Since I'm a Linux newbie it's a bit hard for me to trace the problem. I hope i haven't made i completely ******** :-(

Linking CXX static library ../../lib/libhighgui_pch_dephelp.a
[ 83%] Built target highgui_pch_dephelp
[ 83%] Generating _highgui.h
[ 83%] Generating _highgui.h.gch/highgui_RELEASE.gch
In file included from /home/myself/opencv/trunk/opencv/include/opencv/cxmisc.h:52,
                 from /home/myself/opencv/trunk/opencv/include/opencv/cxcore.hpp:46,
                 from /home/myself/opencv/trunk/opencv/include/opencv/cxcore.h:2116,
                 from /home/myself/opencv/trunk/opencv/include/opencv/highgui.h:47,
                 from /home/myself/opencv/trunk/opencv/release/src/highgui/_highgui.h:45:
/home/myself/opencv/trunk/opencv/./cvconfig.h:68:1: warning: "HAVE_JASPER" redefined
<command-line>: warning: this is the location of the previous definition
/home/myself/opencv/trunk/opencv/./cvconfig.h:71:1: warning: "HAVE_JPEG" redefined
<command-line>: warning: this is the location of the previous definition
/home/myself/opencv/trunk/opencv/./cvconfig.h:98:1: warning: "HAVE_PNG" redefined
<command-line>: warning: this is the location of the previous definition
/home/myself/opencv/trunk/opencv/./cvconfig.h:143:1: warning: "HAVE_TIFF" redefined
<command-line>: warning: this is the location of the previous definition
[ 84%] Built target pch_Generate_highgui
[ 84%] Building CXX object src/highgui/CMakeFiles/highgui.dir/cvcap.o
[ 84%] Building CXX object src/highgui/CMakeFiles/highgui.dir/cvcap_images.o
[ 84%] Building CXX object src/highgui/CMakeFiles/highgui.dir/image.o
[ 84%] Building CXX object src/highgui/CMakeFiles/highgui.dir/loadsave.o
[ 84%] Building CXX object src/highgui/CMakeFiles/highgui.dir/precomp.o
[ 85%] Building CXX object src/highgui/CMakeFiles/highgui.dir/utils.o
[ 85%] Building CXX object src/highgui/CMakeFiles/highgui.dir/window.o
[ 85%] Building CXX object src/highgui/CMakeFiles/highgui.dir/window_gtk.o
[ 85%] Building CXX object src/highgui/CMakeFiles/highgui.dir/cvcap_ffmpeg.o
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:73:29: error: ffmpeg/avformat.h: No such file or directory
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:74:28: error: ffmpeg/avcodec.h: No such file or directory
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:124: error: &#8216;CODEC_ID_H264&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:125: error: &#8216;CODEC_ID_H264&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:126: error: &#8216;CODEC_ID_H264&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:127: error: &#8216;CODEC_ID_H264&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:128: error: &#8216;CODEC_ID_H264&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:129: error: &#8216;CODEC_ID_H264&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:131: error: &#8216;CODEC_ID_H263&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:132: error: &#8216;CODEC_ID_H263P&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:133: error: &#8216;CODEC_ID_H263I&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:134: error: &#8216;CODEC_ID_H261&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:137: error: &#8216;CODEC_ID_H263P&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:138: error: &#8216;CODEC_ID_H263P&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:140: error: &#8216;CODEC_ID_MPEG4&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:141: error: &#8216;CODEC_ID_MPEG4&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:142: error: &#8216;CODEC_ID_MPEG4&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:143: error: &#8216;CODEC_ID_MPEG4&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:144: error: &#8216;CODEC_ID_MPEG4&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:145: error: &#8216;CODEC_ID_MPEG4&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:146: error: &#8216;CODEC_ID_MPEG4&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:149: error: &#8216;CODEC_ID_MPEG4&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:150: error: &#8216;CODEC_ID_MPEG4&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:151: error: &#8216;CODEC_ID_MPEG4&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:152: error: &#8216;CODEC_ID_MPEG4&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:153: error: &#8216;CODEC_ID_MPEG4&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:154: error: &#8216;CODEC_ID_MPEG4&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:156: error: &#8216;CODEC_ID_MPEG4&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:158: error: &#8216;CODEC_ID_MSMPEG4V3&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:159: error: &#8216;CODEC_ID_MSMPEG4V3&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:162: error: &#8216;CODEC_ID_MSMPEG4V3&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:163: error: &#8216;CODEC_ID_MSMPEG4V3&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:164: error: &#8216;CODEC_ID_MSMPEG4V3&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:165: error: &#8216;CODEC_ID_MSMPEG4V3&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:166: error: &#8216;CODEC_ID_MSMPEG4V3&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:167: error: &#8216;CODEC_ID_MSMPEG4V3&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:168: error: &#8216;CODEC_ID_MSMPEG4V3&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:170: error: &#8216;CODEC_ID_MSMPEG4V2&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:173: error: &#8216;CODEC_ID_MSMPEG4V2&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:175: error: &#8216;CODEC_ID_MSMPEG4V1&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:177: error: &#8216;CODEC_ID_WMV1&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:180: error: &#8216;CODEC_ID_WMV2&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:181: error: &#8216;CODEC_ID_DVVIDEO&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:182: error: &#8216;CODEC_ID_DVVIDEO&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:183: error: &#8216;CODEC_ID_DVVIDEO&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:184: error: &#8216;CODEC_ID_DVVIDEO&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:185: error: &#8216;CODEC_ID_MPEG1VIDEO&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:186: error: &#8216;CODEC_ID_MPEG1VIDEO&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:187: error: &#8216;CODEC_ID_MPEG2VIDEO&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:188: error: &#8216;CODEC_ID_MPEG2VIDEO&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:189: error: &#8216;CODEC_ID_MPEG1VIDEO&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:190: error: &#8216;CODEC_ID_MPEG1VIDEO&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:191: error: &#8216;CODEC_ID_MPEG1VIDEO&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:192: error: &#8216;CODEC_ID_MPEG2VIDEO&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:193: error: &#8216;CODEC_ID_MPEG2VIDEO&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:194: error: &#8216;CODEC_ID_MPEG2VIDEO&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:195: error: &#8216;CODEC_ID_MJPEG&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:196: error: &#8216;CODEC_ID_MJPEG&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:197: error: &#8216;CODEC_ID_LJPEG&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:198: error: &#8216;CODEC_ID_MJPEG&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:199: error: &#8216;CODEC_ID_MJPEG&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:200: error: &#8216;CODEC_ID_MJPEG&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:201: error: &#8216;CODEC_ID_MJPEG&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:202: error: &#8216;CODEC_ID_MJPEG&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:203: error: &#8216;CODEC_ID_HUFFYUV&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:204: error: &#8216;CODEC_ID_FFVHUFF&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:205: error: &#8216;CODEC_ID_CYUV&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:206: error: &#8216;CODEC_ID_RAWVIDEO&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:207: error: &#8216;CODEC_ID_RAWVIDEO&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:208: error: &#8216;CODEC_ID_RAWVIDEO&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:209: error: &#8216;CODEC_ID_RAWVIDEO&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:210: error: &#8216;CODEC_ID_RAWVIDEO&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:211: error: &#8216;CODEC_ID_RAWVIDEO&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:212: error: &#8216;CODEC_ID_RAWVIDEO&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:213: error: &#8216;CODEC_ID_RAWVIDEO&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:214: error: &#8216;CODEC_ID_RAWVIDEO&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:215: error: &#8216;CODEC_ID_INDEO3&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:216: error: &#8216;CODEC_ID_INDEO3&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:217: error: &#8216;CODEC_ID_VP3&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:218: error: &#8216;CODEC_ID_VP3&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:219: error: &#8216;CODEC_ID_ASV1&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:220: error: &#8216;CODEC_ID_ASV2&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:221: error: &#8216;CODEC_ID_VCR1&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:222: error: &#8216;CODEC_ID_FFV1&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:223: error: &#8216;CODEC_ID_XAN_WC4&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:224: error: &#8216;CODEC_ID_MSRLE&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:225: error: &#8216;CODEC_ID_MSRLE&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:226: error: &#8216;CODEC_ID_MSVIDEO1&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:227: error: &#8216;CODEC_ID_MSVIDEO1&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:228: error: &#8216;CODEC_ID_MSVIDEO1&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:229: error: &#8216;CODEC_ID_MSVIDEO1&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:230: error: &#8216;CODEC_ID_MSVIDEO1&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:231: error: &#8216;CODEC_ID_MSVIDEO1&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:232: error: &#8216;CODEC_ID_CINEPAK&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:233: error: &#8216;CODEC_ID_TRUEMOTION1&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:234: error: &#8216;CODEC_ID_MSZH&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:235: error: &#8216;CODEC_ID_ZLIB&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:236: error: &#8216;CODEC_ID_SNOW&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:237: error: &#8216;CODEC_ID_4XM&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:238: error: &#8216;CODEC_ID_FLV1&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:239: error: &#8216;CODEC_ID_SVQ1&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:240: error: &#8216;CODEC_ID_TSCC&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:241: error: &#8216;CODEC_ID_ULTI&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:242: error: &#8216;CODEC_ID_VIXL&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:243: error: &#8216;CODEC_ID_QPEG&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:244: error: &#8216;CODEC_ID_QPEG&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:245: error: &#8216;CODEC_ID_QPEG&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:246: error: &#8216;CODEC_ID_WMV3&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:247: error: &#8216;CODEC_ID_LOCO&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:248: error: &#8216;CODEC_ID_THEORA&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:278: error: &#8216;CODEC_ID_NONE&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:301: error: ISO C++ forbids declaration of &#8216;AVFormatContext&#8217; with no type
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:301: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:303: error: ISO C++ forbids declaration of &#8216;AVStream&#8217; with no type
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:303: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:304: error: ISO C++ forbids declaration of &#8216;AVFrame&#8217; with no type
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:304: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:306: error: &#8216;AVFrame&#8217; does not name a type
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:307: error: &#8216;AVPacket&#8217; does not name a type
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp: In member function &#8216;void CvCapture_FFMPEG::init()&#8217;:
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:325: error: &#8216;ic&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:327: error: &#8216;video_st&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:328: error: &#8216;picture&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:330: error: &#8216;rgb_picture&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:333: error: &#8216;packet&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp: In member function &#8216;virtual void CvCapture_FFMPEG::close()&#8217;:
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:342: error: &#8216;picture&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:343: error: &#8216;av_free&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:345: error: &#8216;video_st&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:350: error: &#8216;avcodec_close&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:355: error: &#8216;ic&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:357: error: &#8216;av_close_input_file&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:361: error: &#8216;rgb_picture&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:365: error: &#8216;packet&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:366: error: &#8216;av_free_packet&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp: In member function &#8216;bool CvCapture_FFMPEG::reopen()&#8217;:
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:384: error: &#8216;video_st&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:384: error: &#8216;avcodec_close&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:386: error: &#8216;ic&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:386: error: &#8216;av_close_input_file&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:389: error: &#8216;av_open_input_file&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:390: error: &#8216;av_find_stream_info&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:394: error: &#8216;AVCodecContext&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:394: error: &#8216;enc&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:396: error: &#8216;AVCodec&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:396: error: &#8216;codec&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:396: error: &#8216;avcodec_find_decoder&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:397: error: &#8216;avcodec_open&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp: In member function &#8216;virtual bool CvCapture_FFMPEG::open(const char*)&#8217;:
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:416: error: &#8216;av_register_all&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:422: error: &#8216;ic&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:422: error: &#8216;av_open_input_file&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:427: error: &#8216;av_find_stream_info&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:436: error: &#8216;AVCodecContext&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:436: error: &#8216;enc&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:439: error: &#8216;CODEC_TYPE_VIDEO&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:440: error: &#8216;AVCodec&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:440: error: &#8216;codec&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:440: error: &#8216;avcodec_find_decoder&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:442: error: &#8216;avcodec_open&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:445: error: &#8216;video_st&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:446: error: &#8216;picture&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:446: error: &#8216;avcodec_alloc_frame&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:448: error: &#8216;rgb_picture&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:449: error: &#8216;PIX_FMT_BGR24&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:450: error: &#8216;avpicture_get_size&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:451: error: &#8216;AVPicture&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:451: error: expected primary-expression before &#8216;)&#8217; token
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:452: error: &#8216;avpicture_fill&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:465: error: &#8216;av_seek_frame&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp: In member function &#8216;virtual bool CvCapture_FFMPEG::grabFrame()&#8217;:
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:499: error: &#8216;packet&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:502: error: &#8216;ic&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:502: error: &#8216;video_st&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:506: error: &#8216;packet&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:507: error: &#8216;av_free_packet&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:511: error: &#8216;ic&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:511: error: &#8216;packet&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:511: error: &#8216;av_read_frame&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:513: error: &#8216;av_free_packet&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:522: error: &#8216;video_st&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:523: error: &#8216;picture&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:524: error: &#8216;avcodec_decode_video&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp: In member function &#8216;virtual IplImage* CvCapture_FFMPEG::retrieveFrame(int)&#8217;:
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:541: error: &#8216;video_st&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:541: error: &#8216;picture&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:552: error: &#8216;AVPicture&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:552: error: expected primary-expression before &#8216;)&#8217; token
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:552: error: &#8216;rgb_picture&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:552: error: &#8216;PIX_FMT_BGR24&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:553: error: expected primary-expression before &#8216;)&#8217; token
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:554: error: &#8216;video_st&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:556: error: &#8216;img_convert&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp: In member function &#8216;virtual double CvCapture_FFMPEG::getProperty(int)&#8217;:
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:582: error: &#8216;video_st&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:592: error: &#8216;ic&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:592: error: &#8216;AV_NOPTS_VALUE&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:593: error: &#8216;AV_TIME_BASE&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:597: error: &#8216;video_st&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:597: error: &#8216;AV_NOPTS_VALUE&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:602: error: &#8216;ic&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:602: error: &#8216;AV_NOPTS_VALUE&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:615: error: &#8216;video_st&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp: In member function &#8216;virtual bool CvCapture_FFMPEG::setProperty(int, double)&#8217;:
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:652: error: &#8216;video_st&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:661: error: &#8216;AVRational&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:661: error: expected `;' before &#8216;time_base&#8217;
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:666: error: &#8216;ic&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:666: error: &#8216;AV_NOPTS_VALUE&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:671: error: &#8216;time_base&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:671: error: &#8216;ic&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:673: error: &#8216;AV_NOPTS_VALUE&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:679: error: &#8216;AV_NOPTS_VALUE&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:690: error: &#8216;AV_TIME_BASE&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:696: error: &#8216;ic&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:696: error: &#8216;av_seek_frame&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:700: error: &#8216;AV_TIME_BASE&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp: At global scope:
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:742: error: ISO C++ forbids declaration of &#8216;AVOutputFormat&#8217; with no type
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:742: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:743: error: ISO C++ forbids declaration of &#8216;AVFormatContext&#8217; with no type
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:743: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:747: error: ISO C++ forbids declaration of &#8216;AVFrame&#8217; with no type
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:747: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:748: error: ISO C++ forbids declaration of &#8216;AVFrame&#8217; with no type
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:748: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:750: error: ISO C++ forbids declaration of &#8216;AVStream&#8217; with no type
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:750: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp: In function &#8216;const char* icvFFMPEGErrStr(int)&#8217;:
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:761: error: &#8216;AVERROR_NUMEXPECTED&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:763: error: &#8216;AVERROR_INVALIDDATA&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:765: error: &#8216;AVERROR_NOFMT&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:767: error: &#8216;AVERROR_IO&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:769: error: &#8216;AVERROR_NOMEM&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp: At global scope:
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:779: error: use of enum &#8216;CodecID&#8217; without previous declaration
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:779: error: invalid type in declaration before &#8216;;&#8217; token
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp: In member function &#8216;void CvVideoWriter_FFMPEG::init()&#8217;:
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:784: error: &#8216;fmt&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:785: error: &#8216;oc&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:789: error: &#8216;picture&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:790: error: &#8216;input_picture&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:792: error: &#8216;video_st&#8217; was not declared in this scope
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp: At global scope:
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:804: error: expected initializer before &#8216;*&#8217; token
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:758: warning: &#8216;const char* icvFFMPEGErrStr(int)&#8217; defined but not used
make[2]: *** [src/highgui/CMakeFiles/highgui.dir/cvcap_ffmpeg.o] Error 1
make[1]: *** [src/highgui/CMakeFiles/highgui.dir/all] Error 2
make: *** [all] Error 2

---

### Post by stair314 on 2009-07-26
What arguments did you pass to cmake?

---

### Post by my.self on 2009-07-27
cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D BUILD_PYTHON_SUPPORT=ON ..

All the steps i made you can find under:
[http://opencv.willowgarage.com/wiki/InstallGuide_Linux](http://opencv.willowgarage.com/wiki/InstallGuide_Linux)

---

### Post by zippaplick on 2009-07-27
You might be missing the development packages for ffmpeg

try installing with:

sudo apt-get install libavcodec-dev libavformat-dev libavdevice-dev libavutil-dev


There may be others but that's what I found by searching fro ffmpeg in the synaptic package manager.

In general I've found that if I get a bunch of missing symbols when building something its due to missing *-dev packages.

---

### Post by my.self on 2009-07-27
I already tryed...

I've read something that you have to configure "ffmpeg" with "--enable-shared" and something that you have export the "ffmpeg" libs so that the "opencv" installation can find the files...

I already tryed this
but i as ubuntu newbie can not say if i did it right :-(

In windows i just opened the ".sln" file in Visaul Studio and clicked "Rebuild"
Then i simply added the opencv ".dll's" to my project and it worked fine!

---

### Post by stair314 on 2009-07-27
It's not a shared library issue. This is where your troubles begin:

```

/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:73:29: error: ffmpeg/avformat.h: No such file or directory
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:74:28: error: ffmpeg/avcodec.h: No such file or directory

```

So the problem is that either the ffmpeg headers are not installed, or the makefile is not giving the right include path to g++. If you installed them with apt-get, they should be in /usr/include/ffmpeg. Check that directory and if they're there, then the problem is with the makefile.

---

### Post by my.self on 2009-07-28
I installed "ffmpeg" with apt-get but they aren't in usr/include...

I seachtech for "ffmpeg" and this are the results...

froot@my-laptop:/home/myself/opencv/trunk/opencv/release# find / -name "*ffmpeg*"
/home/myself/opencv/trunk/opencv/3rdparty/include/ffmpeg_
/home/myself/opencv/trunk/opencv/src/highgui/.svn/text-base/cvcap_ffmpeg.cpp.svn-base
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp
/home/myself/opencv/trunk/opencv/src/.deps/lib_highgui_la-cvcap_ffmpeg.Plo
/home/myself/ffmpeg
/home/myself/ffmpeg/.svn/text-base/ffmpeg.c.svn-base
/home/myself/ffmpeg/.svn/prop-base/ffmpeg.c.svn-base
/home/myself/ffmpeg/ffmpeg.o
/home/myself/ffmpeg/ffmpeg_3:0.svn20090728-12ubuntu3-1_i386.deb
/home/myself/ffmpeg/doc/.svn/text-base/ffmpeg-doc.texi.svn-base
/home/myself/ffmpeg/doc/.svn/text-base/ffmpeg_powerpc_performance_evaluation_howto.txt.svn-base
/home/myself/ffmpeg/doc/.svn/prop-base/ffmpeg-doc.texi.svn-base
/home/myself/ffmpeg/doc/.svn/prop-base/ffmpeg_powerpc_performance_evaluation_howto.txt.svn-base
/home/myself/ffmpeg/doc/ffmpeg.1
/home/myself/ffmpeg/doc/ffmpeg-doc.html
/home/myself/ffmpeg/doc/ffmpeg_powerpc_performance_evaluation_howto.txt
/home/myself/ffmpeg/doc/ffmpeg-doc.texi
/home/myself/ffmpeg/ffmpeg.c
/home/myself/ffmpeg/backup-072820091417-pre-ffmpeg.tgz
/home/myself/ffmpeg/ffmpeg.d
/home/myself/ffmpeg/ffmpeg_g
/home/myself/ffmpeg/ffmpeg
/home/myself/ffmpeg/doc-pak/doc/.svn/text-base/ffmpeg-doc.texi.svn-base
/home/myself/ffmpeg/doc-pak/doc/.svn/text-base/ffmpeg_powerpc_performance_evaluation_howto.txt.svn-base
/home/myself/ffmpeg/doc-pak/doc/.svn/prop-base/ffmpeg-doc.texi.svn-base
/home/myself/ffmpeg/doc-pak/doc/.svn/prop-base/ffmpeg_powerpc_performance_evaluation_howto.txt.svn-base
/home/myself/ffmpeg/doc-pak/doc/ffmpeg.1
/home/myself/ffmpeg/doc-pak/doc/ffmpeg-doc.html
/home/myself/ffmpeg/doc-pak/doc/ffmpeg_powerpc_performance_evaluation_howto.txt
/home/myself/ffmpeg/doc-pak/doc/ffmpeg-doc.texi
/var/lib/dpkg/info/gstreamer0.10-ffmpeg.md5sums
/var/lib/dpkg/info/ffmpeg.list
/var/lib/dpkg/info/gstreamer0.10-ffmpeg.list
/var/cache/apt/archives/ffmpeg_3%3a0.svn20090303-1ubuntu6_i386.deb
/var/cache/apt/archives/gstreamer0.10-ffmpeg_0.10.6.2-1ubuntu2_i386.deb
/usr/lib/gstreamer-0.10/libgstffmpegcolorspace.so
/usr/lib/gstreamer-0.10/libgstffmpeg.so
/usr/lib/gstreamer-0.10/libgstffmpegscale.so
/usr/share/doc/gstreamer0.10-ffmpeg
/usr/share/app-install/desktop/gstreamer-ffmpeg.desktop

---

### Post by stair314 on 2009-07-28
Try searching for avcodec.h and avformat.h since those are what's missing.
If you can't find them, then you can probably get them with
[code]
sudo apt-get install libavformat-dev libavcodec-dev
[\code]

If you're wondering how I knew those are the names of the packages to install, I'm working off of two pieces of information:

1) You can use 'apt-cache search' to find packages available to apt-get. In this case I ran 'apt-cache search ffmpeg'.

2) Usually packages just include the .so files (analogous to DLLs in Windows) that end users need to run programs based on a library. If the package name says "-dev" on the end, that usually means it also includes the .h/.hpp files that developers need to compile programs based on that library.

---

### Post by my.self on 2009-07-28
But I checked out the latest "ffmpeg" version from svn...

cd
svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg
cd ffmpeg

./configure --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab --enable-shared

make
sudo checkinstall --fstrans=no --install=yes --pkgname=ffmpeg --pkgversion "3:0.svn`date +%Y%m%d`-12ubuntu3" --default

_______________________________________________________________________________________
_______________________________________________________________________________________

I don't really understand why "opencv" needs the header file???
If you need a functionality from another project in Microsoft .NET you just add a reference to this .dll and everything is done!

In some cases also you have to register you .dll for COM or add it to the Global Assembly Cache but thats all...

How is this done in linux?
Do I have to register these assemblies?
Is there something similar????

??
??
??

Omg...
I have absolutely no plan ;-(

---

### Post by stair314 on 2009-07-28
If you had a precompiled version of opencv, you wouldn't need the header files. Since you're trying to compile it from scratch, you need the header files because the opencv sources contain statements such as
#include "libavcodec.h"
and it is those statements that are causing your error.
You don't need to register the headers with a central location. You probably do need to tell cmake where they are though. If they were in one of the standard locations like /usr/include or /usr/local/include they would be found automatically. Since you checked them out with svn, they're wherever you checked them out. cmake isn't psychic; you'll have to find the headers and tell cmake where they are. This lets cmake put the right include paths in the makefiles, and in turn the makefiles give the right include paths to g++. g++ will only look for headers inside the include paths it is given, otherwise you would have to wait all day for it to scan your whole filesystem.

---

### Post by my.self on 2009-07-30
OK,
I came i bit further...
I just copied the entire "ffmpeg" folder to the root directory of "opencv"

But now i have another compilation error:

[ 83%] Built target pch_Generate_highgui
Scanning dependencies of target highgui
[ 83%] Building CXX object src/highgui/CMakeFiles/highgui.dir/cvcap.o
[ 84%] Building CXX object src/highgui/CMakeFiles/highgui.dir/cvcap_images.o
[ 84%] Building CXX object src/highgui/CMakeFiles/highgui.dir/image.o
[ 84%] Building CXX object src/highgui/CMakeFiles/highgui.dir/loadsave.o
[ 84%] Building CXX object src/highgui/CMakeFiles/highgui.dir/precomp.o
[ 84%] Building CXX object src/highgui/CMakeFiles/highgui.dir/utils.o
[ 84%] Building CXX object src/highgui/CMakeFiles/highgui.dir/window.o
[ 85%] Building CXX object src/highgui/CMakeFiles/highgui.dir/cvcap_ffmpeg.o
/home/myself/opencv/latest_tested_snapshot/opencv/src/highgui/cvcap_ffmpeg.cpp: In member function ‘virtual IplImage* CvCapture_FFMPEG::retrieveFrame(int)’:
/home/myself/opencv/latest_tested_snapshot/opencv/src/highgui/cvcap_ffmpeg.cpp:550: error: ‘img_convert’ was not declared in this scope
/home/myself/opencv/latest_tested_snapshot/opencv/src/highgui/cvcap_ffmpeg.cpp: In member function ‘virtual bool CvVideoWriter_FFMPEG::writeFrame(const IplImage*)’:
/home/myself/opencv/latest_tested_snapshot/opencv/src/highgui/cvcap_ffmpeg.cpp:1045: error: ‘img_convert’ was not declared in this scope
/home/myself/opencv/latest_tested_snapshot/opencv/src/highgui/cvcap_ffmpeg.cpp: In member function ‘virtual bool CvVideoWriter_FFMPEG::open(const char*, int, double, CvSize, bool)’:
/home/myself/opencv/latest_tested_snapshot/opencv/src/highgui/cvcap_ffmpeg.cpp:1181: warning: ‘AVFormatContext* av_alloc_format_context()’ is deprecated (declared at /usr/include/libavformat/avformat.h:873)
/home/myself/opencv/latest_tested_snapshot/opencv/src/highgui/cvcap_ffmpeg.cpp:1181: warning: ‘AVFormatContext* av_alloc_format_context()’ is deprecated (declared at /usr/include/libavformat/avformat.h:873)
make[2]: *** [src/highgui/CMakeFiles/highgui.dir/cvcap_ffmpeg.o] Error 1
make[1]: *** [src/highgui/CMakeFiles/highgui.dir/all] Error 2
make: *** [all] Error 2
[02:35:29] myself ~/opencv/latest_tested_snapshot/opencv/release $  


Any ideas??

---

### Post by skullmunky on 2009-08-01
You can also try using the prebuild OpenCV package that's in the repositories - you may not need to build it from source.  I've always built from source in the past, actually, but I just tried this way and it was pretty smooth.  Note, I didn't try the camera samples yet, so I can't confirm what camera support the package is built with.  Well, here's what I did:

1. installed the ffmpeg development packages:
```

libavcodec52-dev
libavformat52-dev
libavfilter-dev
libavdevice-dev
libavcodec-dev
libavc1394-dev

```

2. installed opencv:
```

libcv1
libcvaux1
libhighgui1
python-opencv
opencv-doc

libcv-dev
libcvaux-dev
libhighgui-dev

```

3. to test, copied the sample programs to my home directory

```

cp -r /usr/share/doc/opencv-doc/examples .
cd examples
cd c
sh build_all.sh

```

 
test the non-camera ones first, like convexhull, delaunay, watershed, etc.  then try camshiftdemo, blobtrack, and facedetect.

for facedetect you need to specify the location of the cascade file.  when you build the entire opencv package from source those are in a data folder which it can find relative to the examples folder; but if you install the prebuilt packages they're somewhere else so you have to specify that, I think like this.

```

./facedetect --cascade /usr/share/opencv/haarcascades/haarcascade_frontalface_alt2.xml

```

If you can't get any camera access it may be because the Ubuntu package is built for 1394 cameras and you're using a usb webcam, or vice versa.  I've had the best luck building OpenCV with the option to use GStreamer for capturing.

Anyway, try this method out first.  If it doesn't work we'll go back to the build-from-source method, it shouldn't be too hard to fix either.

---

### Post by peterkirn on 2009-08-09
I believe I've found the source of this problem. There's a bug involving the different versions of ffmpeg required for other tools...

Discussion here:
[https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/312898](https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/312898)

You're going to have the same problem whether you build with either source or the package, because it impacts the dependencies mentioned here (e.g., libavcodec-dev)

There is a fix coming in Karmic:
[https://launchpad.net/ubuntu/karmic/+source/ffmpeg-debian/4:0.5+svn20090609-1ubuntu2](https://launchpad.net/ubuntu/karmic/+source/ffmpeg-debian/4:0.5+svn20090609-1ubuntu2)

So here's a dumb question: short of upgrading to Karmic alpha, how might I apply that fix to my Jaunty system?

Alternatively, yes, the really fun solution is to uninstall Blender, etc., before attempting this. (Whee...)

---

### Post by skullmunky on 2009-08-10
ah, you're right.  ugh.  ok, so you can't compile programs using the ffmpeg -dev packages if you have the -unstripped libraries installed, because e.g. libavcodec-dev depends on libavcodec52 which forces removal of libavcodec52-unstripped.

So I guess the only solution for now is in fact to build ffmpeg from source, and then build opencv from source, like you were doing.  ugh.  I'm gonna try that out too, we'll see how it goes.

---

### Post by secure on 2009-08-11
> **my.self said:**
> But I checked out the latest "ffmpeg" version from svn...

cd
svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg
cd ffmpeg

./configure --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab --enable-shared

make
sudo checkinstall --fstrans=no --install=yes --pkgname=ffmpeg --pkgversion "3:0.svn`date +%Y%m%d`-12ubuntu3" --default

_______________________________________________________________________________________
_______________________________________________________________________________________

I don't really understand why "opencv" needs the header file???
If you need a functionality from another project in Microsoft .NET you just add a reference to this .dll and everything is done!

In some cases also you have to register you .dll for COM or add it to the Global Assembly Cache but thats all...

How is this done in linux?
Do I have to register these assemblies?
Is there something similar????

??
??
??

Omg...
I have absolutely no plan ;-(

i'm new for ubuntu too
so i don't understand just do like [http://opencv.willowgarage.com/wiki/InstallGuide_Linux](http://opencv.willowgarage.com/wiki/InstallGuide_Linux)
but i have the same problem with you
> 
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:804: error: expected initializer before ‘*’ token
/home/myself/opencv/trunk/opencv/src/highgui/cvcap_ffmpeg.cpp:758: warning: ‘const char* icvFFMPEGErrStr(int)’ defined but not used
make[2]: *** [src/highgui/CMakeFiles/highgui.dir/cvcap_ffmpeg.o] Error 1
make[1]: *** [src/highgui/CMakeFiles/highgui.dir/all] Error 2
make: *** [all] Error 2


first i install ffmpeg with apt-get so later i load it from svn
and
./configure
make 
sudo make install

and then it 100%
sorry for my bad english

---

### Post by bear24rw on 2009-08-11
i had alot of trouble with ffmpeg trying to compile from source, ive been using opencv out of the repositories from months with no problem though. i would highly suggest you just stick with the repositories unless you really need some feature compiled in

---

### Post by unutbu on 2009-08-11
Edit: Oops... I see this was mentioned in post #1. :oops:

[s]Have you tried this guide to compile ffmpeg from source?[/s]

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by my.self on 2009-08-12
Yes, 
i tried this in combination with:
[http://opencv.willowgarage.com/wiki/InstallGuide_Linux](http://opencv.willowgarage.com/wiki/InstallGuide_Linux)

So, my question now...
Is it possible to install opencv on ubuntu 9.04??
Has anyone successful installed it on Jaunty?

---

### Post by secure on 2009-08-12
> **my.self said:**
> Yes, 
i tried this in combination with:
[http://opencv.willowgarage.com/wiki/InstallGuide_Linux](http://opencv.willowgarage.com/wiki/InstallGuide_Linux)

So, my question now...
Is it possible to install opencv on ubuntu 9.04??
Has anyone successful installed it on Jaunty?

me
just try this [http://opencv.willowgarage.com/wiki/InstallGuide_Linux](http://opencv.willowgarage.com/wiki/InstallGuide_Linux)

---

### Post by my.self on 2009-08-13
Look what link is posted above...

---

### Post by raccoonone on 2009-08-14
> **peterkirn said:**
> I believe I've found the source of this problem. There's a bug involving the different versions of ffmpeg required for other tools...

Discussion here:
[https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/312898](https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/312898)

You're going to have the same problem whether you build with either source or the package, because it impacts the dependencies mentioned here (e.g., libavcodec-dev)

There is a fix coming in Karmic:
[https://launchpad.net/ubuntu/karmic/+source/ffmpeg-debian/4:0.5+svn20090609-1ubuntu2](https://launchpad.net/ubuntu/karmic/+source/ffmpeg-debian/4:0.5+svn20090609-1ubuntu2)

So here's a dumb question: short of upgrading to Karmic alpha, how might I apply that fix to my Jaunty system?

Alternatively, yes, the really fun solution is to uninstall Blender, etc., before attempting this. (Whee...)

Does anyone know if the fix in Karmic actually worked? From the last couple comments in that bug report it looks like it was fixing a related, but different issue.

---

