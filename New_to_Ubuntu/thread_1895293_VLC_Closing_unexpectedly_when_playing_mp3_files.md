---
title: "VLC Closing unexpectedly when playing mp3 files"
date: 2011-12-14
forum: New to Ubuntu
---

### Post by rrsk on 2011-12-14
Am using ubuntu 11.04....VLC version: 1.1.9-1ubuntu1.3
VLC Closing unexpectedly when playing mp3 files
any solution?

Note: VLC works properly for Video files

---

### Post by gordintoronto on 2011-12-14
Open a terminal window, enter the command: vlc

Select an MP3 file, see if an error message appears.

Did you install the "restricted extras"?

---

### Post by rrsk on 2011-12-15
i didnot install any restricted extras

i didnot understand these logs......so i played both mp3 and flv files
error logs for mp3 and vedio files are

> 
(for mp3)-------------------------------------------------------------------------------------
[0xc7f7c0] signals interface error: signal 17 overriden (0x7f01a55db450)
[0xc7f7c0] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]
[0x7f01a000db50] access_http access error: error: HTTP/1.0 407 Proxy Authentication Required
[0x7f01a000db50] access_http access error: error: HTTP/1.0 407 Proxy Authentication Required
[0x7f5ef8017220] access_mms access error: cannot connect to images.google.com:80
[0x7f5ef8003d70] main art finder error: no suitable access module for `[http://images.google.com/images?q=Why%20This%20Kolaveri%27di%203%20cover](http://images.google.com/images?q=Why%20This%20Kolaveri%27di%203%20cover)'
Blocked: call to setenv("_PX_CONFIG_ORDER", "", 1)
[0xaab7c0] signals interface error: signal 17 overriden (0x7f5f1bc4f450)
[0xaab7c0] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]
[0x113b650] access_http access error: error: HTTP/1.0 407 Proxy Authentication Required
[0x113b650] access_http access error: error: HTTP/1.0 407 Proxy Authentication Required
[0x113b650] access_mms access error: cannot connect to [www.last.fm:80](www.last.fm:80)
[0x7f5ef8003d70] main art finder error: no suitable access module for `[http://www.last.fm/music/Why](http://www.last.fm/music/Why) This Kolaveri'di/3'
Blocked: call to setenv("_PX_CONFIG_ORDER", "", 1)
[0xaab7c0] signals interface error: signal 17 overriden (0x7f5f1bc4f450)
[0xaab7c0] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]
Segmentation fault

(for flv)-------------------------------------------------------------------------------------
[flv @ 0x7f0184c23950]Estimating duration from bitrate, this may be inaccurate
[flv @ 0x7f01a001b180]Estimating duration from bitrate, this may be inaccurate
[0xc7f7c0] signals interface error: signal 17 overriden (0x7f01a55db450)
[0xc7f7c0] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]
[0x7f01a000db50] access_mms access error: cannot connect to images.google.com:80
[0x12dc530] main art finder error: no suitable access module for `[http://images.google.com/images?q=Why%20This%20Kolaveri%27di%203%20cover](http://images.google.com/images?q=Why%20This%20Kolaveri%27di%203%20cover)'
Blocked: call to setenv("_PX_CONFIG_ORDER", "", 1)
[0xc7f7c0] signals interface error: signal 17 overriden (0x7f01a55db450)
[0xc7f7c0] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]
[0x15c58c0] access_http access error: error: HTTP/1.0 407 Proxy Authentication Required
[0x15c58c0] access_http access error: error: HTTP/1.0 407 Proxy Authentication Required
[0x15c58c0] access_mms access error: cannot connect to [www.last.fm:80](www.last.fm:80)
[0x12dc530] main art finder error: no suitable access module for `[http://www.last.fm/music/Why](http://www.last.fm/music/Why) This Kolaveri'di/3'
Blocked: call to setenv("_PX_CONFIG_ORDER", "", 1)
[0xc7f7c0] signals interface error: signal 17 overriden (0x7f01a55db450)
[0xc7f7c0] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]
Segmentation fault

---

### Post by gordintoronto on 2011-12-15
Please install the Ubuntu restricted extras.

---

### Post by rrsk on 2011-12-16
i installed still problem remains

i note one thing when VLC closes "Blocked: call to setenv("_PX_CONFIG_ORDER", "", 1)" is the error
am a beginner of ubuntu....so pls guide me to understand the error


> [0x1dc17c0] signals interface error: signal 17 overriden (0x7fdc4a37a450)
[0x1dc17c0] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]
[0x243e4f0] access_http access error: error: HTTP/1.0 407 Proxy Authentication Required
[0x243e4f0] access_http access error: error: HTTP/1.0 407 Proxy Authentication Required
[0x243e4f0] access_mms access error: cannot connect to [www.last.fm:80](www.last.fm:80)
[0x2409820] main art finder error: no suitable access module for `[http://www.last.fm/music/Why](http://www.last.fm/music/Why) This Kolaveri'di/3'
Blocked: call to setenv("_PX_CONFIG_ORDER", "", 1)
[0x1dc17c0] signals interface error: signal 17 overriden (0x7fdc4a37a450)
[0x1dc17c0] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]
Segmentation fault

---

