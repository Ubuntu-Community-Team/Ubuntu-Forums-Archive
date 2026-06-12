---
title: "error while downloading a .webm file from rtsp server using GStreamer"
date: 2013-08-08
forum: Programming Talk
---

### Post by Rahul04789 on 2013-08-08
Hi friends,

I am using Live555MediaServer for rtsp  server.

After running this server, and using the following code for downloading file from server I got error.
I want to download a .webm file from server and download it.

Code at client side:

**gst-launch-0.10 -v rtspsrc location=rtsp://192.168.1.2:8554/ABC.webm ! matroskademux name=t t.video_00 ! matroskamux ! filesink location=qqq.webm **

**Error** at client side:

rahul@rahul-VPCEG28FN:~$ gst-launch-0.10 -v rtspsrc location=rtsp://192.168.1.2:8554/ABC.webm ! matroskademux name=t t.video_00 ! matroskamux ! filesink location=qqq.webm 
Setting pipeline to PAUSED ...
Pipeline is live and does not need PREROLL ...
Setting pipeline to PLAYING ...
New clock: GstSystemClock
ERROR: from element /GstPipeline:pipeline0/GstRTSPSrc:rtspsrc0: Could not read from resource.
Additional debug info:
gstrtspsrc.c(4589): gst_rtspsrc_try_send (): /GstPipeline:pipeline0/GstRTSPSrc:rtspsrc0:
Could not receive message. (System error: Connection refused)
Execution ended after 94409568 ns.
Setting pipeline to PAUSED ...
Setting pipeline to READY ...
Setting pipeline to NULL ...
Freeing pipeline ...


Error at Server side:

StreamParser internal error (14 + 149988 > 150000)
Aborted (core dumped)




Please tell me how to get rid of this error.


Regards,
Rahul

---

### Post by Rahul04789 on 2013-08-08
Please tell someone. Its urgent.

---

### Post by Vaphell on 2013-08-09
[http://comments.gmane.org/gmane.comp.multimedia.live555.devel/7467](http://comments.gmane.org/gmane.comp.multimedia.live555.devel/7467)

> The problem here is the extremely large H.264 frame (about 280,000 bytes in size) that you have in this video.  This was too big for our stream parsing code to handle.

You can fix this by changing the constant BANK_SIZE in "liveMedia/StreamParser.cpp" from 150000 to 300000.  (I'll also make this change in the next release of the software.)

---

### Post by Rahul04789 on 2013-08-12
@Vaphell:
Hi 
I have made the corresponding changes and again installed live 
but still i get the following error 



rahul@rahul-VPCEG28FN:~$  gst-launch-0.10 -v rtspsrc location="rtsp://192.168.1.2:8554/ABC.webm" !  matroskademux name=t t.video_00 ! matroskamux ! filesink  location=qq.webm | grep ^[^L]
Setting pipeline to PAUSED ...
Pipeline is live and does not need PREROLL ...
Setting pipeline to PLAYING ...
New clock: GstSystemClock
ERROR: from element /GstPipeline:pipeline0/GstRTSPSrc:rtspsrc0: Resource not found.
Additional debug info:
gstrtspsrc.c(4699): gst_rtspsrc_send (): /GstPipeline:pipeline0/GstRTSPSrc:rtspsrc0:
File Not Found, Or In Incorrect Format
Execution ended after 349604 ns.
Setting pipeline to PAUSED ...
Setting pipeline to READY ...
Setting pipeline to NULL ...
Freeing pipeline ...




But I have placed the file at correct location.

Please tell how to solve it

---

